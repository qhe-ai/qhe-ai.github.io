---
layout: post
title: A quick reference manual for pandas and seaborn
date: 2022-7-20 8:00
description:
tags: RL, Programming
categories: blog
chart:
  vega_lite: true
---



# Seaborn Pandas 速查手册

这篇笔记是作为速查来使用的，读者无需仔细阅读，了解原理



## 获取表头

```
data.columns

Index(['beta', 'alien', 'bank_heist', 'freeway', 'frostbite', 'jamesbond',
       'kangaroo', 'ms_pacman'],
      dtype='object')
```



## 设置刻度字体 图例字体 大小 图例标题有无



https://zhuanlan.zhihu.com/p/437747308

```
ax = sns.scatterplot(x='账单', y='小费', hue='性别', data=tips)
x = [-40, -20, 0, 20, 40]
ax.set_xticks(x)
xlabs = [-40, -20, 0, 20, 40]
ax.set_xticklabels(xlabs, fontsize=14) #设置X座标轴刻度标签字体
y = [0, 2, 4, 6, 8, 10]
ax.set_yticks(y)
ylabs = [0, 2, 4, 6, 8, 10]
ax.set_yticklabels(ylabs, fontsize=14, rotation=30) #设置Y座标轴刻度标签字体
ax.set_ylabel('小费', fontsize=14) #设置Y坐标轴标签字体
ax.set_xlabel('账单', fontsize=14) #设置X坐标轴标签字体
ax.set_title('简单示例图', fontsize=14) #设置标题字体
ax.legend(title = "性别", fontsize = 12, title_fontsize = 14) #设置图例标题、图例标题字体大小、图例字体大小
```



**关于图例**

https://stackoverflow.com/questions/51579215/remove-seaborn-lineplot-legend-title

使用以下的方法可以去掉图例的标题，设置图例大小

```
handles, labels = ax.get_legend_handles_labels()
ax.legend(handles=handles[1:], labels=labels[1:])
plt.setp(ax.get_legend().get_texts(), fontsize=20)
```





## 控制坐标轴 刻度 标签 是否可见 旋转 自动调整

关闭某个子图坐标轴，不可见框线

```python
ax[1, 1].set_axis_off()
```



关闭刻度，可见框线

```python
ax[1, 1].get_xaxis().set_visible(False)
ax[1, 1].get_yaxis().set_visible(False)
```



关闭标签

```
ax.set(xlabel=None)
ax.set(ylabel=None)
```



```
fig.autofmt_xdate()
fig.yticks(y_tick,fontsize=20)
fig.autofmt_ydate()
```



## plt 的画线风格



https://blog.csdn.net/qq_34940959/article/details/78488208



颜色（color 简写为 c）：

蓝色： 'b' (blue)
绿色： 'g' (green)
红色： 'r' (red)
蓝绿色(墨绿色)： 'c' (cyan)
红紫色(洋红)： 'm' (magenta)
黄色： 'y' (yellow)
黑色： 'k' (black)
白色： 'w' (white)
灰度表示： e.g. 0.75 ([0,1]内任意浮点数)
RGB表示法： e.g. '#2F4F4F' 或 (0.18, 0.31, 0.31)
任意合法的html中的颜色表示： e.g. 'red', 'darkslategray'
线型（linestyle 简写为 ls）：

实线： '-'
虚线： '--'
虚点线： '-.'
点线： ':'
点： '.' 
点型（标记marker）：

像素： ','
圆形： 'o'
上三角： '^'
下三角： 'v'
左三角： '<'
右三角： '>'
方形： 's'
加号： '+' 
叉形： 'x'
棱形： 'D'
细棱形： 'd'
三脚架朝下： '1'（就是丫）
三脚架朝上： '2'
三脚架朝左： '3'
三脚架朝右： '4'
六角形： 'h'
旋转六角形： 'H'
五角形： 'p'
垂直线： '|'
水平线： '_'
gnuplot 中的steps： 'steps' （只能用于kwarg中）
标记大小（markersize 简写为 ms）： 

markersize： 实数 
标记边缘宽度（markeredgewidth 简写为 mew）：

markeredgewidth：实数
标记边缘颜色（markeredgecolor 简写为 mec）：

markeredgecolor：颜色选项中的任意值
标记表面颜色（markerfacecolor 简写为 mfc）：

markerfacecolor：颜色选项中的任意值
透明度（alpha）：

alpha： [0,1]之间的浮点数
线宽（linewidth）：

linewidth： 实数




## 调色系统

http://seaborn.pydata.org/tutorial/color_palettes.html?highlight=palette%20rocket

