---
title: "network is unreachable"
date: 2009-05-01
forum: Server Platforms
---

### Post by NewbuntuUser777 on 2009-05-01
Hi,

I just setup a router and an ubuntu server.  I connected my ubuntu desktop and everything is groovy.  The server no luck.  Says network is unreachable when I try to ping stuff.  Don't know what to do now.

---

### Post by doas777 on 2009-05-01
> **NewbuntuUser777 said:**
> Hi,

I just setup a router and an ubuntu server.  I connected my ubuntu desktop and everything is groovy.  The server no luck.  Says network is unreachable when I try to ping stuff.  Don't know what to do now.

whats the output of:
```
ifconfig

route
```

---

### Post by NewbuntuUser777 on 2009-05-01
Found another thread that said to try:


brute-force an IP address via:
ifconfig eth0 inet 192.168.etc...

Then do:
sudo dhclient eth0


Now I can ping, but I have no idea what I just did!

Can anyone explain this magic?

---

### Post by NewbuntuUser777 on 2009-05-01
okay and after rebooting, I'm back to the same place.  
No connection...

ifconfig is 

lo  link encapL: local loopback
inet addr: 127.0.0.1 mask 255.0.0.0
inet6 addr: ::1/128 scope: host
up loopback running mtu: 16436 metric:1
rxpackets 0 ...
then more 0 for rest 
rx bytes: 0 etc....

---

### Post by doas777 on 2009-05-01
is eth0 listed in your /etc/network/interfaces file?
if not try adding
```
auto eth0 inet
```and after you save, restart networking with:```
sudo /etc/init.d/networking restart
```

what does ifconfig show now? does it notice eth0?

---

### Post by NewbuntuUser777 on 2009-05-01
Did that but it said after restarting...
ignoring unkown interface eth0=eth0
ignoring unknown interface inet=inet

---

### Post by doas777 on 2009-05-01
drop the "inet" part, and try again

---

### Post by NewbuntuUser777 on 2009-05-01
ignoring unkown interface eth0=eth0

---

### Post by doas777 on 2009-05-01
> **NewbuntuUser777 said:**
> ignoring unkown interface eth0=eth0hmmm. check out this page on manually configuring your interfaces file.

 
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by NewbuntuUser777 on 2009-05-01
Brilliance my friend!

You had it part right:

auto eth0
iface eth0 inet dhcp

Solved it.

Thanks thanks thanks!

---

