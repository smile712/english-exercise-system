<!--  -->
<template>
  <div class="catalogExamSection">
    <a class="link-primary" :href="examURL">
      <div class="card">
        <picture>
          <source :src="picURL" type="image/webp">
          <source :src="picURL" type="image/jpg">
            <img class="card-img-top"
            :src="picURL"
            style="width:280px; height:395px;" :alt="examName">
        </picture>
        <div class="card-body">
          <div class="title_num">{{ examName }}</div><progress max="100" value="42">

          </progress>
        </div>
      </div>
    </a>

  </div>
</template>

<script>
import * as emitter from '@/utils/emitter/eventEmitter'
export default {
  data () {
    return {
      examName: '2022年考研英语二',
      examURL: '/kaoyan/2022/02',
      basURL: '../../../assets/',
      picURL: require('../../../assets/kaoyan/picData/2022二.jpg')
    }
  },
  methods: {
    changePicURL (belong, name) {
      console.log(name)
      console.log(belong)
      let pic = ''
      pic = (this.basURL + belong + '/picData/' + name + '.jpg').toString()
      console.log(pic)
      this.picURL = require('../../../assets/kaoyan/picData/2023一.jpg')
      this.picURL = require(pic)
      console.log(this.picURL)
    }
  },
  // 生命周期 - 创建完成（访问当前this实例）
  created () {

  },
  // 生命周期 - 挂载完成（访问DOM元素）
  mounted () {
    emitter.on('picChange', event => {
      this.changePicURL(event.detail.belong, event.detail.name)
    })
  }

}
</script>
<style lang="scss" scoped>@import "./CatalogExamSection.scss";</style>
