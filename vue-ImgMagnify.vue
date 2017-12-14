<template>
  <div class="img-magnify">
    <img v-lazy="src" class="img" @click="isMagnify=true">
    <transition enter-active-class="fadeIn" leave-active-class="fadeOut">
      <div v-if="isMagnify&&src" class="magnify" @click="isMagnify=false">
        <div class="magnify-back"></div>
        <img class="magnify-img" :src="src">
      </div>
    </transition>
  </div>
</template>
<script>
export default {
  name: 'img-magnify',
  props: {
    src: {
      default: '',
    },
  },
  data() {
    return {
      isMagnify: false,
    }
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
.img-magnify {
  display: inline-block;
  .magnify {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 9999;
  }
  .img {
    width: 100%;
    height: 100%;
    display: block;
  }
  .magnify-back {
    background-color: #000;
    width: 100%;
    height: 100%;
    opacity: 0.8;
  }
  .magnify-img {
    margin: auto;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    max-height: 100%;
    max-width: 100%;
  }
}

.fadeIn {
  animation: fadeIn .5s;
}

.fadeOut {
  animation: fadeIn  .5s reverse;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
