---
title: "If you have no working wired ethernet with kernel 3.8 &amp; 3.9..."
date: 2013-03-15
forum: Ubuntu Development Version
---

### Post by 3vi1 on 2013-03-15
If you've had sporadic (or constant) issues with your wired Ethernet in Raring, check out the following bug and see if it applies to you:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652")

If it does, please mark it as affecting you.  I'm surprised that not more that two people other than myself have reported problems under Raring (as it appears to affect a couple of different Intel chips), and it worries me that this might not be fixed before 13.04 lands.

---

### Post by ft_ on 2013-03-15
And the good news are :
> Konstantin Khlebnikov (1):
      e1000e: fix pci-device enable-counter balance
from :
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.3-raring/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.3-raring/CHANGES)

As the author of the bug report ;) I wish this fix to fix this mess.
I'll try 3.8.3 as soon as possible, maybe through 3.8.0-13 Ubuntu kernel.

---

### Post by ft_ on 2013-03-16
Same issue with 3.8.0-13 Ubuntu kernel. Must be a power management issue. If you look at the "control" file when AC is plugged, it is set on "on" instead of "auto".

---

### Post by ft_ on 2013-03-16
we have to wait some 3.9 backports, and this time imho it will be fixed :
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/CHANGES)
> Konstantin Khlebnikov (3):
      e1000e: fix pci-device enable-counter balance
      e1000e: fix runtime power management transitions
      e1000e: fix accessing to suspended device

---

### Post by ft_ on 2013-04-09
solved for newer 3.9 kernel, but Raring needs backport :

> We *maybe* (i'm not a kernel expert) need some backports from :

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc3-raring/CHANGES](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-rc3-raring/CHANGES)

more precisely :

Konstantin Khlebnikov (3):
      e1000e: fix pci-device enable-counter balance <-------- already backported
      e1000e: fix runtime power management transitions
      e1000e: fix accessing to suspended device

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1112652)

---

### Post by jjmf on 2013-04-23
I have a similar problem with 3.8.0-19-generic and gnome (raring) ethernet shows its working (most of the time) but connections dies after a few seconds. Booted with 3.5 and it works fine. I wanted to try the [COLOR=#333333][FONT=Ubuntu Mono]/sys/devices/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]pci0000:[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]00/<number of ethernet pci port>/power/control [/FONT][/COLOR]but I don't know how to check the pci port, can you guys help? I'll check and then report on launchpad. Thanks.

---

### Post by ft_ on 2013-04-23
maybe 
**lspci**
?
:mrgreen:

---

### Post by jjmf on 2013-04-23
Oups, I had missed it, ok so I get 

02:00.0 Ethernet controller: Qualcomm Atheros AR8152 v1.1 Fast Ethernet (rev c1)

However I could not find the folder for this device: dir in /sys/devices/pci0000:00/ returns

0000:00:00.0  0000:00:1a.1  0000:00:1c.1  0000:00:1d.2	0000:00:1f.0   pci_bus
0000:00:02.0  0000:00:1a.7  0000:00:1c.4  0000:00:1d.3	0000:00:1f.2   power
0000:00:02.1  0000:00:1b.0  0000:00:1d.0  0000:00:1d.7	0000:00:1f.3   uevent
0000:00:1a.0  0000:00:1c.0  0000:00:1d.1  0000:00:1e.0	firmware_node


 Any thoughts?

---

