<!-- /components/Home.vue -->
<template>
  
  <!-- Container (TOUR Section) -->
<div id="up" class="bg-1">
  <div class="container">
    <h3 class="text-center">ทดสอบ</h3>
    <p class="text-center">ทดสอบการเชื่อม API เเละแสดงผล.<br> โดยใช้ API จาก <strong>"https://jsonplaceholder.typicode.com/albums/1/photos"</strong></p>
    
    
    <div class="row text-center">
      <div class="col-sm-4"  v-for="item in test"> 
        <div class="thumbnail">
          <img :src="item.url" :alt="item.url">
          <p><strong>ชื่อ :</strong>{{ item.title }}</p>
          <button class="btn" data-toggle="modal" >{{ item.id }}</button>
        </div>
      </div>
    </div>
  </div>
  
</div>

</template>

<script>
const API_URL = 'https://jsonplaceholder.typicode.com/albums/1/photos'
export default {
  name: 'Home',
  data: function () {
    return {
      test: [] 
    }
  },
  methods: {
    loadDate: function () {
      this.$http.get(API_URL) //เรียกใช้ ้kttp ที่ API_URL
        .then(response => {
          // console.log(response)
          this.test = response.body //เก็บไว้ในตัวแปร teest
        }, () => {
          this.test = []
        })
    }
  },
  created: function () {
    this.loadDate()
  }
}
</script>