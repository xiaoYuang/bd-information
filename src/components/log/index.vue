<template>
  <div class="submenu-container">
    <div class="submenu-aside dh200">
      <div class="submenu-hd">
        <span>日志管理</span>
      </div>
      <el-menu :default-active="$route.path"
               class="submenu"
               router>
        <el-menu-item v-for="(item,index) in logList"
                      :key="index"
                      :index="item.path"
                      :class="{'is-active':isActived(item.path)}">{{item.name}}</el-menu-item>
        <!--<el-menu-item index="/facility/activation" :class="{'is-active':isActived('/facility/activation')}">激活设备</el-menu-item>-->
        <!--<el-menu-item index="/facility/grouping" :class="{'is-active':isActived('/facility/grouping')}">设备分组</el-menu-item>-->
      </el-menu>
    </div>

    <div class="content-wrapper">
      <breadcrumb class="breadcrumb-container"></breadcrumb>
      <router-view></router-view>
    </div>
  </div>
</template>

<script>
  import Breadcrumb from '@/components/common/Breadcrumb'
  export default {
    name: 'index',
    components: {
      Breadcrumb
    },
    data() {
      return {
        logList: [
          { path: '/log/loginLog', name: '用户登录登出日志' },
          { path: '/log/administrator', name: '管理员操作日志' },
          { path: '/log/client', name: '客户端通讯日志' },
        ]
      }
    },
    methods: {
      isActived(path) {
        let isActived = this.$route.fullPath.indexOf(path) != -1
        return isActived
      }
    }
  }
</script>

<style scoped>

</style>
