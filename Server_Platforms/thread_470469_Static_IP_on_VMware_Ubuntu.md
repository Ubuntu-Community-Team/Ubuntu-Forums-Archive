---
title: "Static IP on VMware Ubuntu"
date: 2007-06-11
forum: Server Platforms
---

### Post by thethimble on 2007-06-11
[size=20]NVM, figured it out. Thanks.
[/size]

Hi. Third day with any form of linux so please bear with me. :). I have a virtual Ubuntu 7.04 partition that I installed without any problems. I managed to install php, mysql, apache2... Those are working perfectly.

I have my virtual machine running as a separate identity on my home network. I have assigned it a static public ip. However, navigating to the ip from an external computer doesn't work.

If I give my vm an internal address http works fine for all computers on the network.

I'm sure I've opened port 80 on my router. I don't know what else to do...



Thanks in advance!

---

### Post by 444 on 2007-06-11
On the router. You don't just open port 80, you say 'redirect port 80 to computer X, port Y'.

---

### Post by thethimble on 2007-06-11
I've done that.

Also, for some reason my VM isn't showing up on the "connected devices" list on my router, but I still have internet access from the VM o_O

I tried defining the static ip from the ubuntu network manager to no avail.

*stumped*

---

### Post by 444 on 2007-06-11
Well then I'm assuming it's setup so the vmware is on a second private network or something... (you didn't say how it was exactly).

So you'd have the router forward port 80 to the host pc, then you'd get some sort of app on the host pc to forward that port 80 to the vmware...

---

