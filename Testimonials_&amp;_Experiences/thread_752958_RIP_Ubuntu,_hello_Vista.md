---
title: "RIP Ubuntu, hello Vista?????"
date: 2008-04-12
forum: Testimonials &amp; Experiences
---

### Post by neonmagnolia on 2008-04-12
Okay, a few months ago I got a Dell Inspiron 1420 that came with Vista installed. For obvious reasons I jumped ship and made the switch to Gutsy Gibbon, cold turkey, after about a month of Vista. I've had some difficulties along the way getting my mic to work among other things, and have struggled from time to time using the terminal. But I liked learning, and was excited to get my hands dirty and *really* learn how to use my computer.

I also have a sixth generation iPod. Up until just recently I hadn't synced my music with it, because for various reasons I hadn't gotten any new music. I recently grabbed about 3GB of albums from a friend, and while attempting to add those to my iPod, I failed miserably. See my post about it here: [http://ubuntuforums.org/showthread.php?t=752290](http://ubuntuforums.org/showthread.php?t=752290)

So I think I've come to the realization that my iPod just isn't compatible with Linux. Thanks, Mr. Jobs, for that one. While Googling this issue I read there is a solution out there, but it's not an easy one, and being so new to linux I can barely even handle the "easy" solutions. Does this mean that in order to get my music back on my iPod I'm going to have to jump back on the bandwagon and revert back to Windows? Somebody please tell me there is a better option out there.

---

### Post by apo00 on 2008-04-12
This is my option (I'm using it): dual boot Vista/Linux
I use Vista when I need connect my iPod or my Nokia phone to PC.
However, I rarely connect iPod/phone, about once a month. If you need update your music everyday, it isn't a good choice for you.
P/s: I'm also a Linux/Ubuntu newbie and I don't want to struggle with connecting media devices to Ubuntu.

---

### Post by trippinnik on 2008-04-12
I've also been able to use Music players through VitualBox running windows and letting VirtualBox handle the USB device.  I also checked on the status of rockbox, but they don't support 6th gen yet.  This is actually one of the reasons I've never considered getting and Apple iPod.

---

### Post by ShelJ on 2008-04-12
I've been having problems with my Philips for about 6 months but found a 2 step solution that works better than whinedoze or iTunes.  Download GRip and Gnomad and follow these two steps:
1.  Rip CDs using GRip.  (It sounds like this is not your problem though)
2.  Transfer the them to your iPod using Gnomad.  If a song doesn't transfer check that there are no illegal characters in the filename, I had this problem with a CD that iTunes couldn't pick up on, but was able to see in Gnomad.

---

### Post by russo.mic on 2008-04-12
I very much recommend virtualbox for running a windowsXP or vista virtual machine.  Very easy to setup, and your Ipod, Phone, or whatever won't ever know it's not a real vista machine.

Good Luck!

---

### Post by Wobblybob on 2008-04-12
I have an 80gb ipod classic that I connect to ubuntu using amarok and gtkpod it took a bit of doing but these two threads helped a great deal.

[http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic]("http://ubuntuforums.org/showthread.php?t=619615&highlight=ipod+classic")

and

[http://ubuntuforums.org/showthread.php?t=611404&highlight=ipod&page=2]("http://ubuntuforums.org/showthread.php?t=611404&highlight=ipod&page=2")

---

### Post by h4mx0r on 2008-04-12
Go to [www.virtualbox.org](www.virtualbox.org) follow their install guide then:

 gedit /etc/init.d/mountdevsubfs.sh
Look for the part about magic and make it say this:

      #
      # Magic to make /proc/bus/usb work
      #
      mkdir -p /dev/bus/usb/.usbfs
      domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
      ln -s .usbfs/devices /dev/bus/usb/devices
      mount --rbind /dev/bus/usb /proc/bus/usb

Open the file /etc/udev/rules.d/40-permissions.rules 

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device", MODE="0664"

to MODE = "0666"

You will now be able to run any windows product virtualized and have full access to any usb device from webcam, ipod, usb toaster, usb headphone, flash drives, whatever. Let windows pillage the f*** out of your usb all from the comfort of a stable ubuntu system, cheers and goodluck with your tunes :)

---

