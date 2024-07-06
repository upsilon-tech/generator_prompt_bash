<!-- eslint-disable max-len -->
<template>
  <header :class="{ dark: darkMode }">
    <div class="header-buttons">
      <IconButton icon="MoonIcon" title="Toggle dark mode" @click="toggleDarkMode"></IconButton>
    </div>
    <h1>$&nbsp;<span class="underscore">_</span>&nbsp;Bash Prompt Generator</h1>
  </header>
</template>
<!-- eslint-enable max-len -->

<script lang="ts">
import { defineComponent } from 'vue';
import darkMode from '@/lib/darkMode';
import IconButton from './ui/IconButton.vue';

/**
 * The site header containing the title.
 */
export default defineComponent({
  name: 'SiteHeader',
  components: {
    IconButton,
  },
  methods: {
    /**
     * Toggles the dark mode.
     */
    toggleDarkMode(): void {
      darkMode().toggle();
    },
  },
  computed: {
    /**
     * Returns `true` if the dark mode is enabled, `false` otherwise.
     */
    darkMode(): boolean {
      return darkMode().enabled;
    },
  },
});
</script>

<style lang="sass" scoped>
@import "@/assets/sass/_variables.sass"

header
  margin: 0
  color: $color-background
  background-color: #212121
  text-align: center

  h1
    font-size: 1.9em
    margin: 0
    padding: 0.5em

  .underscore
    color: #4caa25

.header-buttons
  position: absolute
  top: 1em
  left: 2em
  display: flex
  align-content: center
  gap: 1em

.github-corner
  svg
    position: absolute
    top: 0
    right: 0
    border: 0
    width: 140px
    height: 140px

  .corner
    color: $color-accent

  .octo-arm,
  .octo-body
    color: $color-background

  .octo-arm
    transform-origin: 130px 106px

.github-corner:hover
  .octo-arm
    animation: octocat-wave 560ms ease-in-out

.dark
  .github-corner
    .octo-arm,
    .octo-body
      color: $color-foreground

@keyframes octocat-wave
  0%,
  100%
    transform: rotate(0)

  20%,
  60%
    transform: rotate(-25deg)

  40%,
  80%
    transform: rotate(10deg)

@media screen and (max-width: $breakpoint-medium)
  .header-buttons
    left: 1em
    gap: 0.4em

  .github-corner
    svg
      width: 100px
      height: 100px

    .octo-arm,
    .octo-body
      color: $color-foreground

  .github-corner:hover
    .octo-arm
      animation: none

  .github-corner
    .octo-arm
      animation: octocat-wave 560ms ease-in-out

@media screen and (max-width: $breakpoint-small)
  header
    font-size: 0.8em

    h1
      // keep space for buttons and github corner and wrap text instead
      padding-left: 3em
      padding-right: 3em

  .header-buttons
    left: 0.5em
    gap: 0.2em

  .github-corner
    svg
      width: 80px
      height: 80px

@media screen and (max-width: $breakpoint-tiny)
  header
    font-size: 0.7em

    h1
      margin: 0 auto

  .github-corner
    svg
      width: 60px
      height: 60px


</style>
