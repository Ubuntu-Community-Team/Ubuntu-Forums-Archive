---
title: "what kernel version in 14.04?"
date: 2014-03-26
forum: Ubuntu Development Version
---

### Post by Ubi_one_2014 on 2014-03-26
According to distrowatch, ubuntu 14.04 gets kernel 3.13.0, while latest kernel is 3.13.7, and 3.14 is comming up

does 14.04 truelly got 3.13.0, and not 3.14?

---

### Post by grahammechanical on 2014-03-26
Trusty Tahr updated today has Linux kernel 3.13.0-17. If you are interested in what kernels are going into the Ubuntu development branch then follow the kernel team's meetings.

[http://voices.canonical.com/kernelteam/2014/03/25/kernel-team-meeting-minutes-march-25-2014/](http://voices.canonical.com/kernelteam/2014/03/25/kernel-team-meeting-minutes-march-25-2014/)

From the 4th March meeting

> [COLOR=#333333][FONT=UbuntuBeta]Our unstable branch has [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuBeta]also been rebased to track the latest v3.14-rc5 release.[/FONT][/COLOR]

[http://voices.canonical.com/kernelteam/2014/03/04/kernel-team-meeting-minutes-march-04-2014/](http://voices.canonical.com/kernelteam/2014/03/04/kernel-team-meeting-minutes-march-04-2014/)

There is almost a month to go before release date. Allow the developers time to work.

Regards.

---

### Post by ajgreeny on 2014-03-26
Actually, as of yesterday it now has 3.13.0-19, but who's counting?

---

### Post by Toz on 2014-03-26
*Moved to **Ubuntu+1***.

---

### Post by Ubi_one_2014 on 2014-03-26
> **grahammechanical said:**
> Trusty Tahr updated today has Linux kernel 3.13.0-17. If you are interested in what kernels are going into the Ubuntu development branch then follow the kernel team's meetings.

[http://voices.canonical.com/kernelteam/2014/03/25/kernel-team-meeting-minutes-march-25-2014/](http://voices.canonical.com/kernelteam/2014/03/25/kernel-team-meeting-minutes-march-25-2014/)

From the 4th March meeting



[http://voices.canonical.com/kernelteam/2014/03/04/kernel-team-meeting-minutes-march-04-2014/](http://voices.canonical.com/kernelteam/2014/03/04/kernel-team-meeting-minutes-march-04-2014/)

There is almost a month to go before release date. Allow the developers time to work.

Regards.

ok, but why not 3.13.7, or just latest kernel?

---

### Post by Mateusz Stachowski on 2014-03-26
> **Ubi_one_2014 said:**
> ok, but why not 3.13.7, or just latest kernel?

The kernel that is in repo is in fact 3.13.7 but Canonical have its own versioning.

Changelog from [3.13.7]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13.7-trusty/0002-debian-changelog.patch") in [mainline kernel]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") PPA:

> -  [ Tim Gardner ]
+  *** Mainline build at commit: v3.13.7**
 
-  * [Config] Add new mlx modules to d-i
-  * [Config] Fix d-i spelling error: ahxi_xgene --> ahci_xgene
-  * [Config] Added Muti-Arch support for linux-headers-PKGVER-ABINUM,
-    linux-tools-common, and linux-cloud-tools-common
-    - LP: #1295112
-  * Release Tracking Bug
-    - LP: #1296484
-
-  [ Upstream Kernel Changes ]
-
-  * Drivers: hv: vmbus: Specify the target CPU that should receive
-    notification
-    - LP: #1295813
-
- -- Tim Gardner <tim.gardner@canonical.com>  Sun, 23 Mar 2014 19:54:50 -0600

and changelog from [3.13.0-19.40]("https://launchpad.net/ubuntu/trusty/+source/linux/3.13.0-19.40") which is in Trusty:

> [COLOR=#333333][FONT=Ubuntu Mono]linux (3.13.0-19.40) trusty; urgency=low[/FONT][/COLOR]
  [ Tim Gardner ]

  * [Config] Add new mlx modules to d-i
  * [Config] Fix d-i spelling error: ahxi_xgene --> ahci_xgene
  * [Config] Added Muti-Arch support for linux-headers-PKGVER-ABINUM,
    linux-tools-common, and linux-cloud-tools-common
    - LP: [#1295112]("https://launchpad.net/bugs/1295112")
  * Release Tracking Bug
    - LP: [#1296484]("https://launchpad.net/bugs/1296484")

  [ Upstream Kernel Changes ]

  * Drivers: hv: vmbus: Specify the target CPU that should receive
    notification
    - LP: [#1295813]("https://launchpad.net/bugs/1295813") [COLOR=#333333][FONT=Ubuntu Mono] -- Tim Gardner <[/FONT][/COLOR][tim.gardner@canonical.com]("https://launchpad.net/~timg-tpi")[COLOR=#333333][FONT=Ubuntu Mono]>   Sun, 23 Mar 2014 19:54:50 -0600[/FONT][/COLOR]

You see that mainline build at commit v3.13.7

---

### Post by Gavin77 on 2014-03-26
```
gavin@kubuntu:~$ cat /proc/version_signature 
Ubuntu 3.13.0-19.40-generic **3.13.6**
```

This is the current kernel in the repos.  The kernel freeze is next week on April 3 so there's still time for a newer version.  I hope 3.14 gets in but I'm not sure if it will.

---

### Post by forcecore on 2014-03-26
even if 3.14 released day after or same day, developers always can make it happen.

---

### Post by grahammechanical on 2014-03-26
LTS releases are not supposed to be bleeding edge. And they do have point releases every six months for the first two years. The "latest and greatest" does not always = stable.

---

### Post by forcecore on 2014-03-26
3.14 has more advantages for LTS in longer timeline, for example 3.14 had better audio quality on older core2duo age IBM laptops. Someone had brand new AMD laptop and only with 3.14 it worked, 3.13 caused graphics lockups.

---

### Post by Gavin77 on 2014-03-28
[Linux 3.14 Isn't Going To Make It Into Ubuntu 14.04 LTS]("http://www.phoronix.com/scan.php?page=news_item&px=MTY0NTc")

---

### Post by Bucky Ball on 2014-03-28
> **ajgreeny said:**
> Actually, as of yesterday it now has 3.13.0-19, but who's counting?

Yep. This is me: 3.13.0-19-generic

I did a full update/dist-upgrade this afternoon.

---

