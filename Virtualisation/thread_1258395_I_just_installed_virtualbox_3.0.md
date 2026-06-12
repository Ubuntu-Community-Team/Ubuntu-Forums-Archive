---
title: "I just installed virtualbox 3.0"
date: 2009-09-04
forum: Virtualisation
---

### Post by BrownTown6 on 2009-09-04
And the internet is laggin on the windows xp that i am running with it. I have 8 GB of hard drive set to it and 1 GB of RAM. Is there a way to increase the internet that will go too it. I would prefer that the internet screen on UBUNTU would lag. Thanks for the help.

---

### Post by Perryg on 2009-09-05
You should be able to improve the network speed by selecting the IntelPro/1000 T server for the adapter in the guest settings.  You may need to install the drivers in XP, so have them downloaded and in the guest so you can install them if you need to.

---

### Post by BrownTown6 on 2009-09-05
Thanks for that info but I installed the driver and it still is lagging. on the host computer I have about 5.5-6 Mbps. Is there another program that would work better or do I just need a better system? My system is 80 GiB hard drive with 2 GiB of RAM. It has a 2.4 Ghz Intel Pentium 4 preocessor. UBUNTU 9.04. Nernel Linux 2.6.28-15-generic. GNOME 2.26.1. The name and/or link to free software that runs as good of better then virtualbox would be much appriciated. Thanks.

---

### Post by jocampo on 2009-09-05
> **BrownTown6 said:**
> And the internet is laggin on the windows xp that i am running with it. I have 8 GB of hard drive set to it and 1 GB of RAM. Is there a way to increase the internet that will go too it. I would prefer that the internet screen on UBUNTU would lag. Thanks for the help.

Are you using NAT or Bridged network? Bridged has better performance. Switch to that one if NAT is your current setting.

---

### Post by Perryg on 2009-09-05
I have not found software that works better than VBox.  So tell me a little about what it is you are trying to do.  Copy file from host <> guest? Are you using the shared folders? That kind of thing would help.  And as jocampo pointed out if you have a router then Bridged may actually be faster.  That said I have several that use NAT and are sustaining 100 Meg throughput, so it can't be all VBox's fault.  Which version are you using and is it the OSE or PUEL version.

---

