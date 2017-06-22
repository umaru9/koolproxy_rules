## 目标视频网站

| Site | URL | 支持情况 | 采用方式 | 过滤状态 |
| :--: | :-- | :-----: | :-----: | :-----: |
| 腾讯视频 | <http://v.qq.com/> |✓| 跳过 | pass |
| 乐视视频 | <http://www.le.com/> |✓| 跳过 | pass |
| 新浪视频 | <http://video.sina.com.cn/> |✓| 跳过 | pass |
| 风行视频 | <http://www.fun.tv/> |✓| 跳过 | pass |
| 暴风视频 | <http://www.baofeng.com/> |✓| 跳过 | pass |
| 酷6视频 | <http://www.ku6.com/> |✓| 跳过 | pass |
| 凤凰视频 | <http://v.ifeng.com/> |✓| 跳过 | pass |
| 爱奇异视频 | <http://www.iqiyi.com/> |✓| 跳过 | pass |
| 土豆视频 | <http://www.tudou.com/> |✓| 跳过 | pass |
| 优酷视频 | <http://www.youku.com/> |✓| 跳过 | pass |
| 17173视频 | <http://v.17173.com/> |✓| 跳过 | pass |
| 搜狐视频 | <http://tv.sohu.com/> |✓| 跳过 | pass |
| 56视频 | <http://www.56.com/> |✓| 跳过 | pass |
| 虎牙视频 | <http://v.huya.com/> |✓| 跳过 | pass |

## 已知问题(BUG)
- .....

## Thanks to:
### for static rule
[adblock project](https://getadblock.com/)</br>
[xwhyc](https://github.com/adbyby)</br>
[CJX](https://github.com/cjx82630)</br>
[yiclear](https://www.yiclear.com)</br>
[adsafe](http://www.newadblock.com)</br>
[15536900](https://bitbucket.org/kafan15536900)</br>

## 声明
部分去视频播放器引用:

[OpenGG](http://opengg.me/)</br>
[project YoukuAntiADs by haoutil](http://bbs.kafan.cn/thread-1509944-1-1.html)</br>
[15536900](http://bbs.kafan.cn/thread-1507278-1-1.html)</br>
[adsafe](http://www.newadblock.com)</br>

...</br>

## WIKI

!  ******************************* koolproxy 自定义过滤语法简表 *******************************
!  ------------------------ 规则基于adblock规则，并进行了语法部分的扩展 ------------------------
!  ABP规则请参考https://adblockplus.org/zh_CN/filters，下面为大致摘要
!  "!" 为行注释符，注释行以该符号起始作为一行注释语义，用于规则描述
!  "@@" 为白名单符，白名单具有最高优先级，放行过滤的网站，例如:@@||taobao.com
!  ------------------------------------------------------------------------------------------
!  "*" 为字符通配符，能够匹配0长度或任意长度的字符串，该通配符不能与正则语法混用。
!  "^" 为分隔符，可以是除了字母、数字或者 _ - . % 之外的任何字符。
!  "~" 为排除标识符，通配符能过滤大多数广告，但同时存在误杀, 可以通过排除标识符修正误杀链接。
!  注：通配符仅在 url 规则中支持，html 规则中不支持
!  ------------------------------------------------------------------------------------------
!  "|" 为管线符号，来表示地址的最前端或最末端
!  "||" 为子域通配符，方便匹配主域名下的所有子域
!  用法及例子如下：(以下等号表示等价于)
!  ||xx.com/ad          =  http://xx.com/ad* || http://*.xx.com/ad*
!  ||http://xx.com/ad   =  http://xx.com/ad* || http://*.xx.com/ad*
!  ||https://xx.com/ad  =  https://xx.com/ad* || https://*.xx.com/ad*
!  |xx.com/ad           =  http://xx.com/ad*
!  |http://xx.com/ad    =  http://xx.com/ad*
!  |https://xx.com/ad   =  https://xx.com/ad*
!  ad                   =  http://*ad*
!  http://ad            =  http://*ad*
!  https://ad           =  不支持，需要指定域名，如下例
!  https://xx.com/ad    =  |https://xx.com/ad  =  https://xx.com/ad*
!  [同时可以表示两个以及两个以上的域名]如下例子
!  https://xx.ad.com 和 https://xxx.xx.ad.com  =  ||https://ad.com (注意! 由于https的原因使用要非常谨慎,不可以大范围使用)
!  ------------------------------------------------------------------------------------------
!  兼容adblock规则的html规则语法，例如：
!  fulldls.com,torrentzap.com##.tp_reccomend_banner
!  但是推荐写成以下标准写法：
!  ||fulldls.com##.tp_reccomend_banner
!  ||torrentzap.com##.tp_reccomend_banner
!  如果一个网站html规则有多条，可以合并为这样：
!  ||torrentzap.com##.tp_reccomend_banner,.ad_top,[class="ad_right"]......
!  ------------------------------------------------------------------------------------------
!  文本替换语法：$s@匹配内容@替换内容@
!  文本替换例子：|http://cdn.pcbeta.js.inimc.com/data/cache/common.js?$s@old@new@
!  重定向语法：$r@匹配内容@替换内容@
!  重定向例子：|http://koolshare.cn$r@http://koolshare.cn/*@http://www.qq.com@
!  注：文本替换语法及重定向语法中的匹配内容不仅支持通配符功能，而且额外支持以下功能
!  支持通配符 * 和 ? 表示单个字符
!  支持全正则匹配，/正则内容/ 表示应用正则匹配
!  正则替换：替换内容支持 $1 $2 这样的符号
!  普通替换：替换内容支持 * 这样的符号，表示把命中的内容复制到替换的内容。（类似 $1 $2，但是 * 号会自动计算数字）
!  ------------------------------------------------------------------------------------------
!  未来将逐步添加相关语法，兼容adblock puls的更多语法，敬请期待。
!  ******************************************************************************************
