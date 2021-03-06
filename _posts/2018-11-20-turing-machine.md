---
layout: post
title:  "图灵机和可计算性"
date:   2018-11-20 22:28:22 -0500
categories: science
---

![AI](/asserts/ai.png)

人工智能近年来的崛起，来自于神经网络对经典机器学习的突破，也带了很多商机。众多人工智能初创企业如雨后春笋，视觉，语音，语义，硬件和无人驾驶技术蓬勃发展，
各大巨头也分设人工智能研究员，或者干脆转型成为“人工智能企业”。人工智能的从业者，创业者和投资人，都在试图找到一个问题的答案，机器到底能达到什么样的智能，
未来的强人工智能或者终极人工智能是否会出现，会在哪里，何时出现。只有看清了未来，才能够找到指引技术和企业革新的正确道路。
在我看来研究计算机科学的基础理论，也许是通向这个问题的正确道路。我们希望能够通过分析先辈留下的理论财富，能够逐步接近真相，进而更理性的判断人工智能的发展。

计算机科学的发展一直围绕着两个核心问题，一，如何优美的表达现实世界的问题，二，如何有效的用计算机程序解决他们。
为了理解终极人工智能是否能达到，我们需要需要理解现代计算机的理论计算极限，也就是可计算性。首先我们需要了解图灵机-turing machine.

## 图灵机
图灵机是一种理论计算机模型，在1936年阿兰图灵（Alan Turing）硕士阶段的论文（《论可计算数及其在判定问题中的应用》）中提出的, 被他成为自动机（automatic machine）。

![From Wikipedia](/asserts/turingmachine.jpg)

这种当时只存在于想象中的机器（上图）由一个控制器、一个读写头和一根无限长的纸带组成的，控制器控制读写头从纸带读取信息，也可写入信息到纸带，来完成运算。

算数的历史，可以追溯到人类早期文明的结绳计数，包括后来中国的珠算，莱布尼茨计算器，密码机，巴贝奇的差分机的发明，都属于创造计算机的尝试。直到图灵机的发明，才奠定了现代计算机的理论基础，他在数学上证明了物理机器计算的极限-可计算性。

## 可计算性和NP

### 可计算性
可计算性通俗的讲，就是给了我们评价数学问题是否可计算的标准，这个标准就是图灵机。从更现实的角度讲，只要是现代计算机能计算的，图灵机就一定能计算，图灵机算不出的，计算机也算不出。从图灵机发明到现在将近一个实际，仍然没有看到任何超越图灵机的理论模型出现，如概率图灵机，多道图灵机等众多理论模型都只是改进了效率，并未突破图灵机的理论范畴。

说清楚了计算机能算不能算的问题，我们再聊一聊算得快慢的问题，因为即使一个问题是可计算的，如果效率太低了，可能人有生之年也看不到计算的结果，没有任何意义。这就不得不介绍著名的NP问题，我有几位还在从事计算机理论研究的同学们，基本上都在和它作斗争。

### 复杂度
在介绍NP问题之前，我简单介绍一下复杂度（Complexity）的概念，这里我们仅以时间复杂度距离，时间复杂度指的是程序运行所耗费的时间函数，一般变量用n，n代表同一个问题的不同规模，可以是几十，几千或是几百万。因为计算机想也解决的数量级非常大，也就是n非常大，常常忽略函数的常数部分，用大些的O来表示负责度，如：O(n)表示线性的复杂度。

|      复杂度      | n=10 | n=100 | n=10,000 |  类型  |
|:----------------:|:----:|:------:|:----------:|:------:|
|      O(logn)     |   1   |    10    |     100       |   对数     |
|       O(n)       |   10   |   100     |    10,000        | 多项式 |
| O(n<sup>2</sup>) |    100  |    10000    |      1亿      | 多项式 |
| O(2<sup>n</sup>) |   1024   |     1.27 x 10<sup>30</sup>   |     1.995 x 10<sup>3010</sup>     |  指数  |

上面中从上到下，复杂度依次递增，如果表中数值代表计算的次数的话，随着n的增长，不同复杂度的需要的计算次数有数量级的区别。实际上在计算机问题中，这个n一般都非常大，增长的非常快，例如，数据量和用户量。在计算机里，指数级别的复杂度是不可接受的，如表所示，2的一万次幂是一个超出我们理解的天文数字，为了更直观的理解它到底有多大，我举例两个例子帮助理解，比它小的多的2的256次方要写这么长一串：

2<sup>256</sup> = 115,792,089,237,316,195,423,570,985,008,687,907,853,269,984,665,640,564,039,457,584,007,913,129,639,936

物理世界最大数字，应该是宇宙中粒子总合了，经天文学家估算，也不过1后面80个零到1后面81个零之间的一个数，2的一万次方则是1后面3010个零附近的数. 哪怕是2的100次方，一台每秒能运算百亿次的计算机，也不可能在百年之内得出结果。在实用计算机科学中，解决一个问题算法的复杂度，决定了它是否可以用在实际生产。

### P和NP

在计算机科学领域，P和NP是两个著名抽象问题集合，作为一个非计算机工作者，如果能够和程序员谈论P和NP的问题，是一件非常时髦的事情。P称作多项式时间，NP则是非多项式时间，任意一个判别问题（即给定输入，判断是否的问题），如果能够在多项式时间复杂度得出结果，就属于P，不能在多项式时间内得到结果的则属于NP。NP的问题集合是包含P的，

可以看出P类问题是我们计算机容易解决，而NP类问题中除了P类问题，其他的都是很难在有限时间内得到解答的，我们往往都希望将实际问题转化为P类问题，利用计算机解决，而不愿遇到NP中比较难的问题（NP-Hard）。那么如何判断一个问题是P还是NP-Hard呢，一个简单的办法就是了解已知的NP-Hard问题，提前判断是否是无法解决的问题。感兴趣的同学还可以关注一下NP和P的等价性论断，NP-complete的概念等。复杂度的理论给我们一个效率判断体系，理解了P和NP的概念，有助于进一步理解计算机计算的极限，很多问题虽然是可以计算的，但是无法在短时间内得到结果。很有意思的一个复杂度的应用是非对称加密，正常加密过程和解密过程都是很快速的，然而没有钥匙的破解过程是NP-Hard, 现代区块链技术的发展也依赖于相似的应用，未来我会在别的章节里介绍。

人工智能的难题，有哪些是和NP-Complete等价的，或者属于NP-Hard，有待讨论。









