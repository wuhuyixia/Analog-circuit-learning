# 立创实战派ESP32-S3

## CH340K

    https://item.szlcsc.com/datasheet/CH340K/1056391.html

![](/JLC/Images/24/12/img.png)

![](/JLC/Images/24/12/img_1.png)

![](/JLC/Images/24/12/img_2.png)

### [嵌入式MODEM通迅技术](https://blog.csdn.net/sukhoi27smk/article/details/19302411)

![](/JLC/Images/24/12/img_3.png)


## hello word 的实现

[参考文章](https://blog.csdn.net/Lovely_him/article/details/143655419)

![](/JLC/Images/24/12/img_5.png)

~~~
 idy.py build 编译
 烧录  idf.py {-p COM8} flash.  如果不指定端口号, 那么终端会自己遍历所有能用的端口号挨个尝试
 idf.py -p COM8 monitor 打开监视器
 Ctrl+] 退出监视器
 idf.py menuconfig [--help]  
~~~~

![](/JLC/Images/24/12/img_4.png)

![](/JLC/Images/24/12/img_6.png)

出现报错，头文件找不到    [解决](https://blog.csdn.net/qq_37868450/article/details/105013325)

![](/JLC/Images/24/12/img_7.png)

成功显示

![](/JLC/Images/24/12/img_8.png)

关于问题 `The path for ESP-IDF is not valid: /tools/idf.py not found. `  ，[方法1](https://blog.csdn.net/qq_44903752/article/details/142566895)
[方法2](https://blog.csdn.net/m0_57717860/article/details/142587208)

成功

![](/JLC/Images/24/12/img_9.png)

## 外设例程

    https://wiki.lckfb.com/zh-hans/szpi-esp32s3/beginner/key.html

### boot-key按键

关于

     "compileCommands":"${workspaceFolder}/build/compile_commands.json"

利用自动生成的地址导入，解决头文件问题

连接开发板到电脑，在 VSCode 上选择串口号，选择目标芯片为 esp32s3，串口下载方式，然后点击“一键三联”按钮，等待编译下载打开终端。
终端打开后，按 BOOT 按键，就可以在终端检测到按键按下，并输出按键的电平，如下所示，截取了最后几行。

    I (304) gpio: GPIO[0]| InputEn: 1| OutputEn: 0| OpenDrain: 0| Pullup: 1| Pulldown: 0| Intr:2
    I (314) main_task: Returned from app_main()
    GPIO[0] intr, val: 0

### BLINK

![](/JLC/Images/24/12/img_10.png)

![](/JLC/Images/24/12/img_11.png)

拓展接口是gpio10和11

![](/JLC/Images/24/12/img_12.png)

![](/JLC/Images/24/12/img_13.png)

选择io0为输出，如果你要获取当前的电平状态，请把此配置`io_conf.mode`模式为`GPIO_MODE_INPUT`，表示为输入模式；\
按住boot案件实现打印输出的电平变化