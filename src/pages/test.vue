<template lang="pug">
.container
  .raw(v-if="raw") {{article}}
  wxParse(v-else, :content="article", ref="wxParse")
  .turn-btn(@click="raw = !raw") 切换
</template>

<script>
import wxParse from 'mpvue-wxparse'

export default {
  components: {
    wxParse
  },
  data () {
    return {
      raw: false,
      article: `
<!DOCTYPE html>
<html>
  <head>
    <title>Test</title>
    <link rel="stylesheet" href="" />
    <style>
      body {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1 class="test1">H1</h1>
    <h2 class="test1 test2">H2</h2>
    <h3 style="color: red">H3</h3>
    <h4 style="color: blue;border: 1px solid #000">H4</h4>
    <h5>H5</h5>
    <h6>H6</h6>
    <strong><a>点击购买</a></strong>
  </body>
</html>
      `
    }
  },
  mounted () {
    console.log(this.$refs.wxParse.wxParseData)
  }
}
</script>
