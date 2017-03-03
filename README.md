# study-css
##本人踏入前端学习大坑中，现在正在爬坑

###在学习的第一个阶段遇到一个margin重叠的问题，根据网上收集的资料汇总，总结出来的一些经验。所谓 margin重叠就是子级元素在设置margin-top这个属性的时候，会影响到父级的元素的margin-top，这让我头疼的很久。如图：

####根据网上查找资料，总结出来几种会发生的情况。
  
  1、父层的margin-top与一系列子层中第一个层的margin-top合并
  
  2、上层的margin-bottom与下层的margin-top合并，此时margin值为合并margin值中的最大值。至于负margin，就从正相邻margin的最大值中减去负相邻margin的绝对值的最大值。如果没有正margin，就用0减去相邻margin的绝对值的最大值
  
  3、层高为0时，自身的margin-top和margin-bottom合并
  
####解决方案
  1、一个浮动的盒与任何其它盒之间的margin不会合并（甚至一个浮动盒与它的流内子级之间也不会）
  
  2、建立了新的块格式化上下文的元素（例如，浮动盒与’overflow’不为’visible’的元素）的margin不会与它们的流内子级合并
  
  3、绝对定位的盒的margin不会合并（甚至与它们的流内子级也不会）
  
  4、内联盒的margin不会合并（甚至与它们的流内子级也不会）
  
  5、一个流内块级元素的bottom margin总会与它的下一个流内块级兄弟的top margin合并，除非兄弟有空隙
  
  6、一个流内块级元素的top margin会与它的第一个流内块级子级的top margin合并，如果该元素没有top border，没有top padding并且该子级没有空隙
  
  7、一个’height’为’auto’并且’min-height’为0的流内块级盒的bottom margin会与它的最后一个流内块级子级的bottom margin合并，如果该盒没有bottom padding并且没有bottom border并且子级的bottom margin不与有空隙的top margin合并
  
  8、盒自身的margin也会合并，如果’min-height’属性为0，并且既没有top或者bottom border也没有top或者bottom padding，并且其’height’为0或者’auto’，并且不含行盒，并且其所有流内子级的margin（如果有的话）都合并了
  
 ####具体css操作
  
  1、都用float来定位（有条件要求，适用范围较广）
  
  2、为父元素添加overflow不为visiable 的属性 （适用范围极广，推荐使用）
  
  3、为元素添加border（一般不用）
  
  4、使用绝对定位（适用范围较窄）
  
  5、父元素增加padding-top属性（改变尺寸，不建议使用）
  
###关于display：inline-block的问题。
  
#####quetion1 问题描述：一个父级div块里面包含两个div块，将两个div设置display为inline-block，然后两个div并没有对齐，而是上下错位的。

####解决思路:
   1、将div设置为float，此时inline-block已经无效，可以不要
   
   2、将后者的vertical-align设置为top，两个元素即可对齐。
### 问题3：设置透明度问题opacity和设置background的rbga（），其中opacity设置起透明度后其子元素也会受到透明度的改变，使用rgba不会改变子元素的透明度。
