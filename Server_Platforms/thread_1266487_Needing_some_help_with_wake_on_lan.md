---
title: "Needing some help with wake on lan"
date: 2009-09-14
forum: Server Platforms
---

### Post by devin0 on 2009-09-14
I have been running ubuntu server for a while now and it is running great, however one problem i have been having is not being to turn the machine on remotely. I have tried to follow several tutorials to get wake on lan set up with no success. I am trying to get it set up so that i can wake the ubuntu machine up from another computer on the internet. Can someone give me a link to a good tutorial on how to do this or tell me how to do it? Thanks
-Devin D.

---

### Post by tgalati4 on 2009-09-14
Wake-on-Lan works fine with the Desktop version of Ubuntu.

The server version does not have the sleep scripts nor required modules by default.  If you can't sleep, then you can't wake.

What you want is boot-on-LAN.  Check the BIOS for a boot-on-LAN switch.

Otherwise, I don't know how to do that.

---

### Post by sherl0k on 2009-09-15
Indeed, wake-on-LAN is a feature that needs to be enabled in the BIOS. from there, sending a wol ping will wake it up.

windows version: [http://www.gammadyne.com/cmdline.htm#wol](http://www.gammadyne.com/cmdline.htm#wol)

for Ubuntu, install either the "wakeonlan" or "etherwake" package.

---

### Post by volkswagner on 2009-09-15
What hardware are you running?  If the NIC is onboard, it may only work from a sleep state.  My Gigabyte board does wake from a power off.

---

### Post by tgalati4 on 2009-09-15
My experience is that newer cards/chipsets will work from poweroff state, but it depends on the BIOS and the motherboard keeping 5V alive to the LAN when it is completely off.  You can verify this by looking at your router and seeing a signal light.  One of my gigabyte LAN machines shows up as 10 Mb/sec when off but powered and waiting.

Some of my older cards will only work from a sleep state because the motherboard doesn't supply power in the completely off state.

---

### Post by devin0 on 2009-09-15
I don't think my linux box has a wake on lan card so it wont work. :(
But I do have a windows computer on the same lan as the linux box that I have been able to power on with the wakeonlan command from my linux box. I want to be able to wake up the windows computer with the wakeonlan command
from the internet but I think I need to portforeward or something...I have tried port forewarding port 9 with no success how can I get it to work?

---

### Post by volkswagner on 2009-09-15
I had an issue when setting up port 9 forward on my router.  I can't find the exact article.

The summary was I had to change my subnet and forward port 9 to the broadcast address, since machines don't have an IP in the off state.

Here is a similar article.

[http://www.n01getsout.com/blog/2006/11/16/wake-on-lan-on-linux-with-a-linksys-wrt54g](http://www.n01getsout.com/blog/2006/11/16/wake-on-lan-on-linux-with-a-linksys-wrt54g)

---

