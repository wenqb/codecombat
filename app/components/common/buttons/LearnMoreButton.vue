<template>
  <button class="text-button-link">
    <component
      :is="link ? 'a' : 'span'"
      class="text-button-link__link"
      :href="link"
      :target="target"
    >
      <slot />
      <CarouselArrow
        v-if="hasArrow"
        class="text-button-link__vector"
      />
    </component>
  </button>
</template>

<script>
import CarouselArrow from 'app/components/common/elements/CarouselArrow.vue'
import autoTracked from 'app/components/mixins/auto-tracked.js'

export default {
  name: 'LearnMoreButton',
  components: { CarouselArrow },
  mixins: [autoTracked],
  props: {
    link: {
      type: String,
      required: true,
      default: ''
    },
    target: {
      type: String,
      required: false,
      default: '_blank'
    },
    hasArrow: {
      type: Boolean,
      required: false,
      default: true
    }
  }
}
</script>

<style scoped lang="scss">
@import "app/styles/component_variables.scss";
.text-button-link {
    all: unset;
    align-items: center;
    box-sizing: border-box;
    display: inline-flex;
    gap: 8px;
    padding: 6px 0px;
    position: relative;

    &__link {
        color: var(--color-primary);
        letter-spacing: 0;
        width: fit-content;
        &:hover {
          text-decoration: underline;
        }
    }

    &__vector {
        height: 100%;
        aspect-ratio: 15.25 / 12.75;
        ::v-deep path {
          stroke: var(--color-primary);
        }
    }
}
</style>
