<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" class="logo" />
    <h1>Todo List</h1>
    <input
      class="input"
      v-model="newToDo"
      placeholder="What needs to be done"
    />
    <button class="add-button" v-on:click="add">Add</button>
    <div class="list">
      <ul style="list-style-type: none;">
        <li v-for="(todo, i) in existingToDo" v-bind:key="todo.id">
          <span> {{ i + 1 }}:{{ todo.text }} </span>
          <button class="delete-button" v-on:click="deleteToDo(i)">X</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      newToDo: "",
      existingToDo: [
        { text: "Learn JS design patterns", id: 0 },
        { text: "Learn Vue.js lifecycle", id: 1 },
        { text: "Make a simple Vue.js TodoList app", id: 2 },
      ],
    };
  },

  methods: {
    add() {
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf(),
      }),
        (this.newToDo = "");
    },

    deleteToDo(i) {
      this.existingToDo.splice(i, 1);
    },
  },
};
</script>

<style>
.app {
  text-align: lcenter;
  margin: 0;
  padding: 0;
}
.logo {
  height: 75px;
  margin: auto;
  text-align: center;
}
</style>
