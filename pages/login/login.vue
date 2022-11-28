<template>
  <view class='login-warp'>
    <swiper class='index-swiper' @change='currentChange' autoplay>
      <swiper-item>
        <image src='/static/login/bg-1.jpg' mode='widthFix' class='bg-img'></image>
      </swiper-item>
      <swiper-item>
        <image src='/static/login/bg-2.jpg' mode='widthFix' class='bg-img'></image>
      </swiper-item>
      <swiper-item>
        <image src='/static/login/bg-3.jpg' mode='widthFix' class='bg-img'></image>
      </swiper-item>
    </swiper>
    <view class='btn-warp'>
      <view @click='login' class='pets-button'> 登录</view>
      <view class='dot-warp'>
        <view v-for='(item, index) in 3' :key='item' class='dot-item'
              :class="activeIndex == index ? 'active' : ''"></view>
      </view>
    </view>
<!--    <Login ref='login'></Login>-->
  </view>
</template>

<script>
// import { delItem } from '@/hooks/useStorage';
// import CustomCheckBox from '@/components/CustomCheckBox/CustomCheckBox.vue';
// import Login from './components/LoginDialog.vue';

// import { clearClientId } from '@/hooks/useSetClientId';
// import InterceptorTimer from '@/api/InterceptorTimer';
//
// const interceptorInstance = InterceptorTimer.getInstance();
export default {
  // components: { CustomCheckBox, Login },
  data() {
    return {
      activeIndex: 0
    };
  },
  onShow() {
    // this.$eventAnalyse.sendReport('CLICK', { descr: `访问注册页` });
    // // 清空本地使用时间
    // interceptorInstance.clearTime();
    // this.clearUserInfo();
    // // #ifdef APP-PLUS
    // clearClientId();
    // // #endif
  },
  methods: {
    clearUserInfo() {
      delItem('access_token');
      delItem('refresh_token');
      delItem('userSig');
      delItem('userId');
    },
    //登录弹层
    login() {
      this.$refs.login.init();
    },

    currentChange(e) {
      this.activeIndex = e.detail.current;
    }
  }
};
</script>
<style lang='scss' scoped>
.login-warp {
  width: 100%;
  height: 100%;
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  top: 0;
}

.index-swiper {
  width: 100%;
  height: 100%;
}

.bg-img {
  width: 100%;
  height: 100%;
}

.dot-warp {
  width: 100%;
  display: flex;
  align-items: center;
  margin: 64rpx 0;
  justify-content: center;
}

.dot-item {
  width: 8rpx;
  height: 8rpx;
  border-radius: 50%;
  background-color: gray;
  margin-right: 8rpx;
  background-color: #cccccc;

  &.active {
    background-color: #03bdac;
    width: 40rpx;
    height: 8rpx;
    border-radius: 68rpx;
  }
}

.btn-warp {
  position: absolute;
  left: 24rpx;
  right: 24rpx;
  z-index: 50;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
  bottom: 0rpx;
  bottom: calc(0rpx + constant(safe-area-inset-bottom));
  bottom: calc(0rpx + env(safe-area-inset-bottom));
}

.pets-button{
  width: 100%;
  height: 49px;
  border-radius: 8rpx;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 36rpx;
  background: #03bdac;
  font-weight: 400;
  color: #fff;
}

.icon-right {
  margin-right: 20rpx;
}

.plain {
  margin-top: 24rpx;
}
</style>
