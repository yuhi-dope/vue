<template>
  <div class="Home">
    <input type="text" v-model="papa" />
    <button @click="doAdd">住所自動入力</button>
    <h1 class="add">Address:{{ address }}</h1>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      papa:"",
      address:"",
    };
  },
  methods: {
    doAdd() {
      this.address=this.papa;
    }
  },
  async created() {
    let item = await axios.get(
      `https://apis.postcode-jp.com/api/v4/postcodes/${this.address}?apiKey=o61CLgzK0EIKezwVfGMnkzh1h8TtSxx9UULEs0q`
    );
    this.data = item.data;
    this.address = this.data.address;
  },
};
</script>