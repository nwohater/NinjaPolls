<script>
  import Header from './components/Header.svelte';
  import Footer from './components/Footer.svelte';
  import Tabs from './shared/Tabs.svelte';
  import CreatePollForm from './components/CreatePollForm.svelte';
  import PollList from './components/PollList.svelte';

  //tabs
  let items = ['Current Polls', 'Add New Poll'];
  let activeItem = 'Current Polls';

  const tabChange = (e) => {
    activeItem = e.detail;
  };

  // let polls = [
  //   {
  //     id: 1,
  //     question: 'Python or JavaScript',
  //     answerA: 'Python',
  //     answerB: 'JavaScript',
  //     votesA: 9,
  //     votesB: 15,
  //   },
  // ];

  const handleAdd = (e) => {
    activeItem = 'Current Polls';
  };
</script>

<Header />
<main>
  <Tabs {activeItem} {items} on:tabChange={tabChange} />
  {#if activeItem === 'Current Polls'}
    <!-- <PollList {polls} on:vote={handleVote} /> -->
    <PollList />
  {:else}
    <CreatePollForm on:add={handleAdd} />
  {/if}
</main>
<Footer />

<style>
  main {
    max-width: 960px;
    margin: 40px auto;
  }
</style>
