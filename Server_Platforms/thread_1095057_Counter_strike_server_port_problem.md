---
title: "Counter strike server port problem"
date: 2009-03-13
forum: Server Platforms
---

### Post by planks on 2009-03-13
I have an Ubuntu 8.04 installation on a computer conected to the internet through a router . I make dmz for the ubuntu computer ip, but this website : [https://www.grc.com/x/portprobe=27015](https://www.grc.com/x/portprobe=27015) shows me that port 27015 is closed . I tried to uninstall iptables, but it was the same result . Has ubuntu another firewall except iptables ??? or how can I open the 27015 port .
I have an apache server on the same computer and the apache server is working fine for everybody, not only for my lan .

---

### Post by askreet on 2009-03-17
Please post the output of the following:

sudo netstat -anp|grep LISTEN

sudo iptables -L

---

### Post by rEnEeK on 2009-06-23
Hello, I have this problem too... Can anybody help me? This is my console:

```
root@78:/home/csserver# sudo netstat -anp|grep LISTEN
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN      4500/mysqld
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4808/apache2
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      4808/apache2
tcp6       0      0 :::21                   :::*                    LISTEN      4757/proftpd: (acce
tcp6       0      0 :::22                   :::*                    LISTEN      5020/sshd
unix  2      [ ACC ]     STREAM     LISTENING     13534    4740/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     12824    4596/hald           @/var/run/hald/dbus-pU3hxSTJtV
unix  2      [ ACC ]     STREAM     LISTENING     12655    4500/mysqld         /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     13482    4727/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     12518    4371/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     12840    4596/hald           @/var/run/hald/dbus-pa8cYWOM32
root@78:/home/csserver# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:27015
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www
ACCEPT     udp  --  anywhere             anywhere            udp dpt:27015
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request
ACCEPT     udp  --  anywhere             anywhere            udp dpt:27015
ACCEPT     udp  --  anywhere             anywhere            udp dpt:27015

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@78:/home/csserver#
```

---

### Post by Kareeser on 2009-06-24
I would assume that the DMZ isn't functioning properly, although this is just a WAG.

Is there a particular reason you cannot forward port 27015 manually to the server in question?

---

### Post by askreet on 2009-06-24
> **rEnEeK said:**
> Hello, I have this problem too... Can anybody help me? This is my console:


According to that output, the server is not listening on port 27015.  I don't recall if UDP ports would be displayed as listening, can you pastebin ([http://pastebin.ca](http://pastebin.ca)) the full output of 'sudo netstat -anp'?

Also, your firewall is mucked up with useless rules.  The default action is accept so adding additional accepts really isn't necessary.

HTH,
Askreet

---

