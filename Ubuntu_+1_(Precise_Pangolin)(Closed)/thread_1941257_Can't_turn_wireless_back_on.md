---
title: "Can't turn wireless back on"
date: 2012-03-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by enceladus47 on 2012-03-15
In gnome shell, I turned the wireless switch off by mistake, and when trying to get it back on it just stays off. When I go to network settings it shows wireless as unavailable...

Tried updating and restarting and it just stays off, so connected using ethernet for now, so any ideas what I should try?

---

### Post by TunaCanTommy on 2012-03-15
Try:

> sudo lshw -C network

See if you network shows Disabled or Unclaimed.

---

### Post by enceladus47 on 2012-03-15
Disabled

```
*-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c7:ab:e7:e8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi  driverversion=3.2.0-9-generic firmware=39.31.5.1 build 35138 latency=0  link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:f4c00000-f4c01fff
```

---

### Post by TunaCanTommy on 2012-03-15
Have you checked any BIOS settings that may have gotten changed ? ?
Make sure any hard switches are properly set . . . !

---

### Post by enceladus47 on 2012-03-15
It has nothing to do with BIOS, I switched it off from inside ubuntu and can't get it back on...

and I checked my windows partition and wireless still works there

---

### Post by enceladus47 on 2012-03-15
Ok solved, I found a command that re-enabled the network

```
sudo rfkill unblock all
```

However if I turn off the switch off manually again I can't switch it on except with that command. Thanks :)

---

### Post by TunaCanTommy on 2012-03-15
I don't think I can be of much help at this point . . !
Looks like your drivers are being loaded.
I responded because I have a similar situation. The icon in my systray is showing OFF, but when I checked using > sudo lshw -C network it looked like it was working, and it was, even though the Systray icon showed off-line. 
Yours however is showing "DISABLED" . . perhaps a network guy can jump in here and offer you some suggestions.

---

### Post by enceladus47 on 2012-03-15
Thanks for the help, for now wireless is working and I'll make sure I don't switch it off until I find a fix...

---

### Post by TunaCanTommy on 2012-03-15
Glad you got it working . . my problem was giving me fits.
You might want to make this SOLVED !

---

