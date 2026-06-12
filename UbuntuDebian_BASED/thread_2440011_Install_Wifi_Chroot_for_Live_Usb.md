---
title: "Install Wifi Chroot for Live Usb"
date: 2020-04-04
forum: Ubuntu/Debian BASED
---

### Post by Redalien0304 on 2020-04-04
Is it Possible Install a Restricted Proprietary WiFi Driver in Chroot for a Live Usb Iso??

---

### Post by yancek on 2020-04-04
A 'live' usb is a readonly filesystem by default so generally speaking the answer would be no.  Might be able to do with a persistent usb or you might be able to use the squashfs to modify and re-create the entire system but that is not for the faint of heart.  You can boot a live iso from a usb or dvd and install any software including wifi drivers that you want and use it as long as you want or until a reboot, shutdown or power outage.  Partly dependent upon the amount of RAM.  This is obviously no an ideal or even practical situation.

---

### Post by Redalien0304 on 2020-04-05
That is what i am looking to do is have WiFi ([COLOR=#000000]Restricted Proprietary WiFi Driver) [/COLOR]in a New Ubuntu CinnamonRemix Iso.
Using Cubic now to Modify a Current Iso.

---

### Post by yancek on 2020-04-05
I've never used Cubic but just doing an online search for 'cubic on ubuntu' provided a number of sites with instructions/tutorials on using it.

---

### Post by Redalien0304 on 2020-04-05
yah i have seen those tutorials but they do not cover what would like to do

---

### Post by tea for one on 2020-04-21
> **Redalien0304 said:**
> Is it Possible Install a Restricted Proprietary WiFi Driver in Chroot for a Live Usb Iso??

Are you referring to Broadcom using **bcmwl-kernel-source**?

---

### Post by slickymaster on 2020-04-21
*Thread moved to **Ubuntu/Debian BASED**.*

---

