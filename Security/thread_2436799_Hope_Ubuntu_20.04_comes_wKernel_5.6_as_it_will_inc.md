---
title: "Hope Ubuntu 20.04 comes w/Kernel 5.6 as it will include WireGuard VPN"
date: 2020-02-13
forum: Security
---

### Post by bmullan2 on 2020-02-13
I strongly feel ***Canonical should make every effort to include Kernel 5.6  in Ubuntu 20.04 for these reasons***:

1)  ***Security is Top of Mind with Commercial Enterprise Businesses today*** because of Hackers, Ransomware etc 

2) ***WireGuard VPN has finally been pulled into Linux Kernel 5.6.***   This would be something to highlight w/20.04 !

3)  Ubuntu 20.04 is LTS !

---

### Post by rbmorse on 2020-02-13
There was an announcement in the last couple of days that 20.04 will use the 5.4 kernel.

---

### Post by EuclideanCoffee on 2020-02-13
Ubuntu 20.04 freezes a version of Debian sid and then tries to stabilize it. To this point, I think the kernel 5.6 is a bit new, so we shouldn't expect to see it supported yet in Ubuntu 20.04 LTS.

Building your own kernel shouldn't be impossible; however, so if you need it for enterprise, you certainly have the option of trying to support it yourself. :)

---

### Post by The Cog on 2020-02-13
That's  a shame. There are a lot of reasons to go for 5.6. It just means that 20.04 will outdated before it is even released.

But I have read that canonical plan to back-port Wireguard into 20.04, and that's the biggest reason to want 5.6. 

The other gizmo I would like to try is multipath TCP, but I guess that will have to wait for 20.10. I don't have a serious use for that right now, it's just something I'd be interested to try out.

---

### Post by kevdog on 2020-02-14
Isn't it possible to just install a new kernel into 20.04?

---

### Post by Bashing-om on 2020-02-14
20.04 is LTS, and HWE will provide for later kernels :D

---

### Post by guiverc on 2020-02-14
From the lastest UWN (issue 617 - [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue617?action=show&redirect=UbuntuWeeklyNewsletter%2FCurrent](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue617?action=show&redirect=UbuntuWeeklyNewsletter%2FCurrent))

> **Ubuntu 20.04 LTS Likely To Ship With Linux 5.4 As Opposed To 5.5**

[COLOR=#000000][FONT=Arial]Michael Larabel writes that whilst Linux 5.5 kernel has been released, it's probable that the current 5.4 kernel in Ubuntu 20.04 will be the default kernel shipped. However, upstream kernels will be available with the enablement of the HardWare Enablement (HWE) stack. Michael gives the reasoning for these likely decisions, **and reminds us that the Ubuntu kernel team has backported WireGuard support to the 5.4 LTS kernel**. Links are provided.

[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-20.04-Linux-5.4-Likely](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-20.04-Linux-5.4-Likely)[/FONT][/COLOR]


---

### Post by The Cog on 2020-02-15
> **kevdog said:**
> Isn't it possible to just install a new kernel into 20.04?

Probably. Maybe time to do some learning. Snapshot my system drive first, just in case I bork it (quite likely).

---

