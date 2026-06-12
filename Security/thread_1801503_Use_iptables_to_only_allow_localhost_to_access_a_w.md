---
title: "Use iptables to only allow localhost to access a webserver"
date: 2011-07-10
forum: Security
---

### Post by leegold on 2011-07-10
Hi,

I have a web server installed on my Xubuntu 11.04 desktop. I use it for testing and learning. If I'm at a cafe I don't want anyone interacting with the server - which I assume they could when they know my ip.

Would this command only allow me to use the server on my laptop and prevent anyone else?

$ sudo iptables -A INPUT -s  ! 127.0.0.1 -p http -j DROP

Thanks,

Lee G.

---

### Post by todort on 2011-07-11
Please check:

[http://oktopot.net/blog/2011/05/firewall-for-linux-developers/](http://oktopot.net/blog/2011/05/firewall-for-linux-developers/)

---

### Post by Lars Noodén on 2011-07-11
Also you may want to use the target [REJECT](http://www.chiark.greenend.org.uk/~peterb/network/drop-vs-reject) instead of DROP.  That will make diagnosis easier.

---

### Post by SeijiSensei on 2011-07-11
Why don't you just bind the server to localhost?  In Apache, it would be a Listen directive:

```
Listen 127.0.0.1:80
```

and similarly for NameVirtualHosts

```
NameVirtualHosts 127.0.0.1:80
```

You'll need to use

```
<VirtualHost 127.0.0.1:80>
```

in the vhost definitions rather than "*:80".

---

### Post by CharlesA on 2011-07-11
+1 to binding apache to localhost.

You could also firewall it, but if it's not listening for connections on the external interface, there would be no need to firewall it.

---

