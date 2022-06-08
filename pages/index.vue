<template>
  <div id="app">
    <div ref="carousel" class="main-carousel">
      <div class="carousel-cell"></div>
      <div class="carousel-cell"></div>
      <div class="carousel-cell"></div>
      <div class="carousel-cell"></div>
      <div class="carousel-cell"></div>
    </div>
  </div>
</template>

<script>
import Flickity from "flickity";
export default {
  data() {
    return {
      flickityOptions: {
        dragThreshold: 50,
        initialIndex: 1,
        prevNextButtons: false,
        pageDots: false,
        wrapAround: false,
        hash: true,
        percentPosition: false
      },
      stageDragging: false
    };
  },
  mounted() {
    this.$nextTick(() => {
      const flkty = new Flickity(this.$refs.carousel, this.flickityOptions);
      flkty.on("dragStart", function () {
        this.stageDragging = true;
        console.log("stageDragging: " + this.stageDragging);
      });
      flkty.on("dragEnd", function () {
        this.stageDragging = false;
        console.log("stageDragging: " + this.stageDragging);
      });
    });
  }
};
</script>

<style scoped>
.carousel {
  background: #fafafa;
}

.carousel-cell {
  width: 66%;
  height: 200px;
  margin-right: 10px;
  background: #8c8;
  border-radius: 5px;
  counter-increment: carousel-cell;
}

/* cell number */
.carousel-cell:before {
  display: block;
  text-align: center;
  content: counter(carousel-cell);
  line-height: 200px;
  font-size: 80px;
  color: white;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
