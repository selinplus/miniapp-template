<template>
  <div class="container">
    <div class="head">
      <img class="logo" src="../../../static/imgs/logo.png"/>
      <swiper class="swiper" indicator-dots="true" autoplay="true" interval="5000" duration="1000">  
        <block v-for="(item, index) in items" :key="index">  
          <swiper-item>  
            <image :src="item.url" mode="aspectFill"/> 
          </swiper-item>  
        </block>  
      </swiper> 
    </div>
    <div class="content">
      <div class="left">
          <ul class="ad-list">
            <li class="ad-item" v-for="(ad,index) in ads" :key="index">{{ad.tit}}</li>
          </ul>
      </div>
      <div class="right">
          <ul class="ad-list">
            <li class="ad-item" v-for="(ad,index) in adsr" :key="index">{{ad.tit}}</li>
          </ul>
      </div>
    </div>
    <div class="intro">
      <ul class="intro-list">
        <li class="intro-item" v-for="(ad,index) in tipstoo" :key="index">
          <img :src="ad.src" :data-list="tipstoo" :data-src="ad.src" class="intro-img" @click="previewImg">
          <p class="intro-info">{{ad.info}}</p>
        </li>
      </ul>
    </div>
    <div class="swiper-tab">
      <div class="swiper-tab-item" :class="currentTab==0?'active':''" data-current="0" @click="clickTab">就业岗位</div>
      <div class="swiper-tab-item" :class="currentTab==1?'active':''" data-current="1" @click="clickTab">派遣公司</div>
      <div class="swiper-tab-item" :class="currentTab==2?'active':''" data-current="2" @click="clickTab">派遣海乘</div>
    </div>
    <swiper class="swiper-box" :current="currentTab" duration="300" @change="swiperTab">
      <swiper-item>
        <ul>
          <li class="toa">在海运、引航等单位从事驾驶辅助工作</li>
          <li class="toa">水手机工、三副三管轮</li>
          <li class="toa">二副二管轮、船舶管理员</li>
          <li class="toa">引航调度、轮机管理、机务管理等</li>
        </ul>
      </swiper-item>
      <swiper-item>
        <ul>
          <li class="toa">中远海运、青岛韦立</li>
          <li class="toa">青岛源丰润、招商轮船</li>
          <li class="toa">中外运、神华集团、南京油运</li>
        </ul>
      </swiper-item>
      <swiper-item>
        <ul>
          <li class="toa">皇家加勒比邮轮、公主邮轮</li>
          <li class="toa">歌诗达邮轮，星梦邮轮</li>
          <li class="toa">丽星邮轮等</li>
        </ul>
      </swiper-item>
    </swiper>
    <div class="desc">
      <p class="imp">公司100%安排就业，签订就业协议</p>
      <p class="addre" @click="navi">烟台市福山区崇文街69号302(点击导航)</p>
    </div>
    <div class="intro">
      <ul class="intro-list">
        <li class="intro-item" v-for="(ad,index) in tips" :key="index">
          <img :src="ad.src" :data-list="tips" :data-src="ad.src" class="intro-img" @click="previewImg">
          <p class="intro-info">{{ad.info}}</p>
        </li>
      </ul>
    </div>
    <div class="end-line">
      <p class="cm1" @click="callme1">梦想热线:18596148218[点击拨叫]</p>
      <p class="cm2"  @click="callme2">梦想热线:15615550258[点击拨叫]</p>
    </div>
    <div class="company">
      <p>山东大耳朵软件技术支持</p>
      <p @click="support">快速定制小程序:13287991199</p>
    </div>
  </div>
</template>

<script>

export default {
  data () {
    return {
      windowWidth: 0,
      windowHeight: 0,
      currentTab: 0,
      items: [
        {url: 'https://res.cloudinary.com/selinplus/image/upload/v1530749697/business/sail_training/1-0.jpg'},
        {url: 'https://res.cloudinary.com/selinplus/image/upload/v1530749697/business/sail_training/1.jpg'},
        {url: 'https://res.cloudinary.com/selinplus/image/upload/v1530749698/business/sail_training/3.jpg'},
        {url: 'https://res.cloudinary.com/selinplus/image/upload/v1530749699/business/sail_training/1-3.jpg'},
        {url: 'https://res.cloudinary.com/selinplus/image/upload/v1530749698/business/sail_training/1-2.jpg'},
        {url: 'https://res.cloudinary.com/selinplus/image/upload/v1530749698/business/sail_training/2.jpg'},
        {url: 'https://res.cloudinary.com/selinplus/image/upload/v1530749698/business/sail_training/1-1.jpg'}
      ],
      ads: [
        {tit: '招聘国企水手，机'},
        {tit: '年薪十万，交五'},
        {tit: '选择大于努力，正确的'},
        {tit: '从这里走出国门，走'},
        {tit: '大海的勇士，'}
      ],
      adsr: [
        {tit: '工，厨师，服务员'},
        {tit: '险，有退休'},
        {tit: '选择可以改变你的命运'},
        {tit: '向大海，走向世界！'},
        {tit: '带薪周游世界！'}
      ],
      tips: [
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/hc-1.jpg',
          info: '欢乐'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/hc-2.jpg',
          info: '沙滩'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/hc-3.jpg',
          info: '微笑'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/hc-4.jpg',
          info: '惬意'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/hc-5.jpg',
          info: '展望'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/hc-8.jpg',
          info: '绚烂'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/hc-6.jpg',
          info: '专业'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/hc-7.jpg',
          info: '开心'
        }
      ],
      tipstoo: [
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/sh-1.jpg',
          info: '螃蟹'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/sh-2.jpg',
          info: '烧烤'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/sh-3.jpg',
          info: '鲍鱼'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/sh-4.jpg',
          info: '对虾'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/sh-5.jpg',
          info: '健身'
        },
        {
          src: 'https://res.cloudinary.com/selinplus/image/upload/v1530762650/business/sail_training/sh-6.jpg',
          info: '荣耀'
        }
      ]
    }
  },
  methods: {
    previewImg (e) {
      const src = e.currentTarget.dataset.src
      const imgList = e.currentTarget.dataset.list
      let dealList = []
      imgList.forEach(element => {
        dealList.push(element.src)
      })
      wx.previewImage({
        current: src,
        urls: dealList
      })
    },
    clickTab (e) {
      if (this.currentTab === e.target.dataset.current) {
        return false
      } else {
        this.currentTab = e.target.dataset.current
      }
    },
    navi () {
      wx.openLocation({
        latitude: 37.50886,
        longitude: 121.26997,
        scale: 28
      })
    },
    callme1 () {
      wx.makePhoneCall({
        phoneNumber: '18596148218'
      })
    },
    callme2 () {
      wx.makePhoneCall({
        phoneNumber: '15615550258'
      })
    },
    support () {
      wx.makePhoneCall({
        phoneNumber: '13287991199'
      })
    }
  },
  swiperTab (e) {
    console.log(e.target.current)
    this.currentTab = e.detail.current
  },
  onShareAppMessage: function (res) {
    return {
      title: '宇逸船舶',
      path: '/pages/index/main'
    }
  }
}
</script>

<style scoped>
/*外部容器*/
.container{
  margin: 0;
  padding: 0;
}
/**头部**/
.head{
  margin: 0;
  padding:0;
  width: 100%;
}
.logo{
  height: 60rpx;
  width: 100%;
  padding: 0 0 5px 0;
  border-bottom-style: outset;
  border-color: coral;
  border-bottom-right-radius: 35rpx;
  border-bottom-left-radius: 35rpx;
}
/*轮播*/
.swiper{
  width:100%;
  height: 400rpx;
}
.swiper image {
  width: 100%;
}
/*中部内容*/
.content{
  display: grid;
  grid-template-columns: 50% auto;
  grid-column-gap: 0;
  width: 100%;
  padding:0;
}
/*半面文字*/
.left, .right{
  padding: 0;
  /* background-color:linear(30deg,cornflowerblue 0%,#fff 100%); */
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
  font-size: 0.8em;
}
.left{
  text-align: right;
  color:white;
  background:#35378f;/*linear-gradient(90deg,#fff 10%,#35378f 100%);*/
}
.right{
  color:#35378f;
  background:rgb(231, 192, 192);
}
.ad-list{
  padding: 0;
}
.ad-item{
  margin:0.5em 0;
  font-style:unset;
  line-height: 1.8em;
}
.intro-list{
  display: flex;
  justify-content:center;
  flex-wrap: wrap;
}
/* .intro-item{
  border:1px solid green;
} */
.intro-img{
  width: 48vw;
  filter:drop-shadow();
}
/*tab panel*/
.swiper-tab{
    width: 100%;
    border-bottom: 2rpx solid #ccc;
    text-align: center;
    height: 88rpx;
    line-height: 88rpx;
    display: flex;
    flex-flow: row;
    justify-content: space-between;
}
.swiper-tab-item{
    width: 30%; 
    color:#434343;
}
.active{
    color:#F65959;
    border-bottom: 4rpx solid #F65959;
}
/* swiper{
  text-align: center;
} */
.slide-image {
  width: 100%;
  height: 100px;
}
.swiper-box {
  display: block;
  background: linear-gradient(0deg, #0f9e8b 0%, #0f9e8b 100%);
  height: 175px;
  width: 100%;
  overflow: hidden;
}
.swiper-box view {
  color:rgb(250, 239, 239);
  text-align: center;
}
.toa {
  line-height: 35px;
  padding: 5px;
}
/*tab panel 结束*/
.desc {
  margin-bottom: 15px;
  border-bottom: 1 solid orangered;
  text-align: center;
}
.desc p {
  margin: 8px;
}
.imp{
  text-align: center;
  font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
  line-height: 30px;
  font-size: 40rpx;
  color:rgb(66, 66, 235);
  width: 100%;
  padding:5px;
}
.imp::before{
  content: '';
  border: 1px solid rgb(20, 95, 20);
  border-radius: 10px;
  width:10px;
}
.imp::after{
  content: '';
  border: 1px solid rgb(20, 95, 20);
  border-radius: 10px;
  width:10px;
}
.addre {
  color:rgb(90, 83, 83);
  line-height: 30px;
  font-size: 40rpx;
}
/* p::before{
  content: '';
  border-right: 3px solid rgb(20, 95, 20);
  width:5px;
  padding: 5px;
} */
.end-line {
  margin-top: 10px;
  border-top:1px solid orangered;
  border-bottom: 1px solid orangered;
  margin-bottom: 10px;
}
.cm1 {
  line-height: 50px;
}
.cm2 {
  line-height: 50px;
}
.cm1::before{
  content: '【'
}
.cm1::after{
  content: '】'
}
.cm2::before{
  content: '【'
}
.cm2::after{
  content: '】'
}
.company {
  margin: 25px;
  color:lightgray;
  text-align: center;
}
.company p {
  line-height: 30px;
}
</style>
