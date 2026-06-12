---
title: "Ports Open. Where do I begin?"
date: 2006-01-10
forum: Server Platforms
---

### Post by byen on 2006-01-10
Hey guys,
Ok. ive been an Ubuntu Users for a long time and during Hoary I installed firestarter and an online port scan test turned out good. But After reinstalling Breezy I went to Shield up and they gave me a report that "many or all of my ports were open and I need to close the ports" And this was with Firestarter ON!
I tried installing nessus but it says "login failed" or "host not found' Ive loked around a Lot and havnt found much that could help me here.

This is very very important to me cuz I use wifi and live in an area where there are over 15 wifi connections including a coffee house which gives users access to sit down and have a play at the wifi networks in the neighborhood and I dont want to get "violated :( "

Please help. Thank you for your time.
Byen

---

### Post by LordHunter317 on 2006-01-10
Post the output of netstat -an --inet --inet6

---

### Post by byen on 2006-01-10
thank you for replying.. here is the output

___________________________________________________________
byen@xblade:~$ netstat -an --inet --inet6
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:1241            0.0.0.0:*               LISTEN
tcp        0      0 192.168.0.100:56654     64.233.167.125:5222     ESTABLISHED
tcp        0      0 192.168.0.100:34332     207.46.0.82:1863        ESTABLISHED
tcp        0      0 192.168.0.100:46475     66.249.81.99:80         TIME_WAIT
tcp        0      0 192.168.0.100:46476     66.249.81.99:80         TIME_WAIT
tcp        0      0 192.168.0.100:46478     66.249.81.99:80         TIME_WAIT
tcp        0      0 192.168.0.100:46479     66.249.81.99:80         TIME_WAIT
tcp        0      0 192.168.0.100:46480     66.249.81.99:80         TIME_WAIT
tcp        0      0 192.168.0.100:37999     216.155.193.172:5050    ESTABLISHED
udp        0      0 0.0.0.0:32768           0.0.0.0:*
udp        0      0 127.0.0.1:53            0.0.0.0:*
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp6       0      0 :::32769                :::*
byen@xblade:~$
_______________________________________________________________

---

