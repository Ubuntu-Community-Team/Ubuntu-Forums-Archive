---
title: "Map physical controller to specific /dev/input/js* device"
date: 2014-04-29
forum: Virtualisation
---

### Post by SeraphTC on 2014-04-29
I'm running a Win7 x64 Host, VirtualBox 4.3.10 with Ubuntu 14.04 Guest.  Guest Additions are installed.

I'm going to be using the Guest to run some older games (Primarily the LucasArts X-Wing Series) with hardware acceleration enabled (because drivers post Jan last year prevent this from working with older games - thanks to the magic of WINE and OpenGL, this isn't a problem via a VM ;) )

I've run into a little snag with my Joystick.  The game will use the lowest numbered JS device on the system - however, the VirtualBox Mouse Integration device is assigned dev/input/js0 whenever the VM is started, forcing my Joystick to dev/input/js1 when connected.

Now sure, I can sudo rm /dev/input/js0 (which works), but that's messy and I don't like it.

If the VM is rebooted with the joystick attached, on restart it will be assigned dev/input/js0 and the Mouse Integration goes to js1.

I've tried forcing SDL to js1, but it makes no difference (and even if it did I couldn't script it as it would break on reboot anyway, as the joystick would no longer be JS1).

Ideally, I'd like to force the system to set the Mouse Integration device to dev/input/js1 whether another joystick is connected or not.  Is that possible??

Failing that, is it possible to easily determine which device is set to which dev/input/js*, and then swap it to another, higher numbered js*?  (ie, if js0 = mouse integration, force it to js2?)

I'm willing to investigate other kinds of workarounds, so please feel free to throw ideas at me!!

Thanks for reading for any contributions you can make!

SeraphTC

---

### Post by SeraphTC on 2014-05-08
Does anyone have any ideas at all about how I can accomplish this?

---

### Post by sisco311 on 2014-05-08
> **SeraphTC said:**
> 
 I've run into a little snag with my Joystick.  The game will use the lowest numbered JS device on the system - however, the VirtualBox Mouse Integration device is assigned dev/input/js0 whenever the VM is started, forcing my Joystick to dev/input/js1 when connected.

If you can specify the device file in the game, then use the symlink in /dev/input/by-id, which will always point to the same physical device.

Otherwise you will have to write a udev rule.    [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

