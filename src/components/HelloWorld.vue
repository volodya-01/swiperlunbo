<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
   <div class="contan">
      <swiper :options="swiperOption" >
    <swiper-slide  v-for="(slide, index) in swiperSlides" :key="index">
      <div class="box">I'm Slide {{ slide }}</div>
      <img src="" alt="">
    </swiper-slide>
<!--    <div class="swiper-pagination" slot="pagination"></div> -->
        <div class="swiper-button-prev" slot="button-prev"></div>
<div class="swiper-button-next" slot="button-next"></div>
  </swiper>
   </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      swiperOption: {
         slidesPerView: 6,
          spaceBetween:30,
          slidesPerGroup: 6,
          loop: true,
          loopFillGroupWithBlank: true,
          pagination: {
            el: '.swiper-pagination',
            /* clickable: true */
          },
           navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev'
          }
        },
        swiperSlides: [1, 2, 3, 4, 5,6],
       
    }
  },
created(){
this.$axios
        .post(
          "http://192.168.1.17:8000/api/v1/test"
          )
        .then(res => {
            console.log(res);
  
        })
        .catch(error => {
          console.log(error);
        });
    
},
    mounted() {
      setInterval(() => {
        console.log('simulate async data')
        if (this.swiperSlides.length < 60) {
          this.swiperSlides.push(this.swiperSlides.length + 1)
        }
      },50)
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
.contan{
  display: -webkit-flex;
  display: flex;
  display: flex-box;
  justify-content: center;
  align-items: center;
  align-self: center;
  
   margin-left: 0px;
}
.box {
  
  width: 294px;
  height: 200px;
  background-color: aqua;
}

</style>
