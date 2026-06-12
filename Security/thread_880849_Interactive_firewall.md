---
title: "Interactive firewall"
date: 2008-08-05
forum: Security
---

### Post by alexv75 on 2008-08-05
This is one of the few things that are preventing me to migrate fully to Linux. I know that Linux is more secure overall, but my Windows mentality haunts me :lol: and i need to ease my mind somehow :p . Is there a firewall that offers analogous or at least close level of interactivity and functionality like Eset Smart Security (example below)?

---

### Post by K2712 on 2008-08-05
Linux comes with a very good firewall called iptables, and there are GUI front-ends to manage it, depending on your desktop environment.

For gnome -> firestarter -->[screenshots]("http://www.fs-security.com/screenshots.php")
For KDE ->  guarddog -->[screenshots]("http://www.simonzone.com/software/guarddog/#screenshots")

There are probably more, but these are the most popular.

---

### Post by alexv75 on 2008-08-07
Thanks, but they aren't nearly as interactive as i would like (i would say they aren't interactive at all)... But i've found something simpler that should do the job well enough at least for now - [http://gufw.tuxfamily.org/screenshots.html](http://gufw.tuxfamily.org/screenshots.html) (i know that UFW is part of Ubuntu for a long time now, but i personally prefer GUIs over console :d )

---

### Post by Shazaam on 2008-08-07
AFAIK there are very FEW programs in linux that "phone home" so if you don't have any servers running all you need to do is look at the inbound side of iptables. UFW and others (Firestarter, Guarddog etc) allow you to configure that very nicely.

---

### Post by bodhi.zazen on 2008-08-07
There are several issues.

In linux apps are much more modular. One is a firewall, another configures the firewall, a third monitors network traffic.

Also you should learn ufw:

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

GUI : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

gufw is a gui front ent. I have not used it.

For monitoring network traffic you have everything from snort to wireshark.

Also you need to re-adjust to Linux Security :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

