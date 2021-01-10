<template>
  <h1 class="header">Todo List</h1>
  <form @submit.prevent="addTasks">
    <label>Enter Daily Task</label>
    <input type="text" required v-model="task" />
    <button type="submit">Add Task</button>
    <div>
      <p class="todotitle">My Todo</p>
      <p
        class="task"
        v-for="singleTask in tasks"
        :key="singleTask"
        v-on:click="deleteTask(singleTask)"
      >
        {{ singleTask }}
      </p>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      task: "",
      tasks: [],
    };
  },
  methods: {
    addTasks() {
      if (this.task !== "") {
        if (!this.tasks.includes(this.task)) {
          this.tasks.push(this.task);
        }
        this.task = "";
      }
    },
    deleteTask(task) {
      this.tasks = this.tasks.filter((item) => {
        return task !== item;
      });
    },
  },
};
</script>

<style>
.header {
  color: #41b883;
}
form {
  max-width: 420px;
  margin: 30px auto;
  background: #34495e;
  padding: 30px;
  border-radius: 20px;
}
input {
  display: block;
  background: #34495e;
  border: none;
  border-bottom: 2px solid #42b883;
  width: 100%;
  box-sizing: border-box;
  padding: 10px;
  color: #41b883;
  font-size: 15px;
}
label {
  color: white;
  display: block;
  margin-bottom: 10px;
  letter-spacing: 2px;
}
button {
  border: none;
  border: 1px solid #41b883;
  padding: 5px 10px;
  color: white;
  letter-spacing: 1px;
  margin: 15px 10px 10px 10px;
  background-color: #41b883;
  font-size: 15px;
}
.todotitle {
  color: aliceblue;
  font-size: 20px;
  letter-spacing: 2px;
}
.task{
    color: aliceblue;
    text-transform: capitalize;
    padding: 5px;
    border-bottom: 1px solid white;
    width: 100%;
}
.task:hover{
    color:red;
    border: red 1px solid;
}

</style>