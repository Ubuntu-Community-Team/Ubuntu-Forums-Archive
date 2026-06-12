---
title: "Lubuntu lxappearance core dump"
date: 2015-06-30
forum: Ubuntu Development Version
---

### Post by VMC on 2015-06-30
Trying to activate Appearances triggers a core dump. From command line its '*lxappearance*'. 

Here is one of many bug reports.[ lxappearance package]("https://bugs.launchpad.net/ubuntu/+source/lxappearance/+bug/1468529")

[A side note. Searching failed Plank-doc theme change led me to lxapparence. Hopefully, once Appearances is fixed Plank will be fixed]

---

### Post by ventrical on 2015-07-01
Same here.

```

ventrical@ventrical-MS-7850:~$ inxi -b
System:    Host: ventrical-MS-7850 Kernel: 3.19.0-22-generic x86_64 (64 bit)
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 15.10 wily
Machine:   Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0
           Bios: American Megatrends v: V2.8 date: 07/17/2014
CPU:       Dual core Intel Pentium G3240 (-MCP-) speed/max: 804/3100 MHz
Graphics:  Card: Intel Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
           Display Server: X.Org 1.17.1 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1440x900@59.9hz
           GLX Renderer: Mesa DRI Intel Haswell Desktop
           GLX Version: 3.0 Mesa 10.5.8
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 120.0GB (5.4% used)
Info:      Processes: 144 Uptime: 4 min Memory: 371.2/3814.9MB
           Client: Shell (bash) inxi: 2.2.16 
ventrical@ventrical-MS-7850:~$ 



```

---

### Post by VMC on 2015-07-02
I noticed the bug report has not been assigned to anyone. Is that because its not a Ubuntu package? I wonder where to report the package. I tried searching under lxde.
I'm guessing from [this link]("https://launchpad.net/ubuntu/+source/lxappearance"), that its debian maintained. Tried looking upstream but got a launchpad error. Last update on this package was 2015-05-04.

---

### Post by cariboo on 2015-07-02
From [this]("http://http://forum.lxde.org/viewtopic.php?t=575") forum post, it looks like you need to report bugs here:

[http://sourceforge.net/p/lxde/bugs/](http://sourceforge.net/p/lxde/bugs/)

**Note:** Ublock claims this is a malicious site, so use it at your own risk.

---

### Post by vasa1 on 2015-07-02
> **cariboo said:**
> ...
[http://sourceforge.net/p/lxde/bugs/](http://sourceforge.net/p/lxde/bugs/)

**Note:** Ublock claims this is a malicious site, so use it at your own risk.

> What may be even more troubling for Sourceforge is that uBlock -- and all of its spin-offs and forks -- is now blocking access to the site by default.From [http://www.ghacks.net/2015/06/15/popular-software-projects-leave-sourceforge/](http://www.ghacks.net/2015/06/15/popular-software-projects-leave-sourceforge/)

---

### Post by VMC on 2015-07-02
I have NO idea how to form a ticket over @ SF, but I created one anyway:
[https://sourceforge.net/p/lxde/bugs/764/](https://sourceforge.net/p/lxde/bugs/764/)

Edit: apparently "libobrender 3.6.0-1" is a culprit, and "libobrender 3.6.0-2" will be out soon to fix the issue, according to this [bug report]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=788520"), message#10.

---

### Post by Chanath on 2015-08-06
Just uninstall lxappearance-obconf and you'd get lxappearance working.

---

### Post by syntaxerror74 on 2015-08-10
> **Chanath said:**
> Just uninstall lxappearance-obconf and you'd get lxappearance working.

Well spotted! It's the plugin that causes trouble, see also here
[https://bugs.launchpad.net/ubuntu/+source/lxappearance-obconf/+bug/1469276](https://bugs.launchpad.net/ubuntu/+source/lxappearance-obconf/+bug/1469276)

Upgrading to Openbox 3.6.0 fixed everything, though. (even with the plugin installed)

---

