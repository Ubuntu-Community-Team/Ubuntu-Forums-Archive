---
title: "Can't reach port on 10.04 64bits"
date: 2011-01-11
forum: Server Platforms
---

### Post by biglele on 2011-01-11
I have ubuntu Linux xxxx 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64   /   GNU/Linux   /   Ubuntu 10.04 LTS installed on two identical hardware machines. SSH server work, ping work, oracle11g server works, but on one of mi servers one port of a application that develp here can be reach, the port is 2809 (corba).

If i do telnet xxx 2809 on the machine, port is responding, but if i do the same in any machine in LAN, dont respond. This only happend on one server!!! the other just work fine :(

I have all firewall disabled!!

```
root@xxx:~#  iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

```
root@xxx:~# ufw status
Status: inactive
```

Any idea?
Thanks in advance

---

### Post by HugoSerrano on 2011-01-11
In local machine you do:
 telnet localhost 2809
or
telnet Private.Lan.IP.Address 2809
?

---

### Post by biglele on 2011-01-11
> **HugoSerrano said:**
> In local machine you do:
 telnet localhost 2809
or
telnet Private.Lan.IP.Address 2809
?

Yes, i do not use localhost because aplication is on virtual eth.


```
root@xxx:~# telnet app10 2809
Trying x.x.x.140...
Connected to app10.x.x.com.
Escape character is '^]'.

^C^C^CConnection closed by foreign host.
root@xxx:~#
```


but on same lan on windows

```
U:\>telnet app10 2809
Conectándose a app10...No se puede abrir la conexión al host, en puerto 2809: Error en la conexión

U:\>
```

---

### Post by HugoSerrano on 2011-01-11
Try:
telnet x.x.x.140 2809 
from other lan machine.

Do:
netstat -natup 
and show us the output

---

### Post by biglele on 2011-01-11
> **HugoSerrano said:**
> Try:
telnet x.x.x.140 2809 
from other lan machine.

Do:
netstat -natup 
and show us the output

telnet IP port

```
U:\>telnet x.x.x.140 2809
Conectándose a x.x.x.140...No se puede abrir la conexión al host, en puerto 2809: Error en la conexión

U:\>
```


Heres the result
x.x.x.25 is eth0
x.x.x.140 is eth0:1
x.x.x.199 is mi PC ssh connection

```
root@xxx:~# netstat -natup
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:16748           0.0.0.0:*               LISTEN      7533/4dl-container.
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1378/sshd
tcp        0      0 x.x.x.140:2809      0.0.0.0:*               LISTEN      7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:2809      x.x.x.199:2528      SYN_RECV    -
tcp        0      0 127.0.0.1:6010          0.0.0.0:*               LISTEN      2264/0
tcp        0      0 127.0.0.1:6011          0.0.0.0:*               LISTEN      2272/1
tcp        0      0 x.x.x.140:4000      0.0.0.0:*               LISTEN      7489/Naming_Service
tcp        0      0 x.x.x.140:4002      0.0.0.0:*               LISTEN      7490/Notify_Service
tcp        0      0 0.0.0.0:3938            0.0.0.0:*               LISTEN      2741/emagent
tcp        0      0 x.x.x.140:4003      0.0.0.0:*               LISTEN      7533/4dl-container.
tcp        0      0 x.x.x.140:5000      0.0.0.0:*               LISTEN      7477/app10.bin
tcp        0      0 x.x.x.140:5001      0.0.0.0:*               LISTEN      7478/LoadManager
tcp        0      0 127.0.1.1:43594         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 127.0.1.1:43591         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 127.0.1.1:43595         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:5000      x.x.x.140:31393     ESTABLISHED 7477/app10.bin
tcp        0      0 x.x.x.140:24665     x.x.x.140:2809      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:15438     x.x.x.140:4003      ESTABLISHED 7478/LoadManager
tcp        0      0 127.0.1.1:43588         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:4003      x.x.x.140:15438     ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:28461     x.x.x.140:4002      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:4002      x.x.x.140:28461     ESTABLISHED 7490/Notify_Service
tcp        0      0 127.0.1.1:63600         127.0.1.1:1521          ESTABLISHED 3205/ora_pmon_xxxx
tcp        0      0 x.x.x.140:2809      x.x.x.140:29801     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:2809      x.x.x.140:24665     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.25:22         x.x.x.199:4510      ESTABLISHED 2194/sshd: yyyyy
tcp        0      0 127.0.1.1:43590         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:45262     x.x.x.140:2809      ESTABLISHED 7478/LoadManager
tcp        0      0 x.x.x.140:2809      x.x.x.140:22308     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:5000      x.x.x.140:31367     ESTABLISHED 7477/app10.bin
tcp        0      0 x.x.x.140:2809      x.x.x.140:58737     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:4000      x.x.x.140:20847     ESTABLISHED 7489/Naming_Service
tcp        0      0 x.x.x.140:2809      x.x.x.140:41262     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:25747     x.x.x.140:4000      ESTABLISHED 7490/Notify_Service
tcp        0      0 x.x.x.140:17274     x.x.x.140:2809      ESTABLISHED 7477/app10.bin
tcp        0      0 127.0.1.1:43587         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:4002      x.x.x.140:35682     ESTABLISHED 7490/Notify_Service
tcp        0      0 x.x.x.140:41262     x.x.x.140:2809      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:44180     x.x.x.140:5001      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:4000      x.x.x.140:25747     ESTABLISHED 7489/Naming_Service
tcp        0      0 x.x.x.140:5000      x.x.x.140:31399     ESTABLISHED 7477/app10.bin
tcp        0      0 x.x.x.140:4003      x.x.x.140:55062     ESTABLISHED 7533/4dl-container.
tcp        0      0 127.0.1.1:43586         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:4002      x.x.x.140:35698     ESTABLISHED 7490/Notify_Service
tcp        0      0 x.x.x.140:5001      x.x.x.140:44180     ESTABLISHED 7478/LoadManager
tcp        0      0 127.0.1.1:63662         127.0.1.1:1521          ESTABLISHED 2741/emagent
tcp        0      0 127.0.1.1:43589         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:11873     x.x.x.140:2809      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:4000      x.x.x.140:34750     ESTABLISHED 7489/Naming_Service
tcp        0      0 x.x.x.140:2809      x.x.x.140:50383     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:5000      x.x.x.140:18990     ESTABLISHED 7477/app10.bin
tcp        0      0 x.x.x.140:4003      x.x.x.140:57424     ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:55062     x.x.x.140:4003      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:2809      x.x.x.140:11873     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:2809      x.x.x.140:52793     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:29801     x.x.x.140:2809      ESTABLISHED 7489/Naming_Service
tcp        0      0 127.0.1.1:63723         127.0.1.1:1521          ESTABLISHED 2741/emagent
tcp        0      0 x.x.x.140:18990     x.x.x.140:5000      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:4003      x.x.x.140:57417     ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:2809      x.x.x.199:1424      ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.25:22         x.x.x.199:4511      ESTABLISHED 2272/1
tcp        0      0 x.x.x.140:55047     x.x.x.140:4711      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:50383     x.x.x.140:2809      ESTABLISHED 7477/app10.bin
tcp        0      0 x.x.x.140:4002      x.x.x.140:35700     ESTABLISHED 7490/Notify_Service
tcp        0      0 x.x.x.140:4000      x.x.x.140:34710     ESTABLISHED 7489/Naming_Service
tcp        0      0 x.x.x.140:2809      x.x.x.140:45262     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 127.0.1.1:43593         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:5000      x.x.x.140:55719     ESTABLISHED 7477/app10.bin
tcp        0      0 127.0.1.1:63789         127.0.1.1:1521          ESTABLISHED 2741/emagent
tcp        0      0 x.x.x.140:4000      x.x.x.140:34758     ESTABLISHED 7489/Naming_Service
tcp        0      0 x.x.x.140:55719     x.x.x.140:5000      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:2809      x.x.x.140:17274     ESTABLISHED 7487/ImplRepo_Servi
tcp        0      0 x.x.x.140:4003      x.x.x.140:57407     ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:52793     x.x.x.140:2809      ESTABLISHED 7490/Notify_Service
tcp        0      0 x.x.x.140:12203     x.x.x.140:4712      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:20847     x.x.x.140:4000      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:22308     x.x.x.140:2809      ESTABLISHED 7489/Naming_Service
tcp        0      0 x.x.x.140:9661      x.x.x.140:4713      ESTABLISHED 7533/4dl-container.
tcp        0      0 x.x.x.140:58737     x.x.x.140:2809      ESTABLISHED 7490/Notify_Service
tcp        0      0 127.0.1.1:43592         127.0.1.1:1521          ESTABLISHED 7533/4dl-container.
tcp6       0      0 :::5520                 :::*                    LISTEN      2711/java
tcp6       0      0 :::1521                 :::*                    LISTEN      3072/tnslsnr
tcp6       0      0 :::63826                :::*                    LISTEN      3239/ora_d000_xxxx
tcp6       0      0 :::22                   :::*                    LISTEN      1378/sshd
tcp6       0      0 ::1:6010                :::*                    LISTEN      2264/0
tcp6       0      0 ::1:6011                :::*                    LISTEN      2272/1
tcp6       0      0 :::1158                 :::*                    LISTEN      2711/java
tcp6       0      0 x.x.x.140:4711      :::*                    LISTEN      7757/java
tcp6       0      0 :::8040                 :::*                    LISTEN      7757/java
tcp6       0      0 x.x.x.140:4712      :::*                    LISTEN      7497/java
tcp6       0      0 x.x.x.140:4713      :::*                    LISTEN      7758/java
tcp6       0      0 127.0.1.1:63642         127.0.1.1:1521          ESTABLISHED 2711/java
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43591         ESTABLISHED 7596/oraclexxx11
tcp6       0      0 x.x.x.140:47609     x.x.x.140:2809      TIME_WAIT   -
tcp6       0      0 x.x.x.140:4712      x.x.x.140:37209     ESTABLISHED 7497/java
tcp6       0      0 x.x.x.25:1521       x.x.x.25:44017      ESTABLISHED 8021/oraclexxx11
tcp6       0      0 x.x.x.140:35698     x.x.x.140:4002      ESTABLISHED 7758/java
tcp6       0      0 x.x.x.140:57417     x.x.x.140:4003      ESTABLISHED 7758/java
tcp6       0      0 x.x.x.25:1521       x.x.x.25:14421      ESTABLISHED 7997/oraclexxx11
tcp6       0      0 127.0.1.1:63646         127.0.1.1:1521          ESTABLISHED 2711/java
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63662         ESTABLISHED 3475/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63643         ESTABLISHED 3398/oraclexxx11
tcp6       0      0 x.x.x.25:1521       x.x.x.25:51336      ESTABLISHED 8023/oraclexxx11
tcp6       0      0 x.x.x.140:31393     x.x.x.140:5000      ESTABLISHED 7758/java
tcp6       0      0 127.0.1.1:63643         127.0.1.1:1521          ESTABLISHED 2711/java
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63600         ESTABLISHED 3072/tnslsnr
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63646         ESTABLISHED 3404/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:55006         TIME_WAIT   -
tcp6       0      0 x.x.x.140:57424     x.x.x.140:4003      ESTABLISHED 7757/java
tcp6       0      0 x.x.x.25:14421      x.x.x.25:1521       ESTABLISHED 7758/java
tcp6       0      0 x.x.x.140:35682     x.x.x.140:4002      ESTABLISHED 7497/java
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63642         ESTABLISHED 3396/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43586         ESTABLISHED 7586/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43592         ESTABLISHED 7598/oraclexxx11
tcp6       0      0 x.x.x.140:37209     x.x.x.140:4712      ESTABLISHED 7757/java
tcp6       0      0 x.x.x.25:47795      x.x.x.25:1521       ESTABLISHED 7758/java
tcp6       0      0 x.x.x.140:4713      x.x.x.140:9661      ESTABLISHED 7758/java
tcp6       0      0 x.x.x.25:44017      x.x.x.25:1521       ESTABLISHED 7758/java
tcp6       0      0 x.x.x.25:1521       x.x.x.25:47795      ESTABLISHED 7982/oraclexxx11
tcp6       0      0 x.x.x.25:1521       x.x.x.25:17850      ESTABLISHED 8019/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43590         ESTABLISHED 7594/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43594         ESTABLISHED 7602/oraclexxx11
tcp6       0      0 x.x.x.140:4712      x.x.x.140:12203     ESTABLISHED 7497/java
tcp6       0      0 x.x.x.25:51829      x.x.x.52:389        ESTABLISHED 7497/java
tcp6       0      0 x.x.x.140:57407     x.x.x.140:4003      ESTABLISHED 7497/java
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43587         ESTABLISHED 7588/oraclexxx11
tcp6       0      0 x.x.x.140:4711      x.x.x.140:55047     ESTABLISHED 7757/java
tcp6       0      0 127.0.1.1:63644         127.0.1.1:1521          ESTABLISHED 2711/java
tcp6       0      0 x.x.x.25:51336      x.x.x.25:1521       ESTABLISHED 7758/java
tcp6       0      0 127.0.1.1:63645         127.0.1.1:1521          ESTABLISHED 2711/java
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63789         ESTABLISHED 4904/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63645         ESTABLISHED 3402/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43595         ESTABLISHED 7604/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63723         ESTABLISHED 4331/oraclexxx11
tcp6       0      0 x.x.x.140:31367     x.x.x.140:5000      ESTABLISHED 7497/java
tcp6       0      0 127.0.1.1:1521          127.0.1.1:55008         TIME_WAIT   -
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43588         ESTABLISHED 7590/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43589         ESTABLISHED 7592/oraclexxx11
tcp6       0      0 x.x.x.25:17850      x.x.x.25:1521       ESTABLISHED 7758/java
tcp6       0      0 x.x.x.140:34750     x.x.x.140:4000      ESTABLISHED 7757/java
tcp6       0      0 x.x.x.140:34710     x.x.x.140:4000      ESTABLISHED 7497/java
tcp6       0      0 x.x.x.140:34758     x.x.x.140:4000      ESTABLISHED 7758/java
tcp6       0      0 127.0.1.1:1521          127.0.1.1:63644         ESTABLISHED 3400/oraclexxx11
tcp6       0      0 127.0.1.1:1521          127.0.1.1:43593         ESTABLISHED 7600/oraclexxx11
tcp6       0      0 x.x.x.140:35700     x.x.x.140:4002      ESTABLISHED 7757/java
tcp6       0      0 x.x.x.140:31399     x.x.x.140:5000      ESTABLISHED 7757/java
udp6       0      0 :::44367                :::*                                3235/ora_mmon_xxxx
udp6       0      0 ::1:39643               :::*                                3241/ora_s000_xxxx
udp6       0      0 ::1:22287               :::*                                3239/ora_d000_xxxx
udp6       0      0 ::1:38957               :::*                                3205/ora_pmon_xxxx


```

---

### Post by biglele on 2011-01-11
Problem solved... someone config another server with that IP whitout inform... some packets reach right server... some packets dont!
That's embarrasing, i know!!!!
thanks HugoSerrano for help!

---

