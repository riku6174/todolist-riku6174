<script setup lang="ts">
import { ref } from 'vue'
interface Task {
  name: string
  progress: Boolean
}
const tasks = ref<Ttem[]>([
  { name: '散歩', progress: false },
  { name: '水やり', progress: false }
])
let newTaskName = ref('')
const addTask = () => {
    if (newTaskName.value === '') return
    tasks.value.push({ name: newTaskName.value, progress: false })
    newTaskName.value = ''
}
</script>

<template>
    <div>
        <div>未完了タスク</div>
        <ul>
            <!-- <li v-for="task in tasks" :key="task.name">
                <div v-if="task.progress===false">
                    <div>{{ task.name }}</div>
                    <button @click="task.progress=true">完了</button>
                </div>
                
            </li> -->

            <div v-for="task in tasks" :key="task.name">
                <li v-if="task.progress===false">{{ task.name }}</li>
                <button v-if="task.progress===false" @click="task.progress=true">完了</button>
            </div>
        </ul>
        <div>完了タスク</div>
        <ul>
            <!-- <li v-for="task in tasks" :key="task.name">
                <div v-if="task.progress===true">
                    <div>{{ task.name }}</div>
                    <button @click="task.progress=false">戻す</button>
                </div>
                
            </li> -->

            <div v-for="task in tasks" :key="task.name">
                <li v-if="task.progress===true">{{ task.name }}</li>
                <button v-if="task.progress===true" @click="task.progress=false">完了</button>
            </div>
        </ul>

        <div>
            <label>
                タスク名
                <input v-model="newTaskName" type="text" />
            </label>
            <button @click="addTask">追加</button>
        </div>
    </div>
  
</template>

<style>
.over500{
    color: red;
}
</style>