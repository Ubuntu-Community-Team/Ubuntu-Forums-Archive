---
title: "No Network after Gibbon to Heron upgrade"
date: 2008-07-11
forum: Virtualisation
---

### Post by brooney on 2008-07-11
Hey all,

i'm currently running 64 bit Ubuntu 8.0.4 on my Host machine using VMWare Server 2.x.  I have a number of guest machines, all 32 bit images, which have in the past worked correctly while running a mix of windows xp, windows 2003 and ubuntu 7.0.

I decided to upgrade one of my ubuntu guest machines yesterday and it seemed to work fine however i've lost my network.

i'm configured to use NAT as this is all with a wireless card and vmware does support bridged on a wireless card.

if i do ifconfig i can see my interface and it appears to be up.  doing an lsmod shows the two network modules loaded that i have seen discussed in other threads.  my network manager seems to think it is a wireless connection though as it only shows wireless info (all disabled).

i've run the vmware-config.pl script multiple times in a vain attempt that it may fix it.

i've tried to run dhclient on the eth0 interface which seems to work in that an ip address is assigned to the interface but network manager still doesn't seem to realize it and if i try to browse i still don't get anywhere.

anyone have any ideas/suggestions?

thanks
ben

---

