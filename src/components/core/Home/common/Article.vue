<template>
  <article class="article" :style="`min-height: ${minHeight}px`">
    <div class="article__head">
      <Logo :black="true" />
    </div>
    <div class="article__content"></div>
  </article>
</template>
<script>
import Logo from "@/components/shared/MagazineLogo";
export default {
  props: {
    item: Object
  },
  components: {
    Logo
  },
  data() {
    return {
      minHeight: 0
    };
  },
  mounted() {
    this.calculate();
    if (window) {
      window.addEventListener("resize", this.calculate);
    }
  },
  destroyed() {
    if (window) {
      window.removeEventListener("resize", this.calculate);
    }
  },
  methods: {
    calculate() {
      this.minHeight = this.$el.clientWidth / 1.7;
    }
  }
};
</script>
<style lang="scss" scoped>
.article {
  width: 100%;
  background-color: var(--second-color);
  color: var(--primary-color);
  position: relative;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 5%;

  &__container {
  }
}
</style>
