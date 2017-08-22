# vuex-mapState
Vuex中mapState用法

vuex里index.js中的用法

```
import Vue from 'vue'
import Vuex from 'vuex'
import mutations from './mutations'
import actions from './action'
import getters from './getters'

Vue.use(Vuex)

const state = {
    userInfo: { phone: 111 }, //用户信息
    orderList: [{ orderno: '1111' }], //订单列表
    orderDetail: null, //订单产品详情
    login: false, //是否登录
}

export default new Vuex.Store({
    state,
    getters,
    actions,
    mutations,
})
```

在模板中
```
computed: {
  ...mapState([
       'orderList',
       'login'
    ]),
},   
mounted(){  
  console.log(typeof orderList); ==>undefind
  console.log(typeof this.orderList)==>object
}   
```

mapState通过扩展运算符将store.state.orderList 映射this.orderList  这个this 很重要，这个映射直接映射到当前Vue的this对象上。


所以通过this都能将这些对象点出来，同理，mapActions, mapMutations都是一样的道理。牢记~~~
