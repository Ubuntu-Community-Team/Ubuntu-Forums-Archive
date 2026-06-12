---
title: "x86 tablet (w10 to ubuntu touch) help"
date: 2016-07-19
forum: Ubuntu Phone and Tablet
---

### Post by jhay2 on 2016-07-19
hi i have an x86 tablet with windows 10 installed on it .. i just want to install ubuntu touch. but theres no ubuntu touch for x86 . 

i tried the desktop version .but it is not tablet friendly and also . sounds , wifi bluetooth , accelerator, sensor . camera are not working on my tablet , 

is there any tricks to install ubuntu touch on my tablet ? thanks in advance

---

### Post by grahammechanical on 2016-07-19
The description "x86 tablet" does not tell us anything about the hardware. It does not even give us a make and model that we can do a web search to find out about the hardware.

When you say that you tried the desktop version, what does that mean? A live session or did you install it? Even in a live session we can use Additional Drivers to install any drivers that may not be present in the ISO image. But things like drivers for accelerator sensors and built in cameras will not be present in the repositories. They are not usually required in the desktop version. You may find that Ubuntu Touch does not have drivers for all your hardware either.

This will be an experiment. Do you have a method for re-installing whatever OS is already on that machine? Are you willing to experiment? I would not risk it.

There are 32 bit (i386) Ubuntu Touch 16.10 pre-installed images. They are not ISO images. If I was to try this I would use a USB memory stick and then use the Disks utility's Restore Image function to put the pre-installed image on the USB stick. If I restored this image to a hard disk it would re-partition the hard disk. I know that. That is what will happen to the tablet if you find a way of putting a pre-installed image on to that tablet.

[URL="http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/"]http://cdimage.ubuntu.com/ubuntu-touch/daily-preinstalled/current/

[/URL]Regards.

---

