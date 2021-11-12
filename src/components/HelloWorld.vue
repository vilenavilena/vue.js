<template>
  <div class="hello">
    {{message}}-{{message.length}} symbols
    <br/>
    <input type="number" placeholder="operand1" v-model.number="operand1"/>
    <input type="number" placeholder="operand2" v-model.number="operand2"/>
   <br/>
   {{ result }}
   <br/>
    <button v-on:click="result= operand1 + operand2">+</button>
    <button @click="result=operand1-operand2">-</button>
    <button @click="mul">*</button>
    <button @click="div">/</button>
    <button @click="exp">^</button>
    <button @click="divInt">Целочисленное деление</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String,

  }, 
  data() {
    return {
      message: "Hello Vue",
      result: 0,
      operand1: 0,
      operand2: 0
    }
  },
  methods: {
    onChange(str, event){
      console.log(str, event);
    },
    mul() {
      this.result = this.operand1 * this.operand2
    },
    div() {
      const {operand1, operand2} = this
      this.result = operand1 / operand2
    },
    onChangeInput(event) {
      this.operand1 = event.target.value
      console.dir(event.target)
    },
    exp() {
      this.result = Math.pow(this.operand1, this.operand2)
    },
    divInt() {
      this.result = Math.floor(this.operand1 / this.operand2)
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
