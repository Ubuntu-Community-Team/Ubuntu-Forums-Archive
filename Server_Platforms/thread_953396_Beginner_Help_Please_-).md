---
title: "Beginner Help Please :-)"
date: 2008-10-20
forum: Server Platforms
---

### Post by duncanpeck on 2008-10-20
Just installed ubuntu server.

I am using a Intel pro/wireless 3945abg network card and was wondering what commands to use and how to set it up to access the internet though the router? The router automatically assigns an ip address. I am planning on setting up a webserver using DynDNS so what I can still use my dynamic IP assigned by my ISP but have the advantages of a static interent IP address.

Any help would be greatly appreciated.

---

### Post by mtl3414 on 2008-10-20
You can set network settings in "/etc/network/interfaces"

then just need restartwith that "/etc/init.d/networking restart"

---

### Post by OffAxis on 2008-10-20
and don't forget to forward the port 80 traffic on the router to your server.

---

### Post by Dr Small on 2008-10-20
Depending on what you plan to do with the server, you will probably want to setup a OpenSSH Server along with Apache, Php, MySQL, PhpMyAdmin.

All of your network configurations can be found in:
```
/etc/network/interfaces
```

Then when you are done, you can start networking:
```
sudo /etc/init.d/networking start
```

If you are behind a router/firewall, then it is probably just best to leave all the firewall rules empty unless you plan to setup DenyHosts to block unauthorized access to your server. Then just forward the respected ports in your router so it can be accessed from outside of your LAN.

Dr Small

---

