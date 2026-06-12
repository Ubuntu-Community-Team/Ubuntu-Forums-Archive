---
title: "modifying the ubuntu firewall"
date: 2010-01-12
forum: Security
---

### Post by 26venger on 2010-01-12
how do i modify the ubuntu firewall to let in certain ip addresses but lock others out
any help would be great

---

### Post by Jive Turkey on 2010-01-12
in a terminal type "man ufw" read that, come back with any questions.  There is a corresponding GUI application for it you can install called "gufw."  The terminal version has more options though.

the way too simple answer that might not help is:
A)```
sudo ufw allow from x.x.x.x port x to x.x.x.x port x
```
B)```
 sudo ufw deny from x.x.x.x port x to x.x.x.x port x
```

---

### Post by adam814 on 2010-01-12
Do you really need to allow *any* traffic from that one IP?  Maybe you just need to open one port for it.

I'd do this:
```
sudo ufw allow from <ip address> to any port <port>
```

---

### Post by Jive Turkey on 2010-01-12
So, after reading the man page, what it sounds like you want to do is set the default to "deny" except for a few IP addresses, is that right?

---

### Post by bodhi.zazen on 2010-01-13
> **26venger said:**
> how do i modify the ubuntu firewall to let in certain ip addresses but lock others out
any help would be great

The firewall is iptables which is a front end for netfilter.

It can be configured directly on the command line or with any number of tools.

UFW is the default for ubuntu, UFW is a command line tool. Gufw is a graphical front end for UFW.

See these blog enteries :

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

[http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

And for iptables:

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by Rob_H on 2010-01-13
And if you prefer a GUI, install **gufw**.

EDIT: Nevermind, I missed Bodhi's comment saying the same thing.

---

### Post by 26venger on 2010-02-15
thanks for the help

---

