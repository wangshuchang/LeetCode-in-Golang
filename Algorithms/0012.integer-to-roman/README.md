# [12. Integer to Roman](https://leetcode.com/problems/integer-to-roman/)

## 题目
Given an integer, convert it to a roman numeral.

Input is guaranteed to be within the range from 1 to 3999.

以下是维基百科上关于[罗马数字](https://zh.wikipedia.org/zh-cn/%E7%BD%97%E9%A9%AC%E6%95%B0%E5%AD%97)的解释。

罗马数字共有7个，即Ⅰ（1）、Ⅴ（5）、Ⅹ（10）、Ⅼ（50）、Ⅽ（100）、Ⅾ（500）和Ⅿ（1000）。按照下述的规则可以表示任意正整数。需要注意的是罗马数字中没有“0”，与进位制无关。一般认为罗马数字只用来记数，而不作演算。

1. 重复数次：一个罗马数字重复几次，就表示这个数的几倍。
1. 右加左减：
    1. 在较大的罗马数字的右边记上较小的罗马数字，表示大数字加小数字。
    1. 在较大的罗马数字的左边记上较小的罗马数字，表示大数字减小数字。
    1. 左减的数字有限制，仅限于I、X、C。比如45不可以写成VL，只能是XLV
    1. 但是，左减时不可跨越一个位值。比如，99不可以用IC（ 100-1）表示，而是用XCIX（ [100-10]+[10-1]）表示。（等同于阿拉伯数字每位数字分别表示。）
    1. 左减数字必须为一位，比如8写成VIII，而非IIX。
    1. 右加数字不可连续超过三位，比如14写成XIV，而非XIIII。（见下方“数码限制”一项。）
1. 加线乘千：
    1. 在罗马数字的上方加上一条横线或者加上下标的Ⅿ，表示将这个数乘以1000，即是原数的1000倍。
    1. 同理，如果上方有两条横线，即是原数的1000000 倍。
1. 数码限制：
    1. 同一数码最多只能连续出现三次，如40不可表示为XXXX，而要表示为XL。

## 解题思路
关于罗马数字的说明，看起来很复杂。但对于编程来说，最关键的一条是
> 但是，左减时不可跨越一个位值。比如，99不可以用IC（ 100-1）表示，而是用XCIX（ [100-10]+[10-1]）表示。（等同于阿拉伯数字每位数字分别表示。）
说明，罗马数字和阿拉伯数字一样，都是按位表示的。只要把与“个十百千”上的阿拉伯数字对应的罗马数字罗列出来，就可以自由组合得到罗马数字了。

## 总结
表驱动法，是《代码大全》中提到的一种编程模式，可以应对复杂的查询情况。