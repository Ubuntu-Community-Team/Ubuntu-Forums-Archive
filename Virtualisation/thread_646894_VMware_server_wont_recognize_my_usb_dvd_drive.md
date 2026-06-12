---
title: "VMware server wont recognize my usb dvd drive"
date: 2007-12-21
forum: Virtualisation
---

### Post by systemintheglitch on 2007-12-21
Hi..
i have a dvd drive.. It is plugged in and the cd drive shows up on my desktop as a cd..

Now.. The only option in my virtual machine gives me for the cd drive is autodetect..
and let me tell you..
it does NOT auto detect my usb dvd drive.

---

### Post by fjgaude on 2007-12-21
In order for VMware in Gutsy to recognize USB devices you need to uncomment four lines, like so:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment lines 42-45, starting with #mkdir -p /dev/bus/usb/.usbfs

That should do it. If not get back with us.

---

### Post by systemintheglitch on 2007-12-22
wow thank you. I couldnt find that on google search at all.

---

### Post by systemintheglitch on 2007-12-22
that did not work

---

### Post by lmcfadden on 2007-12-22
I am also running VMWare Server with Gutsy, and to access any of my USB devices, such as external hard drive, DVD or Memory stick, I have to select it from the *VMWare Server* menu as noted below.

VM>Removable Devices>USB Devices> Select the device you want to enable.

---

### Post by fjgaude on 2007-12-22
The next thing to try is to place this line in your fstab file and reboot:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Such seems to aid the ability to add USB drives.

---

### Post by edvisser on 2007-12-24
Just what I needed, frank. Thanks
Ed

---

### Post by edvisser on 2007-12-24
to clarify; I implemented both your suggestions frank, prior that, I had no devices appear on VM > Removable Devices > USB Devices.

---

### Post by fjgaude on 2007-12-24
Good, one more satisfied Ubuntu user. <smile>

Merry Christmas.

---

