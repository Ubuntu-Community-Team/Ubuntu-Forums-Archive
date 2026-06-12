---
title: "Downloadable Ubuntu Studio Manual"
date: 2009-03-05
forum: Ubuntu Studio
---

### Post by Ouia on 2009-03-05
Is there one? Because I can't use my wireless in UbuntuStudio 64bit, and I have no idea how it all works.

Other option is to boot into Hardy, remember what I need and reboot into studio.
Over and over again because I have no idea it all works :)

---

### Post by DennisDee on 2009-03-06
I had same problems on ubuntu studio with wireless.

```
sudo apt-get install network-manager-gnome
```

After that reboot computer and it should work same as on Hardy

---

### Post by Ouia on 2009-03-06
It doesn't recognize it. Also, I'm using a Ralink RT2870.(sitecom 300N usb), which is troublesome on it's own in 8.04.

From what I see, all available packages are already installed. (I had synaptic also look at the install DVD).

---

### Post by soulful1 on 2009-03-06
I had the same problem when I booted from the DVD. I just sucked it up, downloaded HH 8.04, then upgraded to Ubuntu Studio through the terminal.

---

### Post by Stochastic on 2009-03-07
One easy solution is to plug your computer into your router until you fix the problem.  But, no there is no UbuntuStudio Manual.  The closest two things I can think of are the Community Docs: [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio) (there are tools that will let you download the whole webpage if you have the space)
or the official Ubuntu Book: [http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0137136684](http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0137136684)

---

### Post by Ouia on 2009-03-07
Thanks..

Looks like I have to use an extra computer for a while until I have the basics of studio down or until I manage to get connected.

I had an upgraded Hardy before, but that gave other problems, that are now solved by using a separate partitions for Hardy and Studio.

---

### Post by Stochastic on 2009-03-07
what wireless chipset do you have?
If you're not sure, just post the output of this command ```
lshw -class network
```

---

### Post by Ouia on 2009-03-08
Here it is...

[HTML]WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:df:b7:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       physical id: 2
       logical name: ra0
       serial: 00:0c:f6:4b:4c:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=172.19.3.7 multicast=yes wireless=RT2870 Wireless[/HTML]

---

