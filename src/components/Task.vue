<template>
    <div @dblclick="$emit('toggle-reminder',this.id)" :class="['task',task.reminder ? 'reminder':'']">
        <h3>
            {{task.text}}
            <i @click="onEdit(task.id)" class="fas fa-edit"></i>
            <i @click="onDelete(task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{task.day}}</p>
    </div>
    
</template>

<script>
    export default {
        name:'Task',
        props: {
            task:Object,
        },
        methods: {
            onDelete(id) {
                //console.log("delete button");
                this.$emit('delete-task',id)
            },
            onEdit(id) {
              this.$emit('edit-task',id)
            }
        }
    }
</script>

<style scope>
.fas {
  color: rgb(255, 0, 0);
}
.fa-edit{
  color:rgb(164, 233, 62);

}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>