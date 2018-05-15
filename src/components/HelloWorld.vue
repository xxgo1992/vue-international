<template>
  <div class="hello">
    <div class="container">
      <h1 :style='{color}'>{{$t('common.home')}}</h1>
      <ul class="theme">
        <li v-for='(theme, index) in $i18n.messages.en.skin' :key=index>
          <span :style='{background:theme}' class='cube' @click='changeTheme(theme)'></span>
        </li>
      </ul>
      <!-- <span>{{$t('navbar.languageSwitch')}}</span> -->
      <el-switch
        style="display: block"
        v-model="iszh"
        active-color="#13ce66"
        inactive-color="#ff4949"
        :active-text="$t('navbar.zh')"
        :inactive-text="$t('navbar.en')"
        @change='changeLanguage'>
      </el-switch>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      color: '#000'
    }
  },
  computed: {
    iszh: {
      get() {
        console.log('t', this.$i18n)
        return (this.$i18n.locale === 'zh')
      },
      set(v) {
      }
    }
  },
  methods: {
    changeTheme(theme){
      this.color = theme
    },
    changeLanguage (lang) {
      console.log('lang', lang)
      this.$i18n.locale = lang?'zh' : 'en'

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.hello{
  /* width: 300px; */
  height: 100%;
  margin: 0 auto;
  background: url(../img/bg.jpg) top center;
  min-width: 1000px;
  /* background-size: 100% 100% */
}
.container{
  margin: 0 auto;
  width: 1000px;
  height: 100%;
  background: #fff
}
.cube{
  width: 20px;
  height: 20px;
  display: block;
  cursor: pointer;
}
</style>
