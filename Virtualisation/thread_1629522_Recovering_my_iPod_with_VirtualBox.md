---
title: "Recovering my iPod with VirtualBox"
date: 2010-11-23
forum: Virtualisation
---

### Post by coregan on 2010-11-23
Ubuntu 10.10 and VirtualBox v3.2.10

I have successfully connected my iPod Touch to a VirtualBox guest running Windows XP and iTunes. Last night I decided to update my iPod's firmware. I have done this many times before but with earlier versions of Ubuntu and VirtualBox and while there have been some hiccups I have been successful.

But now my iPod is stuck in Recovery Mode. I made some progress this evening (I had forgotten to add myself to the vboxusers group) and I can now start the recovery process in iTunes, but when the iPod resets itself partway through it switches out of Recovery Mode but is no longer accessible (it's listed under USB Devices but it's grayed out).

I found this article and my problem looks similar:

[http://forums.gentoo.org/viewtopic-p-6305578.html?sid=8b6dad53f7bd4f3206287eb4da68441b](http://forums.gentoo.org/viewtopic-p-6305578.html?sid=8b6dad53f7bd4f3206287eb4da68441b)

Sure enough, when I run usbmuxd in debug mode I am seeing similar output and it eventually segfaults.

I am running out of ideas.

---

### Post by tekkidd on 2010-11-23
You really need a computer with windows installed, after the ipod  enters recovery it disconnects from virtualbox and that it the end.

---

### Post by coregan on 2010-11-23
> **tekkidd said:**
> You really need a computer with windows installed, after the ipod  enters recovery it disconnects from virtualbox and that it the end.

I have done this before, and even with the disconnecting it's possible. Whenever the iPod disconnects, simply go to USB Devices and reconnect it. My problem is that when it switches out of Recovery Mode, my iPod reappears under USB Devices but is grayed out, I can't select it. This hasn't happened before.

---

### Post by coregan on 2010-11-25
Solved!

I compiled and installed the latest usbmuxd (1.0.6). It no longer segfaults during the recovery but the iPod was still grayed out. At this point I figured it was a permission problem but I wasn't sure where. I am a member of the plugdev and vboxusers groups. Installing usbmuxd overwrote "85-usbmuxd.rules" so it's quite possible that the magic I need is in the original, but I chose the lazier method: I created a symlink to my .VirtualBox directory in root's home and started VirtualBox as root. This time when my iPod switch from Recovery to normal, it appeared and I was able to continue. My iPod is now happily syncing.

It greatly helps to create filters for the iPod in both normal and recovery modes. VirtualBox was able to attach the iPod automatically and the recovery happened with little intervention on my part.

Once the sync is complete, I am going to restore the original usbmuxd and also take a diff of 85-usbmuxd.rules to see if something else explains the permission problems.

---

### Post by coregan on 2010-11-25
> **coregan said:**
> Once the sync is complete, I am going to restore the original usbmuxd and also take a diff of 85-usbmuxd.rules to see if something else explains the permission problems.

I think the permission problem I was experiencing was due to the udev rules file for usbmuxd. The Ubuntu version sets OWNER to usbmux, and I think that's what's needed under Ubuntu to give me the right to access the device.

Interesting... I killed usbmuxd and started a normal sync. I don't see usbmuxd in the process list. Is it only used during recovery?

Anyway, I think there is a bug in usbmuxd v1.0.4 and Ubuntu should update it to v1.0.6.

---

### Post by coregan on 2010-11-25
> **coregan said:**
> Anyway, I think there is a bug in usbmuxd v1.0.4 and Ubuntu should update it to v1.0.6.

Bug reported to Ubuntu.

---

