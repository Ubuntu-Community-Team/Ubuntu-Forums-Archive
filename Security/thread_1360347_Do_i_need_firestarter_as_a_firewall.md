---
title: "Do i need firestarter as a firewall"
date: 2009-12-20
forum: Security
---

### Post by hatewindows on 2009-12-20
Or does ubuntu 9.10 have its own built in firewall?

---

### Post by teward on 2009-12-20
Firestarter is just a GUI frontend to manipulate the iptables, ubuntu's built in network filter protocols.

iptables comes with the system, however I use Firestarter to help facilitate messing with the iptables (as I'm not one who prefers to screw with iptables via the terminal).

there IS ufw, and gufw is the GUI frontend you can install for it, however you need some knowledge of the command line to manipulate it.


Firestarter messes with the iptables, and it seems to block anything that needs blocking; it also works well for specifying what internet traffic to allow, etc.

---

### Post by hatewindows on 2009-12-20
Thanks for the info!!

---

### Post by lovinglinux on 2009-12-20
> **TrekCaptainUSA said:**
> there IS ufw, and gufw is the GUI frontend you can install for it, however you need some knowledge of the command line to manipulate it.

You don't need any command-line knowledge to use gufw. In fact, it is the recommended firewall manager these days.

---

### Post by bodhi.zazen on 2009-12-20
[quote=TrekCaptainUSA;8533684there IS ufw, and gufw is the GUI frontend you can install for it, however you need some knowledge of the command line to manipulate it.[/quote]

That is only partially true. GUFW is a graphical tool and does not require use of the command line.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

---

### Post by teward on 2009-12-21
> **bodhi.zazen said:**
> That is only partially true. GUFW is a graphical tool and does not require use of the command line.

[http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)

i'm a bit tired, and wrote the sentence weirdly.  my fault.

---

