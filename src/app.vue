<!--主入口 -->
<template>
	<div id="app" style="height:100%;">
		<!-- 路由 页面切换 -->
    	<transition name="fade" mode="out-in">
    		<template>
	            <keep-alive v-if="$route.meta.keepAlive">
	                <router-view></router-view>
	            </keep-alive>
            <router-view v-if="!$route.meta.keepAlive"></router-view>
        </template>
    	</transition>
  	</div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
	computed: mapGetters({
	    userInfo: 'userInfo'
	}),

	methods: {
		...mapActions([
			'setUser'
		]),
	}
}
</script>

<style lang="sass">
// 导入css
@import 'styles/style'
// 导入iconfont
@import 'styles/iconfont/iconfont.css'
// 动画
.fade-enter-active, .fade-leave-active
    transition: opacity .5s
.fade-enter, .fade-leave-active
    opacity: 0
</style>