---
id: 973
title: ChromiumVim常用操作
date: 2016-11-27T11:26:20+08:00
author: cloud
layout: post
guid: http://www.cloudchou.com/?p=973
permalink: /work/post-973.html
categories:  
  - work
tags:
  - 工作效率
  - ChromiumVim常用操作
  - CVim常用操作
---

ChromiumVim插件是Chrome的一个插件，也叫CVim，可以让你浏览网页时，用键盘代替鼠标进行操作，本篇只和大家分享使用该插件时的常用操作，熟练使用这些快捷键之后，大部分情况下就不需要再使用鼠标了。


##  背景

我越来越讨厌用鼠标，因为我用鼠标经常无法准确的点击我想要点击的元素，并且常常要移动大片区域才能移动到我想要点击的元素上，如果将鼠标调整的比较灵敏呢，经常无法精确移动到点击区域，如果将鼠标调整的稍微迟钝一点又觉得太慢，所以用鼠标总是觉得不爽。但是用Windows没法避免用鼠标，尤其是在浏览器上浏览网页时。

当同事和我分享ChromiumVim这个插件时，立即觉得眼前一亮，装了这个插件之后，大部分情况下，就可以用键盘代替鼠标了。但是ChromiumVim的快捷键特别多，很难记住这么多，我只想记住高频操作，于是和大家分享一下我使用的CVim的常用快捷键，大部分情况下已经够用了。


## 常用操作

1.  点击链接(比如搜索某个关键字之后，需要点击其中某个，或者看到某个菜单栏，想要选中其中某个菜单)

    f: 输入指示字母后，如果是链接，则在本tab里打开链接
 
    F: 输入指示字母后，如果是链接，则在新tab里打开链接，并且将新tab激活

    > F 原本是只在新tab里打开链接，但是不会将新tab激活，需要在Setting里修改配置 添加 map F createActiveTabbedHint

    > 这里的f表示focus的含义

    输入f之后的效果如下图所示，如果要点击某个链接，只需要输入链接上提示的字幕即可

    ![cvim_f_effect](/assets/blogimgs/cvim_f_effect.png)

2.  打开输入的网址(有时候停留在某个页面时，想打开新网页，可以使用这个操作)

    o: 输入o之后，会打开命令提示工具条，工具条有提示词:open, 输入你想打开的链接或者关键字时，工具条会提示你可选项，如果你想打开第一个可选项，只需按回车键就可以了，否则使用tab键进行选择，这个非常有用，CVim会提示你历史打开过的内容。 选择好按回车键后，会在本页面打开你的选择项。

    t:  和o类似，但是工具条提示tabnew, 会在新页面打开

    工具条显示提示词之后，可以先输入搜索引擎的缩略词，然后再输入搜索内容，这样的话会打开搜索引擎去搜你输入的内容，像我的话配置了3个搜索引擎，并为之赋了缩略词。配置方式如下所示: 

    ```
    let searchengine zhihu = 'https://www.zhihu.com/search?q=%s'
    let searchengine youdao = 'http://youdao.com/w/eng/%s'
    let searchalias g = 'google'
    let searchalias zh = 'zhihu'
    let searchalias yd = 'youdao'
    ```

    所以当我输入o之后，再输入g，然后输入test+回车键，则会在当前页面打开google并搜索test，如下图所示:

    ![cvim_o_google](/assets/blogimgs/cvim_o_google.png)

3.  使用google 搜索某个词语 

    a (其实是命令:tagnew google的缩写)

    输入a 之后然后输入要搜索的关键字


4.  翻页(搜索关键字之后，通常会有很多页的内容，这时候适合用翻页快捷键) 

    [[:  连续按两下'['，可以快速的翻到上一页  

    ]]:  连续按两下']'，可以快速的翻到下一页  

    > 为了让中文也支持翻页，需要做下面的配置,以识别上一页或者下一页

    ```
    let previousmatchpattern = '((?!last)(prev(ious)?|上一(页|頁)?|newer|back|«|less|<<?|gigi‹fd| )+)'
    let nextmatchpattern = '((?!first)(下一(页|頁)?|next|older|more|>>?|›|»|forward| )+)'
    ```

5.  焦点放到页面第1个输入框: gi(go to inputbox)

6.  关掉右侧所有标签页: gx$

7.  页面历史
   
    回退: Alt + key-left
   
    前进: Alt + key-right

8.  tab操作
   
    跳转到第1个tab: g0   

    跳转到最后1个tab: g$

    跳转到指定tab: ctrl + 数字指定tab顺序，如 ctrl+1跳转到第2个tab

    当前tab向前移动: <

    当前tab向后移动: >

9.  网页内跳转

    调到文件头: gg 

    跳转到网页尾:shift+g 

10.  查找

     使用/进入查找模式， 然后使用n跳转到下一个匹配单词， 使用N跳转到上一个匹配的单词

     查找时可以使用正则匹配，这个非常方便

11.  复制文字

     使用查找定位到某个文字后按v进入visual模式可选择要复制的文字， 然后可以使用hjkl移动，

     h向左移动 j向上移动 k向下移动 l向右移动 

     然后使用y就可以复制了

12.  修改配置 

     :settings，注意在配置界面修改好之后，必须点击Save保存，然后刷新页面新配置才能生效，我在此处折腾了很久。

13.  查找帮助 :help

## CVim目前支持不好的一些地方

1.  鼠标悬停操作支持不好，虽然官方说可以用q创建鼠标悬停事件，但尝试后发现不可用

2.  某些网页只一个输入框，某个输入框得到焦点后，它会一直霸占焦点，此时就算按ese，也不能失去焦点，所以不能使用CVim快捷命令


## 玩转CVim遇到的一些坑

1.  第1次安装完插件CVim后，必须重启Chrome才能使用该插件，刚开始安装的人很容易被这个坑到

2.  配置修改后不能立即生效, 网页加载过程中也不能使用CVim

    必须刷新网页，或者打开新的tab这个配置才能生效，因为CVim毕竟只是一个网页插件，浏览器的工作原理是等页面的所有内容加载后再重新加载插件，而插件不是每次都实时地去读这个配置的，所以必须刷新网页，等页面加载完毕后，新配置才生效。

## 总结

总的来说，CVim是一个很棒的插件，我现在已经熟练使用这些常用操作，大部分情况下不再用鼠标浏览网页了。

再和大家分享一下我的[CVim配置](https://gist.github.com/cloudchou/b280814bd87bc0013967f4fd68f38fd0)的Gist。







   ​