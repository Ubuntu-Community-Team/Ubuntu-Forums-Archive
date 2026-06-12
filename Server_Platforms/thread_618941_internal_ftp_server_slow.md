---
title: "internal ftp server slow"
date: 2007-11-20
forum: Server Platforms
---

### Post by mouseboyx on 2007-11-20
I have a proftpd server running on
192.168.2.5
and the client is
192.168.2.4

I have changed config files to allow unlimited up and down speeds and a traceroute  from client to server and server to client is direct.

The speed of my network is 100mbp/s but it is uploading/downloading at
.05

---

### Post by netlogic on 2007-11-21
check your iptables in case you have limited your bandwidth. also, some ftp servers have bandwidth caps. it might be turned on. also, run your favorite sniffer to find out if you are having packet loss.

this is a link to proftpd's bandwidth limiting.
[http://www.proftpd.org/localsite/Userguide/linked/x950.html](http://www.proftpd.org/localsite/Userguide/linked/x950.html)

---

### Post by mouseboyx on 2007-11-23
Thanks I will try it as soon as i get home.

---

