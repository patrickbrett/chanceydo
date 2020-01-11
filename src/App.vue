<template>
  <div id="container">
  <input v-model="newName" placeholder="Name..." />
  <input v-model="newPlace" placeholder="Place..." />

  <select v-model="currentColour">
    <option v-for="colour in colours">{{colour}}</option>
  </select>

  <button @click="addPerson">Add person</button>
  <button @click="removeAll">Remove all</button>
  <div class="person" v-for="(person, index) in people">
    <div :class="'label ' + person.colour"></div>
    <b>{{person.name}}</b> <i>{{person.place}}</i>
    <button @click="removePerson(index)">remove</button>
  </div>
  <div v-if="people.length === 0"> Add people here</div>
</div>
</template>

<script>
export default {
  name: "app",
  data: function () {
    return {
      newName: "",
      newPlace: "",
      people: [
        {
          name: "naomi",
          place: "india",
          colour: "green"
        },{
          name: "lidia",
          place: "italy",
          colour: "blue"
        }
      ],
      colours: [ "red", "green", "blue" ],
      currentColour: "red"
    }
  },
  methods: {
    addPerson() {
      let newPerson = {
        name: this.newName,
        place: this.newPlace,
        colour: this.currentColour
      }
      this.people.push(newPerson)
      this.newName = ""
      this.newPlace= ''
    },
    removePerson(index) {
      this.people.splice(index,1)
    },
    removeAll(){
      this.people=[]
    }
  }
};
</script>

<style>
  #container {
    border: 3px solid black;
    padding: 20px;
    margin: 20px;
    display: inline-block;
  }

  .person {
    margin: 10px;
  }

  .label {
    width: 20px;
    height: 20px;
    border-radius: 10px;
    display: inline-block;
  }

  .red {
    background: #c44031;
  }

  .blue {
    background: #1580d1;
  }

  .green {
    background: #14ba43;
  }
</style>
