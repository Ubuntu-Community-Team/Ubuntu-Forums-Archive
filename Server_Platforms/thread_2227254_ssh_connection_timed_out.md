---
title: "ssh connection timed out"
date: 2014-05-31
forum: Server Platforms
---

### Post by dusan3 on 2014-05-31
Hi guys,

I have installed Ubuntu Desktop 14.04 and i having a problem with ssh....When i ping ip that i wanna do ssh its ok,i'm getting response but when i try ssh@ipserver i'm getting connection timed out.I already tried this on ubuntu server and everything did well but on desktop now i have problem.
Can someone help me.

Thanks.

---

### Post by deadflowr on 2014-05-31
It's unclear, so I'll ask. 
Did you install the ssh server on the desktop?

---

### Post by dusan3 on 2014-05-31
yes ...i install openssh-server and allow port 22 on ufw firewall and also port forwarded port 22 on my router....

---

### Post by dusan3 on 2014-06-01
Can somebody help me with this?I'm still having a problem.I can access locally on ip address(192.168.1.23) but when i try on external ip (109.93.72.102) i'm getting connection timed out and dont know whats the problem.

Thanks.

---

### Post by steeldriver on 2014-06-01
Are you trying the external IP from inside your LAN? if so, it may just be that your router doesn't support that (NAT loopback / hairpinning)

---

### Post by dusan3 on 2014-06-01
I already try this with ubuntu server and this was successfull but on Desktop version i'm having a problem....I want to access my server at home from computer at work.This was successfull on Ubuntu Server 14.04.

---

### Post by dusan3 on 2014-06-01
this is output of netstat -tulpn:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      9032/mysqld     
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1022/vsftpd     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      4518/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      2407/cupsd      
tcp6       0      0 :::80                   :::*                    LISTEN      14179/apache2   
tcp6       0      0 :::22                   :::*                    LISTEN      4518/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      2407/cupsd      
udp        0      0 0.0.0.0:58973           0.0.0.0:*                           719/avahi-daemon: r
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1080/cups-browsed
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           719/avahi-daemon: r
udp6       0      0 :::5353                 :::*                                719/avahi-daemon: r
udp6       0      0 :::54557                :::*                                719/avahi-daemon: r
```

and this is output of ufw status:
```
80                         ALLOW       Anywhere
22                         ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
80 (v6)                    ALLOW       Anywhere (v6)
22 (v6)                    ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
```

is something wrong with this?

---

### Post by dusan3 on 2014-06-01
Can someone help me with this?

---

### Post by Hugo_Serrano on 2014-06-01
Hello!

If you can access it on local network, the problem it's on your router.
Have you configured the port forwarding?

Hugo.

---

### Post by sweekly44 on 2014-06-02
Also, if you have enabled port-forwarding on your router it's also a good idea to set a static ip for your server, so it will always be the same.

---

