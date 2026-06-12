---
title: "Managing daemons"
date: 2008-08-16
forum: System76 Support
---

### Post by andrewdied on 2008-08-16
How do you manage daemons in ubuntu?  For example, I installed postgresql, but I don't want it to start at boot.  Administration > Services only lists a few of the daemons.

---

### Post by thomasaaron on 2008-08-18
Look in System > Preferences > Sessions > Startup Programs.
Is it in there?

---

### Post by andrewdied on 2008-08-18
> **thomasaaron said:**
> Look in System > Preferences > Sessions > Startup Programs.
Is it in there?

No, it's not those.  I'm looking for more service type daemons, like postfix or postgresql.  In SuSE you'd use YaST to manage whether or not daemons start up, or in Red Hat there's a fancy script you can use after you edit the headers of the /etc/init.d/ startup scripts.

For example, I want postgresql or mysql installed, but I don't want it running all the time.  How do I make it not start automatically?

---

### Post by pauper on 2008-08-18
If you're talking about /etc/init.d entries, you can install "sysv-rc-conf"
and disable them there. Then, when the need arises, you would run something
like "sudo /etc/init.d/mysql start".

---

### Post by andrewdied on 2008-08-18
> **pauper said:**
> If you're talking about /etc/init.d entries, you can install "sysv-rc-config"
and disable them there. Then, when the need arises, you would run something
like "sudo /etc/init.d/mysql start".

```
~$ sudo apt-get sysv-rc-config
[sudo] password for andrew: 
E: Invalid operation sysv-rc-config
```

sysv-rc-config isn't in apt-get or the package manager.  Do you have any idea what package it's part of?  Ubuntu usually has an app for everything, I just can't figure out what this one is.

---

### Post by pauper on 2008-08-18
```
sudo apt-get [highlight]install[/highlight] sysv-rc-conf
```

Try any mirror (hardy):
[http://packages.ubuntu.com/hardy/all/sysv-rc-conf/download](http://packages.ubuntu.com/hardy/all/sysv-rc-conf/download)

---

### Post by andrewdied on 2008-08-18
> **pauper said:**
> ```
sudo apt-get [highlight]install[/highlight] sysv-rc-conf
```

Try any mirror (hardy):
[http://packages.ubuntu.com/hardy/all/sysv-rc-conf/download](http://packages.ubuntu.com/hardy/all/sysv-rc-conf/download)

Ah, right.  I found it as sysv-rc-conf.  I'm surprised -- I hadn't expected an ncurses-type app for this.  Everything else in ubuntu is so GUI-y.  Thanks for the help.

---

### Post by pauper on 2008-08-18
Oops, my apologies for the typo. Will correct it.

---

### Post by davedicius on 2011-03-06
Hi.
Well FYI and the general information, the app is now called: sysv-rc-conf
and you can install it by typing:
[INDENT]**sudo apt-get install sysv-rc-conf**[/INDENT]
In a standard ubuntu distro (10.10 latest)

---

