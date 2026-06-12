---
title: "Xubuntu no network applet"
date: 2012-03-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by The Cog on 2012-03-03
I just installed Xubuntu 12.04 B1 for a test drive on my netbook, and I can't find any way to enable the wireless network. There is no network manager applet. Running nm-applet command gives an error message that it can't find network manager's active connections (I forget the exact wording). There is a connections editor in the System menu, but I can't find any way to tell it to activate the connection after editing it.

This seems true of both the live CD and the system it installs.

Is there a way to activate wireless at all?

---

### Post by kazztan0325 on 2012-03-03
Yes, me too!
Network icon does not appear in Indicator Plugin on Xubuntu 12.04 Beta1!

So I installed "wicd" and uninstalled "network-manager-gnome".

---

### Post by kansasnoob on 2012-03-03
Same thing on Lubuntu :)

---

### Post by The Cog on 2012-03-03
OK, it looks like the fix is in. I connected an ethernet cable in order to install wicd, and found a huge number of updates - no network manager needed for the ethernet to come up. After a reboot, the network manager applet was there although I had to disable and re-enable networking for all the options to appear. It seems to be working now.

---

### Post by ChinaSailor on 2012-03-12
> **kazztan0325 said:**
> Yes, me too!
Network icon does not appear in Indicator Plugin on Xubuntu 12.04 Beta1!

So I installed "wicd" and uninstalled "network-manager-gnome".


Awesome easy fix - Thank You!

It also fixed the hang-up at boot time I.E... "Waiting for network config..."

Gnome was such a good thing, just a year ago, then Unity... ah~....

---

### Post by kazztan0325 on 2012-03-13
> **ChinaSailor said:**
> Awesome easy fix - Thank You!

It also fixed the hang-up at boot time I.E... "Waiting for network config..."

Gnome was such a good thing, just a year ago, then Unity... ah~....

Hi ChinaSailor,

You are welcome!

I agree with you, because Linux itineracy on my real machine is like below:

Ubuntu 9.10 > Ubuntu 10.04 LTS > Ubuntu 10.10 > Linux Mint 11 GNOME > Linux Mint 12 GNOME with Xubuntu Session (I don't use GNOME 3 Session, and I am running Xubuntu 12.04 Beta 1 in VirtualBox.)

I customized XFCE and made it be similar to my previous GNOME 2 Desktop.

...Oh, sorry moderators, I unconsciously wrote off topic, forgive me please!

---

