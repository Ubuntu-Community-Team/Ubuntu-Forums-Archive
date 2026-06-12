---
title: "Lightdm session screwed up after rebooting this morning"
date: 2015-03-16
forum: Ubuntu Development Version
---

### Post by wgarcia on 2015-03-16
After installing some updates and restarting my 15.04 Ubuntu laptop this morning, the system starts lightdm but it gets some messages from the bootup system and goes back and fourth from lightdm to text, and doesn't allow me to login past the lightdm initial screen. I tried booting both with systemv and upstart and both produce the same. 

Still investigating.

---

### Post by wgarcia on 2015-03-16
I could enter now the system with the previous kernel version, 3.19.0-7-generic, with the 3.19.0-9 I can't get past the lightdm initial screen, I start getting blinking messages from the acpi process being started, and I can't enter my password or do anything. I tried starting with "acpi=off pci=noacpi", and here I the graphics card is not recognized. So I'm going to try to report a bug on this.

---

### Post by dino99 on 2015-03-16
which graphic driver is used ?
how are the bios acpi settings set ?
have you switched to gdm ? (sudo dpkg-reconfigure lightdm) (might be installed by gnome-shell)

---

### Post by wgarcia on 2015-03-16
Now it is starting OK with 3.19.0-9, go figure...

---

### Post by wgarcia on 2015-03-16
Thanks 9d9, it's a Intel/NVIDIA system, using the NVIDIA with proprietary 340 drivers, the NVDIA is GF108GLM (NVS 5200M). No idea how the bios acpi is being set, was working fine for a year and half until this morning's update. I haven't tried to switch to gdm. 

In any case as I said in my previous message, I first booted fine with 3.19.0-7, and then tried to boot again to 3.19.0-9 to reproduce the error and report a bug, but it booted perfectly. I don't know if the previous successful boot did something and fixed it, or what...

---

### Post by grahammechanical on 2015-03-16
What you are experiencing sounds normal for kernel 3.19.0-9. Based upon my own experience that is.

I installed 3.19-rc and it would not build any Nvidia driver. So, I removed it and used 3.18. Then I got 3.19.0-7 through the normal update channels and that worked well with Nvidia. I next used dist-upgrade to bring in 3.19.0-9 and it would not build any Nvidia driver. But 3.19.0-7 would. So, I used that. Now here I am a few days later using kernel 3.19.0-9 with an Nvidia driver. And all I have done is daily update. As you say - go figure.

I am also getting the acpi error message. 

It is normal weather for this time of year. :)

Regards.

---

### Post by wgarcia on 2015-03-16
Yes, it looks like something went on switching from 3.19.0-9 to 3.19.0-7 and back, because I swear I didn't do anything else. The ACPI thing is a message that shows up when the bootup process starts, I read around it is a harmless warning, and this was not what caused my first message above. It was something related to the ACPI process starting, and the messages caused by that the would blink in the ligthdm login session, not allowing me to do anything, not even going to a text session with ALT-GR-6.

---

