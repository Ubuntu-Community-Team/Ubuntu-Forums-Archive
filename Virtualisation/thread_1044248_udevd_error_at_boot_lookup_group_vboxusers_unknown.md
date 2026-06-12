---
title: "udevd error at boot: lookup_group vboxusers unknown"
date: 2009-01-19
forum: Virtualisation
---

### Post by armandoct on 2009-01-19
Hi all,

in the last week i was not able to resolve this problem:

on my ubuntu hardy i worked for about one year with
virtualbox 2.0.x with various guests and host networking
script to setup the tap interfaces at guest os startup...

recently i updated virtualbox to version 2.1 to enjoy
easier network configuration provided, and my shared
folders between host and guest have stopped working...

Well, i thought, let's revert back to version 2.0... but...
right after removing 2.1 and reinstalling 2.0.x this message 
appeared at boot time: 

```

udevd[####]: lookup_group: secified group 'vboxusers' unknown


```

this is my config:

the output of my **uname -a** is:
```

Linux pc-name 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux

```

the results for the command  **grep -ln vbox /etc/udev/rules.d/*** are:
```
/etc/udev/rules.d/50-virtualbox-ose.rules:1:KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", GROUP="vboxusers", MODE="0660"
/etc/udev/rules.d/60-vboxdrv.rules:1:KERNEL=="vboxdrv", NAME="vboxdrv", OWNER="root", GROUP="vboxusers", MODE="0660"
```

the output of my **sudo groups username** is:
```

username adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin vboxusers tomcat


```
(the vboxusers group exists and my user is in the group)

some ideas on how to solve the problem?

thanks,
Armando.

---

### Post by armandoct on 2009-01-21
I tried to find among the configuration files of udev but I found nothing.

---

### Post by rboliver on 2009-01-25
Hi all,

I'm having the exactly same error...it says it is UDEV error 1333 (if it helps).

I'm running the kernel 2.6.24-21:

Linux xxxxx-laptop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

However, this was not happening while I was using 2.6.24-19...it started when I updated to 21.

Any help?

Rubens

---

### Post by Noo on 2009-01-30
I have the same error at boot after uninstalling virtualbox ose 2.0.4.

---

### Post by Kheops_74 on 2009-03-01
Same here : Linux sang-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

Any news?

---

### Post by Kheops_74 on 2009-04-13
Does anybody knows what is this error? Which file i must update?

Thanks

---

