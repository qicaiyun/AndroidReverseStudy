### FRIDA

* 为Frida改成非标准端口：./frida-server-12.10.2-android-arm -l 0.0.0.0:8888

* 标准搭配：frida==12.8.0 frida-tools==5.3.0 objection1.8.4

* 列出手机里所有包名: frida-ps -H 192.168.199.237(手机ip):8888

* 查看frida服务是否可用：frida-ps -U  android.process.acore

* 查看进程：frida-ps -U  | grep 包名

* 指定多个pid：使用-p参数，指定pid

* 脚本注入：
    > 1) attach模式：frida -U android.process.acore -l s1.js
    > 2) spawn模式：frida -U --no-pause -f com.xes.jazhanghui.activity -l hash.js

* Options：  
    命令行模式
    > 1)  -f 为spwan模式，以全新的进程启动一个app。如果不加f，就是先让程序一段时间运行在attach上去。
    > 2)  -l 指定hook脚本
    > 3)  -o xxx.txt   把结果输出到txt文件
    > 4)  --no-pause 继续、恢复执行的意思，如果加-f，不加--no-pause,程序会挂起，需要在命令行手动执行%resume，让程序恢复执行，hook脚本也执行。
    > 5)  F  最前台进程, frida -UF  

    交互模式
    > 1)  %resume 用命令行启动frida时,进入交互界面后，如果不加--no-pause，要输入此命令，使程序继续执行。
    > 2)  %reload 用来重新加载脚本
    > 3)  Frida   用命令行启动frida时,进入交互界面后，查看环境
    > 4)  console.log('hello') 可以直接运行js命令