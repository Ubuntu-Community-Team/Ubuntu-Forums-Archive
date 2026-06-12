---
title: "Help with finding tutorials for router/NAS project"
date: 2011-07-06
forum: The Cafe
---

### Post by Statik on 2011-07-06
Hi all,

I've been fascinated with the tiny Linux distributions I've seen around that run on low-powered Internet devices lately. The two main ones are Gargoyle, which installs on a router, replacing the original firmware, and SnakeOS, which installs on a cheap NAS, again replacing the original firmware.

I've been looking around and I can get an older laptop for less than $30. It is 2 to 3 times more powerful than either of these devices. I was thinking that it would be cool to combine the features of both those devices into a small Linux distribution that would run on the laptop.

I've worked through about half of the Linux-from-scratch setup before, so I thought I'd start with something like that, and I think things like samba, iptables, etc. can be used. The one thing I haven't found is a tutorial for making a web interface that can affect those settings. Can anyone point me to such a tutorial?

As well, any ideas of features or tools that could accomplish the different tasks would be appreciated.

Main features desired:
NAT
DHCP
Wireless access point
Whitelists (depending on MAC)
MAC filtering
SAMBA
FTP
Web GUI
Transmission with web GUI

Hardware should support 802.1N, 2*100BT and USB (for 1TB HD)

Any help appreciated!

Statik

---

### Post by aeiah on 2011-07-06
have a look at openwrt or dd-wrt, unless you want to build the os yourself.

or install something tiny like lfs and see if webmin is light enough

---

### Post by Statik on 2011-07-06
I tried webmin before and found it rather too large and overly complicated for what I wanted. I'm looking for a tutorial on how to interface the webgui to the settings, like webmin. I have been a web programmer by trade, but not active currently. I'm comfortable building the OS myself, building the gui myself, but I'm not sure how to connect the two.

I'm probably going to use webmin's module list as a starting point for modules to include as they point to the individual sources as well. If I can manage to get something working, I'll release it FOSS as well, but this is more for my own cheap pleasure. :) I'm also open to using Tiny or DSL as a core. Just something small and quick.

The hardware will be an old laptop (700MHz with 20gig HD) so power won't be the problem. Small, easy to use and configure are priorities. Throughput is also essential. I'm sure the old laptop won't have the wireless I want, so I'll be adding USB wireless, and a second 100BT ethernet through USB as well. 
USB1 - wireless
USB2 - ethernet
USB3 - HD
USB4 - something else. Printer sharing? another HD, etc.

Thanks for the suggestion!

Statik

---

### Post by mips on 2011-07-06
Have a look at ZeroShell

---

### Post by wizard10000 on 2011-07-06
> **aeiah said:**
> have a look at openwrt or dd-wrt, unless you want to build the os yourself.


This.  DD-WRT will do everything but the torrent client out of the box.

I've got a pair of these running DD-WRT and so far they've been great.

[ASUS RT-N16 Wireless Router 802.11b/g/n up to 300Mbps DD-WRT Open Source support with USB Storage, Printer And Media Server]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320038")

On the 1TB external drive - if it's a 3.5" drive it'll probably require an external power supply.

---

### Post by Statik on 2011-07-06
This sort of solution is great, but I'm trying to accomplish two things:
1. Use less expensive hardware
2. Use higher performance hardware.

Using an older laptop will accomplish both of these tasks. As well, having used open-wrt and dd-wrt before I settled on gargoyle for my present router, and having used snakeOS, I think there is room for improvement. webmin tries to do too much, at least out of the box, and snakeOS and gargoyle, if joined, would work, but aren't x86 presently.

I also have an issue with my HD spinning down and not waking up on snakeOS, which I think is a problem with the drive itself. I'm hoping that I can use a more powerful implementation to add keep-awake functionality as well. Perhaps SMART monitoring as well. Who knows . . . the possibilities are great and with $20-$40 laptops available, its much cheaper than the linked solution.

Thanks tho, I think I'm on the right track.

Statik

---

### Post by jerenept on 2011-07-06
> **Statik said:**
> This sort of solution is great, but I'm trying to accomplish two things:
1. Use less expensive hardware
2. Use higher performance hardware.

Using an older laptop will accomplish both of these tasks. As well, having used open-wrt and dd-wrt before I settled on gargoyle for my present router, and having used snakeOS, I think there is room for improvement. webmin tries to do too much, at least out of the box, and snakeOS and gargoyle, if joined, would work, but aren't x86 presently.

I also have an issue with my HD spinning down and not waking up on snakeOS, which I think is a problem with the drive itself. I'm hoping that I can use a more powerful implementation to add keep-awake functionality as well. Perhaps SMART monitoring as well. Who knows . . . the possibilities are great and with $20-$40 laptops available, its much cheaper than the linked solution.

Thanks tho, I think I'm on the right track.

Statik

Try [FreeNAS]("http://freenas.org/") on the laptop?

---

### Post by Statik on 2011-07-06
Well, that's half the solution. It is a NAS like SnakeOS, but x86, but it isn't a NAT/router/firewall/whitelist. People have created one or the other, and webmin does it all, but is too complicated.

Again, great suggestion, but not quite what I'm looking for / wanting to create.

Thanks!

Statik

---

