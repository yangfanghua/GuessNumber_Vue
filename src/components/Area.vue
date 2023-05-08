<script>
export default {
  components: {},
  //資料變數宣告
  data() {
    return {
        min:1,
        max:100,
        guess:null,
        answer:Math.floor(Math.random()*100+1),
        isans:false,
    };
  },
  //方法
  methods: {

    fn() {
        if (this.guess < this.min || this.guess > this.max) {
          alert("看清楚~~!不要亂輸入拉");
          this.guess=null;
          return;
        }
        if (this.guess < this.answer) {
          this.min = this.guess;
          this.guess=null;
        }
        if (this.guess > this.answer) {
            this.max = this.guess;
            this.guess=null;
        }
        if (this.guess == this.answer) {
          alert("答對拉~!");
          this.isans=true;
        }
      },

  },
  //生命週期
  mounted() {},
};
</script>

<template>
  <div class="cantainer bg-ligh">
    <p class="h1" >猜猜看</p>
    
    <div v-if="isans">
        <p>答對了</p>
    </div>

    <div class="number" v-else>
    <p>{{ min }}</p>
    <p>-</p>
    <p>{{ max }}</p>
    </div>
    <input type="number" v-model="guess">
    <button class="btn-secondary" type="button" @click="fn">回答</button>
  </div>
</template>

<style scoped>

.cantainer{
text-align: center;

}
.number{
    display: flex;
    justify-content: center;
    font-size: 180px;
}

</style>
