---
title: "boot commands"
date: 2004-12-03
forum: The Cafe
---

### Post by mikeymike on 2004-12-03
Hi, 
I recently installed ubuntu, i still use FC3 but was wondering is there a script like 
"rc.local" in debain based/ubuntu so i can run some commands at start up and if so what would the syntax be for it the same as rc.local or different.

Thanks, 
Mike

---

### Post by diebels on 2004-12-03
use /etc/init.d/bootmisc.sh , or make your own
```
cd /etc/init.d/
sudo touch rc.local
sudo chmod +x rc.local
sudo ln -s rc.local ../rcS.d/80rc.local
```

---

### Post by mikeymike on 2004-12-03
[QUOTE=diebels]use /etc/init.d/bootmisc.sh , or make your own
```
cd /etc/init.d/
sudo touch rc.local
sudo chmod +x rc.local
sudo ln -s rc.local ../rcS.d/80rc.local
```[/QUOTE]

thanks :)

---

### Post by p!=f on 2004-12-03
Smoother way is to create **/etc/rc.boot** directory and place the scripts you want to startup on boot here.

---

### Post by offby1 on 2004-12-26
Is that all it takes?  By default anything in rc.boot will run on startup?

---

### Post by gstrock on 2006-01-16
any idea at what point in the boot up procedure
they get executed?  Is it after all the init.d scripts
get executed?

---

### Post by art2003 on 2006-01-20
[http://www.debian.org/doc/FAQ/ch-customizing.en.html](http://www.debian.org/doc/FAQ/ch-customizing.en.html)

Like all Unices, Ubuntu boots up by executing the program init. The configuration file for init (which is /etc/inittab) specifies that the **first script to be executed should be /etc/init.d/rcS**. This script runs **all of the scripts in /etc/rcS.d/** by sourcing or forking subprocess depending on their file extension to perform initialization such as to check and to mount file systems, to load modules, to start the network services, to set the clock, and to perform other initialization.[B] Then, for compatibility, it runs the files in /etc/rc.boot/ too. 
[/B]
After completing the boot process, init executes all start scripts in a directory specified by the default runlevel (this runlevel is given by the entry for id in /etc/inittab). Like most System V compatible Unices, Linux has 7 runlevels:

---

