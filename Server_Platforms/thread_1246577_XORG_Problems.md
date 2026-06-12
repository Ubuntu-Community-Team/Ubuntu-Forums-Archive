---
title: "XORG Problems"
date: 2009-08-21
forum: Server Platforms
---

### Post by wefojoij on 2009-08-21
Hi! I just set up a gui in Ubuntu server. But the /etc/X11/xorg.conf file is empty! Also, my Xorg process is taking up 100% of a cpu core. Can I resolve this?

---

### Post by cariboo on 2009-08-22
Go to System-->Administration-->Hardware Drivers and install the recommended driver for your video card.

---

### Post by wefojoij on 2009-08-22
I don't have a dedicated video card on the server ... the hardware drivers box is empty.

---

### Post by wefojoij on 2009-08-22
I need
       Driver "radeon"

---

### Post by wefojoij on 2009-08-22
I have the following card:
[http://ati.amd.com/products/server/es1000/index.html](http://ati.amd.com/products/server/es1000/index.html)

---

### Post by cariboo on 2009-08-22
What is the cpu usage when you stop X?

Edit: at the prompt try:

```
sudo dpkg-reconfigure -phigh xsever-xorg
```

This should create a default /etc/X11/xorg.conf file to which you can add the radeon driver.

---

### Post by wefojoij on 2009-08-22
What should I add to the file? Thanks...

---

### Post by wefojoij on 2009-08-24
Any ideas about the es1000 card? Many thanks!

---

