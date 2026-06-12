---
title: "how to change port 1194"
date: 2009-12-07
forum: Server Platforms
---

### Post by pawan_lal on 2009-12-07
i have configured openvpn on ubuntu 8.04lts  i am using 1194 udp port for openvpn in ubuntu.  in  that machine only i am using squirrellmailmail for postfix and ssh.  when i checked the port results r this

root@server1:~# netstat -plan | grep :80 
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      5878/apache2



root@server1:~# netstat -plan | grep :22
tcp6       0      0 :::22                   :::*                    LISTEN      4860/sshd
tcp6       0     52 192.168.15.2:22         192.168.15.3:2958       ESTABLISHED 6028/sshd: server1


and when i am checking port 1194  

root@server1:~# netstat -plan | grep :1194
root@server1:~#


output is nothing means 1194 is not  working n i think thats why i am not able to connect to openvpn from client side

---

### Post by kerignell on 2009-12-07
Is the server daemon running?

---

