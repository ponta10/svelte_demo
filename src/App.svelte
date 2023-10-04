<script lang="ts">
  export let name: string = "world";

  let newTask: string = "";
  let tasks: string[] = [];

  function addTask() {
    if (newTask.trim() !== "") {
      tasks = [...tasks, newTask.trim()];
      newTask = "";
    }
  }

  function removeTask(index: number) {
    tasks = tasks.filter((_, i) => i !== index);
  }
</script>

<main>
  <h1>Hello {name}!</h1>
  <input bind:value={newTask} placeholder="New task" />
  <button on:click={addTask}>Add task</button>

  <ul>
    {#each tasks as task, index}
      <li>
        <button on:click={() => removeTask(index)}>{task}</button>
      </li>
    {/each}
  </ul>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  ul {
    list-style-type: none;
    padding: 0;
  }

  li {
    margin: 0.5em 0;
    cursor: pointer;
  }

  li:hover {
    text-decoration: line-through;
  }
</style>
