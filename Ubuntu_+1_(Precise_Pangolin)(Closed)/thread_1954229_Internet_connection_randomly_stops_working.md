---
title: "Internet connection randomly stops working"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by adamant715 on 2012-04-07
I am currently using Ubuntu 12.04 Beta 2 and the internet connection seems to randomly drop, and when it's working, performance is less than stellar (compared to Windows 7). My network card is a Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller. I have google'd far and wide for a fix and the only one I could find is this: [https://launchpad.net/~foresto/+archive/extradrivers](https://launchpad.net/~foresto/+archive/extradrivers). The problem is, the sk98lin driver is not all that compatible with the most recent kernel in Ubuntu (3.2). So I'm wondering if anybody could help me? I've read that the sky2 driver is rather buggy in Ubuntu, so maybe there's another driver.

---

### Post by joeboomer628 on 2012-04-12
I am having a similar problem except different interface. My motherboard has dual Realtek 8111 DL GBE interfaces. At first I thought it was a driver problem because the r8169 was selected and the r8168 is associated with my hardware. I went to the realtek site and they have a driver package with an autorun.sh script that will replace the r8169 with r8168 and configure it. This was successful in replacing the driver but did not solve the problem. I then removed network manager and replaced it with wicd and the performance and reliability improved significantly. Gnome network manager has been through significant changes since the gnome 3 process started and I suspect there is a bug but am not experienced enough at bug chasing to root it out. I am using wicd until precise updates again but this keeps me from running gnome 3 because network manager removal cripples it. It's ok in Unity.

---

### Post by mathia on 2012-04-13
Hi,
try to install the latest driver (v10.92.1.3) from:

[http://www.marvell.com/support/downloads/search.do](http://www.marvell.com/support/downloads/search.do)

and let me know the results.

---

