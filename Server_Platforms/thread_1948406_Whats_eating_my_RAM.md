---
title: "Whats eating my RAM"
date: 2012-03-28
forum: Server Platforms
---

### Post by Dasoren on 2012-03-28
hi, I am some what new to RAM in linux. I have been using linux for about 3 years now, and most of the time with my on hardware, and lots of RAM, but I got a VPS from a Host, to host a TeamSpeak3 server for me that can be up 100% of the time and have a good network to the net. 

anyway, here is whats up, the server uses about 200-300MB of RAM, but now and then it uses up to 1GB, but lately it is using 1GB all the time. I have read alot about this and understand most of it, but I do not understand why it is using 1GB of RAM, when it should only be using 200-300MB, at most. 

```

"free -m"

             total       used       free     shared    buffers     cached
Mem:          2048       1032       1015          0          0          0
-/+ buffers/cache:       1032       1015
Swap:            0          0          0

"ps -aux"

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23548  1664 ?        Ss   Feb26   0:06 init
root      1285  0.0  0.0  14760  1096 ?        Ss   Feb26   0:00 /usr/sbin/xinetd -dontfork -pidfile /var/run/xinetd.pid -stayalive -inetd_compat
root      1299  0.0  0.1  49424  2668 ?        Ss   Feb26   0:42 /usr/sbin/sshd -D
root      1313  0.0  0.0  18888  1016 ?        Ss   Feb26   0:14 cron
syslog    1335  0.0  0.0  12536   772 ?        Ss   Feb26   0:34 /sbin/syslogd -u syslog
root      1349  0.0  0.0   6712   648 ?        Ss   Feb26   3:59 /usr/sbin/vnstatd -d
root      1390  0.0  0.0  68268  2072 ?        Ss   Feb26   3:23 sendmail: MTA: accepting connections
root      1414  0.0  0.3 108572  7400 ?        Ss   Feb26   6:24 /usr/sbin/apache2 -k start
root      1478  0.0  0.0  22124  1712 ?        Ss   Feb26   0:00 SCREEN -S ts3serverdasoren
root      1479  0.0  0.1  18040  2116 pts/1    Ss   Feb26   0:00 /bin/bash
root      1500  0.0  0.0   4180   624 pts/1    S+   Feb26   0:00 /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root      1503  3.4  1.1 277540 24156 pts/1    Sl+  Feb26 1522:43 ./ts3server_linux_amd64 start inifile=ts3server.ini
root      1598  0.0  0.0  22124  1644 ?        Ss   Feb26   0:00 SCREEN -S minecraft
root      1599  0.0  0.1  18040  2100 pts/3    Ss+  Feb26   0:00 /bin/bash
root      3247  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3274  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3337  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3658  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3685  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      3876  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root      5495  0.0  0.2 108572  4584 ?        S    01:58   0:00 /usr/sbin/apache2 -k start
root      5747  0.0  0.2 108572  4584 ?        S    02:40   0:00 /usr/sbin/apache2 -k start
root      5762  0.0  0.2 108572  4584 ?        S    02:42   0:00 /usr/sbin/apache2 -k start
root      7904  1.4  2.5 1055924 53928 pts/4   Sl+  04:31   1:05 java -Xms10M -jar JTS3ServerMod.jar
root      9333  0.0  0.0  15064  1124 pts/0    R+   05:46   0:00 ps -aux
root      9424  0.0  0.1  70796  3472 ?        Ss   Mar23   0:04 sshd: root@pts/0
root      9436  0.0  0.1  18064  2144 pts/0    Ss   Mar23   0:00 -bash
root      9453  0.0  0.0  22124  1712 ?        Ss   Mar23   0:00 SCREEN -S ts3bot
root      9454  0.0  0.1  18088  2120 pts/4    Ss   Mar23   0:00 /bin/bash
root     29807  0.0  0.0  22128  1716 ?        Ss   Mar23   0:00 SCREEN -S ts3servermcrealm
root     29808  0.0  0.1  18092  2168 pts/5    Ss   Mar23   0:00 /bin/bash
root     30380  0.0  0.0   4180   624 pts/5    S+   Mar23   0:00 /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root     30383  2.7  0.4 198508  9836 pts/5    Sl+  Mar23 174:02 ./ts3server_linux_amd64 start inifile=ts3server.ini
root     30596  0.0  0.2 108572  4584 ?        S    Mar27   0:00 /usr/sbin/apache2 -k start
root     32633  0.0  0.0  21860  1424 ?        Ss   Mar18   0:00 SCREEN -S mc
root     32634  0.0  0.1  18096  2164 pts/2    Ss+  Mar18   0:00 /bin/bash

"ps -axfu"

USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23548  1664 ?        Ss   Feb26   0:06 init
root      1285  0.0  0.0  14760  1096 ?        Ss   Feb26   0:00 /usr/sbin/xinetd -dontfork -pidfile /var/run/xinetd.pid -stayalive -inetd_compat
root      1299  0.0  0.1  49424  2668 ?        Ss   Feb26   0:42 /usr/sbin/sshd -D
root      9424  0.0  0.1  70796  3472 ?        Ss   Mar23   0:04  \_ sshd: root@pts/0
root      9436  0.0  0.1  18064  2144 pts/0    Ss   Mar23   0:00      \_ -bash
root      9556  0.0  0.0  15060  1072 pts/0    R+   06:01   0:00          \_ ps axfu
root      1313  0.0  0.0  18888  1016 ?        Ss   Feb26   0:14 cron
syslog    1335  0.0  0.0  12536   772 ?        Ss   Feb26   0:34 /sbin/syslogd -u syslog
root      1349  0.0  0.0   6712   648 ?        Ss   Feb26   3:59 /usr/sbin/vnstatd -d
root      1390  0.0  0.0  68268  2072 ?        Ss   Feb26   3:23 sendmail: MTA: accepting connections
root      1414  0.0  0.3 108572  7400 ?        Ss   Feb26   6:24 /usr/sbin/apache2 -k start
root      3337  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3685  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3876  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root     30596  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3247  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3274  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      3658  0.0  0.2 108572  4584 ?        S    Mar27   0:00  \_ /usr/sbin/apache2 -k start
root      5495  0.0  0.2 108572  4584 ?        S    01:58   0:00  \_ /usr/sbin/apache2 -k start
root      5747  0.0  0.2 108572  4584 ?        S    02:40   0:00  \_ /usr/sbin/apache2 -k start
root      5762  0.0  0.2 108572  4584 ?        S    02:42   0:00  \_ /usr/sbin/apache2 -k start
root      1478  0.0  0.0  22124  1712 ?        Ss   Feb26   0:00 SCREEN -S ts3serverdasoren
root      1479  0.0  0.1  18040  2116 pts/1    Ss   Feb26   0:00  \_ /bin/bash
root      1500  0.0  0.0   4180   624 pts/1    S+   Feb26   0:00      \_ /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root      1503  3.4  1.1 277540 24156 pts/1    Sl+  Feb26 1523:07          \_ ./ts3server_linux_amd64 start inifile=ts3server.ini
root      1598  0.0  0.0  22124  1644 ?        Ss   Feb26   0:00 SCREEN -S minecraft
root      1599  0.0  0.1  18048  2108 pts/3    Ss+  Feb26   0:00  \_ /bin/bash
root     32633  0.0  0.0  22136  1652 ?        Ss   Mar18   0:00 SCREEN -S mc
root     32634  0.0  0.1  18096  2164 pts/2    Ss+  Mar18   0:00  \_ /bin/bash
root      9453  0.0  0.0  22124  1712 ?        Ss   Mar23   0:00 SCREEN -S ts3bot
root      9454  0.0  0.1  18088  2120 pts/4    Ss   Mar23   0:00  \_ /bin/bash
root      7904  1.4  2.6 1055924 55952 pts/4   Sl+  04:31   1:18      \_ java -Xms10M -jar JTS3ServerMod.jar
root     29807  0.0  0.0  22128  1716 ?        Ss   Mar23   0:00 SCREEN -S ts3servermcrealm
root     29808  0.0  0.1  18092  2168 pts/5    Ss   Mar23   0:00  \_ /bin/bash
root     30380  0.0  0.0   4180   624 pts/5    S+   Mar23   0:00      \_ /bin/sh ./ts3server_minimal_runscript.sh start inifile=ts3server.ini
root     30383  2.7  0.4 198508  9836 pts/5    Sl+  Mar23 174:25          \_ ./ts3server_linux_amd64 start inifile=ts3server.ini


```

---

### Post by SeijiSensei on 2012-03-28
Did you read the responses in the other thread?  Linux typically uses all the machine's memory.  That which isn't devoted to storing program code is used to cache disk activity.  If you start additional programs, the memory devoted to caching will fall.

---

### Post by Dasoren on 2012-03-28
yes I did and was just looking at the ts3bot screen with the "java -Xms10M -jar JTS3ServerMod.jar" it needed to be "java -Xmx10M -jar JTS3ServerMod.jar" the -Xms to -Xmx, that is where is was, and every thing is good now. lol java killing again.

---

