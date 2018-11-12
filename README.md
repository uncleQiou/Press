# Press
note
# Windows中查看端口占用及关闭对应进程
+ 开始--运行--cmd 进入命令提示符 输入netstat -ano 即可看到所有连接的PID，之后在任务管理器（右键电脑屏幕的状态栏即可找到）中找到这个PID所对应的程序。如果任务管理器中没有PID这一项,可以在任务管理器中选"查看"-"选择列" 。

> 1.查看所有连接的PID

          开始--运行--cmd  ，输入netstat -ano

           找到端口号对应的PID后，从任务管理器中停止PID对应程序。

> 2.查看占用8080端口程序

          ①先C:>netstat -ano|findstr "8080"

           协议    本地地址           外部地址           状态           PID

           TCP 127.0.0.1:1433   0.0.0.0       LISTENING     4984

           ②再C:>tasklist|findstr "4984"

          映像名称             PID   会话名        会话#   内存使用

          sqlservr.exe         4984 Services       0      51,844 K

    P：很清楚吧，是sqlserver服务占用端口”1433“，然后Kill 之。

> 3.结束该进程

          C:\>taskkill /f /t /im sqlservr.exe
          或者
          C:\>taskkill /F /pid “4984”
