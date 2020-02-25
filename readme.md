# 基于PyUserInput实现自动复制

PyUserInput项目地址：https://github.com/SavinaRoja/PyUserInput

## 一. windows环境下的安装

* 安装pywin32, pyHook

从**https://www.lfd.uci.edu/~gohlke/pythonlibs**上下载对应版本的pywin32, pyHook

使用以下命令安装：

```cmd
pip install 对应包所在路径
```



* 安装PyUserInput

```
pip install PyUserInput
```



## 二. 实例

* 拖拽指定位置内容

```python
from pymouse import *
import time

def drag(start, end, mouse):
    """

    :param start: 开始位置
    :param end: 结束位置
    :param mouse:
    :return:
    """
    mouse.press(start[0], start[1])  # 左键按住
    time.sleep(2)
    mouse.move(end[0], end[1])  # 移动鼠标，此时左键是没有释放的
    time.sleep(1)
    mouse.release(end[0], end[1])  # 释放鼠标

if __name__=="__main__":
    mouse = PyMouse()
    drag([487, 368], [900, 500], mouse)
```



* 复制与黏贴

```python
from pykeyboard import *
from pymouse import *
import time

def drag(start, end, mouse):
    """

    :param start: 开始位置
    :param end: 结束位置
    :param mouse:
    :return:
    """
    mouse.press(start[0], start[1])  # 左键按住
    time.sleep(2)
    mouse.move(end[0], end[1])  # 移动鼠标，此时左键是没有释放的
    time.sleep(1)
    mouse.release(end[0], end[1])  # 释放鼠标

def copy(start, end, copy_to, mouse, keyboard):
    """

    :param start: 开始位置
    :param end: 结束位置
    :param copy_to: 复制到哪
    :param mouse:
    :param keyboard:
    :return:
    """
    drag(start, end, mouse)
    keyboard.press_keys([keyboard.control_l_key, "c"])
    mouse.click(copy_to[0], copy_to[1])
    keyboard.press_keys([keyboard.control_l_key, "v"])

if __name__=="__main__":
    mouse = PyMouse()
    keyboard = PyKeyboard()
    copy([487, 368], [900, 500],[487, 368], mouse, keyboard)
```

