---
title: "GAZV4: No window decorations after 10.04 upgrade"
date: 2010-06-08
forum: System76 Support
---

### Post by bretthall on 2010-06-08
I upgraded to lucid over the weekend and everything went smooth except that I no longer have any window decorations when I first log in. If I go to the "System->Preferences->Appearance" control panel I see that desktop effects are turned off. Turning them on causes the window decorations to appear after the "searching for drivers" dialog displays for about 20 seconds. I have to do this everytime I boot up. Has anyone else seen this?

---

### Post by isantop on 2010-06-08
Did you perform a fresh install or an Upgrade from 8.04/9.10?

This sounds like a random upgrade error.

---

### Post by bretthall on 2010-06-09
> **isantop said:**
> Did you perform a fresh install or an Upgrade from 8.04/9.10?

This sounds like a random upgrade error.

I did an upgrade from 9.10.

---

### Post by isantop on 2010-06-09
Please run the following command from a terminal (Applications > Accessories > Terminal):
```
cat /etc/modprobe.d/blacklist.conf
```

Post the output here.

---

### Post by Tart on 2010-06-09
Recently my experiments created similar problem 
Try
```
metacity --replace
```
does it help?
Try this also if first one doesn't work
```
compiz --replace
```

---

### Post by bretthall on 2010-06-10
> **isantop said:**
> Please run the following command from a terminal (Applications > Accessories > Terminal):
```
cat /etc/modprobe.d/blacklist.conf
```

Post the output here.

Here it is:

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by bretthall on 2010-06-10
> **Tart said:**
> Recently my experiments created similar problem 
Try
```
metacity --replace
```
does it help?
Try this also if first one doesn't work
```
compiz --replace
```

I can't actually get to a terminal window to type them when I'm having the problem. I can launch a terminal but I can't focus any windows.

---

### Post by thomasaaron on 2010-06-10
Please try running this command...
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

If you can't type it into a terminal, try pressing Alt-F2, select "Run in terminal" and run it from there. Then, reboot your machine. Did that work?

---

### Post by bretthall on 2010-06-11
> **thomasaaron said:**
> Please try running this command...
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

If you can't type it into a terminal, try pressing Alt-F2, select "Run in terminal" and run it from there. Then, reboot your machine. Did that work?

That didn't help. I'm guessing there's something wrong in my home directory, if I create a new user everything works fine for that user. I only encounter the problem for the user that I had before the upgrade.

---

### Post by thomasaaron on 2010-06-11
OK. Then try running this command...

mv .gnome2 .gnome2.bk

Then reboot. It should create a new version of the .gnome2 directory/config files. Maybe that will straighten it up.

---

### Post by bretthall on 2010-06-13
> **thomasaaron said:**
> OK. Then try running this command...

mv .gnome2 .gnome2.bk

Then reboot. It should create a new version of the .gnome2 directory/config files. Maybe that will straighten it up.

Nope, that didn't help either.

---

### Post by devil404 on 2010-06-22
Made a step closer with [FONT="Courier New"]compiz --replace[/FONT]

```
me@laptor3:~$ compiz --replace
/bin/sh: emerald: not found
/bin/sh: emerald: not found

```

So, I did a [FONT="Courier New"]sudo apt-get install emerald[/FONT] to install the missing application. I ran [FONT="Courier New"]compiz --replace[/FONT] again, and VOILA! there's window decorations again. I'll post again after a reboot to confirm. I just got so excited about being able to move my windows around I had to say something.

---

