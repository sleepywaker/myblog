<template>
    <div>
      <div :class="{infoShow:this.$store.state.isInfoShow,infoHide:!this.$store.state.isInfoShow}">
      <Header/>
      <div class="archive">
          <div class="article-content"> 
              <p class="fontA">{{artList.title}}</p>
              <p>{{artList.date}}</p>
             <p>    1、安装插件</p> 
              <p>   npm install vue-lazyload – save</p> 
               <p>   2、“src/main.js”引入插件,并使用use，设置参数（loading时显示图片）</p>
               <p>  import VueLazyLoad from &#x27;vue-lazyload&#x27;</p> 
                <p>  Vue.use(VueLazyLoad,{</p>
             <p>     loading:&quot;/static/loading-svg/loading-bars.svg&quot;</p>  
            <p>     })</p> 
             <p>    3、显示图片位置使用v-lazy指令，设置加载完成时的图片路径</p> 
              <p>  &lt;img v-lazy=&quot;&#x27;/static/&#x27;+item.productImg&quot; alt=&quot;&quot;&gt; </p>     
            
          </div>
      </div>
      <Footer/>
      </div>
      <Siteinfo/>
    </div>
  </template>
    
  <script>
  import './../../assets/css/articles.css'
  import Header from '@/components/Header.vue'
  import Footer from '@/components/Footer.vue'
  import Siteinfo from '@/components/Siteinfo.vue'
  import articles from './../../assets/articles.json'
    export default {
      data(){
        return {
          artList:'',
        }
      },
      mounted(){
        this.getArticle()
      },
      components:{
        Header,
        Footer,
        Siteinfo
      },
      methods:{
        getArticle(){
          this.artList=articles.art8; 
        }
      }
    }
  </script>
  <style scoped>
    .archive{
      min-height:calc(100vh - 210px);
      box-sizing:border-box;
      width:100%;
      background-color:#BBE4FF;
    }
    .title{
      display:block;
    }
    @keyframes in{
      from{
        padding-right:0;
        }
      to{
        padding-right:320px;
        }
    }
    @keyframes out{
      from{
        padding-right:320px;
      }
      to{
        padding-right:0;
      }
    }
  .infoShow{
      padding-right:320px;
      animation:in 0.5s ease-out;
    }
  .infoHide{
      padding-right:0;
      animation:out 0.5s ease-out;
    }
  </style>