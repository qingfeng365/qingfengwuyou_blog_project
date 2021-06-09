# css动画基础 - animation

语法：[MDN animation](https://developer.mozilla.org/zh-CN/docs/Web/CSS/animation)

## Animation 最基本的动画属性

掌握以下几个属性即可

- @keyframes
- animation 属性是一个简写属性，用于设置八个动画属性
  - animation-name
  - animation-duration
  - animation-timing-function
  - animation-delay
  - animation-iteration-count
  - animation-direction
  - animation-fill-mode
  - animation-play-state 实验功能，不考虑



|属性                      | 描述             |  缺省值        |
|:-----------------------:|:----------------:|:-------------:| 
|animation-name           |动画的名称          |  none        |
|animation-duration       |指定一个动画周期的时长|   0s         |
|animation-timing-function|动画的速度曲线       |  ease        |
|animation-delay          |动画开始延时时间     |    0s         |
|animation-iteration-count|动画运行的次数       |    1         |
|animation-direction      |动画向前循环         | normal       |
|animation-fill-mode      |对象动画时间之外的状态|    none       |


`关于 animation 简写的说明 `

- 顺序没有强制规定
- 但由于有两个属性都涉及时间值，因此第一个时间值会分配给 animation-duration
- 不属于关键字的字符串，会分配给 animation-name
- 只有 animation-name animation-duration 是必须设置的，因为这两个属性的初始值都不会产生动画

## 纵向连续滚动的示例

[codepen](https://codepen.io/qingfengwuyou/pen/VwpBxYO)

`html`

```html
<div class="scroll-view">
  <div class="ul">
    <div class="li">11111</div>
    <div class="li">22222</div>
    <div class="li">33333</div>
    <div class="li">44444</div>
    <div class="li">55555</div>
    <div class="li">11111</div>
  </div>
</div>
```

`css`

```css
@keyframes scroll {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(calc(-100% + 32px));
  }
}
.ul {
  animation-name: scroll;
  animation-duration: 5s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
  /* animation: scroll 5s linear infinite; 动画属性简写 */
  background-color: #dc3545;
}
.li {
  font-size: 16px;
  height: 32px;
  line-height: 32px;
  text-align: center;
}
.scroll-view {
  box-sizing: border-box;
  margin: 24px;
  background-color: #007bff;
  color: #fff;
  height: 32px;
  padding: 0 24px;
  border-radius: 20px;
  overflow: hidden;
  width: 180px;
}
```

`要点说明：`

