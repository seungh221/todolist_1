<template>
  <div id="app">
    <div class="container">
      <div class="col-md-6 offest-md-3">
       <h1 class="text-center mb-4">Todo 어플리케이션</h1>
       <input type="text" class="form-control mb-4" v-model="userInput" @keyup.enter="addNewTodo">
      
       <div class="list-group mb-4">
          <button class="list-group-item text-left" v-for="todo in activeTodoList" v-bind:key='todo' @click="toggleTodoState(todo)">
           {{ todo.label }}
          </button>
       </div>

       <div class="text-right">
         <button type="button" class="btn btn-sm" @click="changeCurrentState('active')">할 일</button>
         <button type="button" class="btn btn-sm" @click="changeCurrentState('done')">완료 </button> 
         <button type="button" class="btn btn-sm" @click="changeCurrentState('all')">전체</button>        
       </div>  
      </div>    
    </div> 
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return{
      userInput: '',
      todoList: [],
      currentStates: 'active'
    };
  },
  computed: {
    activeToDoList() {
      return this.todolist.filter(todo => this.currentStates ==='all' && todo.state === this.currentStates);
  
    }
  },
  methods: { 
    changeCurrentState(state) {
      this.currentStates = state;
    },
    addNewTodo() {
      this.todoList.push({
        label: this.userInput,
        state: 'active'
      });
      this.userInput= '';

    },
    toggleTodoState(todo){
      todo.state = todo.state === 'active'? 'done' : 'active' ;
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
