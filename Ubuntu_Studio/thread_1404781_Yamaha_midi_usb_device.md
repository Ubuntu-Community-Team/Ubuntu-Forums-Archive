---
title: "Yamaha midi usb device"
date: 2010-02-11
forum: Ubuntu Studio
---

### Post by Fenderian_Mayhew on 2010-02-11
is it just me or is there no driver for Yamaha midi usb connectors. i found one but it doesn't seem to work. i need some help. 

thanks

---

### Post by GraysonPeddie on 2010-02-12
Open the terminal and type in this command:

sudo lsusb | grep Yamaha

This will tell you what device you have.

---

### Post by Fenderian_Mayhew on 2010-02-12
i have a 
Bus 002 Device 003: ID 0499:1009 Yamaha Corp. UX16 MIDI I/F

this is a usb to midi connector but JackControll and Muse don't recognize it

---

### Post by raboofje on 2010-02-13
> **Fenderian_Mayhew said:**
> i have a 
Bus 002 Device 003: ID 0499:1009 Yamaha Corp. UX16 MIDI I/F

this is a usb to midi connector but JackControll and Muse don't recognize it

It's listed at [http://www.qbik.ch/usb/devices/showdev.php?id=1451](http://www.qbik.ch/usb/devices/showdev.php?id=1451) . The comment says 'Use ALSA 0.9.0rc4 or later', are you? Do you have the snd-usb-audio kernel module loaded? 

Anything in dmesg or /var/log/messages or /var/log/syslog when you plug in the device?

---

