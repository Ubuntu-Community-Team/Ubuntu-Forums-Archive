---
title: "USB port doesn't appear to work"
date: 2008-07-16
forum: Server Platforms
---

### Post by 47_MasoN_47 on 2008-07-16
I'm using a Dell Poweredge 1600SC.  I have a USB hard drive with backup files on it that I want to transfer to it to use as a temporary file server but the USB ports don't appear to work.  It has 2 USB ports on the rear.  I tried detecting the USB ports/devices by doing the following.
```
$ lsusb
Bus 001 Device 001: ID 0000:0000
```
I'm not really sure what that means, but to me it looks like it isn't really detecting the USB ports.

Anybody know of a way I can fix this?  It's rather urgent.

---

### Post by Arthur Archnix on 2008-07-16
A few hints / places to start looking.

1. Run these commands as "sudo", so "sudo lsusb". Could make a difference. For lshw it does.

2. sudo lshw

3. read your boot logs for errors, or post them.

4. run dmesg, then plug in a usb device and run dmesg, then unplug and run dmesg.

---

### Post by 47_MasoN_47 on 2008-07-16
Thanks for the reply.  I ran lsusb with sudo before and it didn't make a difference.  I did sudo lshw and it shows the USB controller and has all the right information about it, or so it appears anyway.

It seems to say the same thing every time I run that dmesg command.

---

### Post by Arthur Archnix on 2008-07-16
Time to post those logs then. dmesg should have said "oh hey, you plugged in a usb device. Then, geez, I don't know what to do with it. Or here's where I mounted the darn thing.

The fact that it did none of that means... your machine has bad juju. Let's see the logs and see if we can find a spot where things go sideways.

Also, try a few different usb devices and all usb ports with that dmesg command. Things like a usb mouse, or flashdrive are better to use and test with than usb connected hard-drives.

Oh, and some bios's have the option to disable usb ports, or disable usb legacy support. Take a look if yours has that "feature".

---

### Post by 47_MasoN_47 on 2008-07-16
Pardon me for being rather n00bish here, but where do I find those logs?  Also, sorry for the delay on posting, I was in a conference call with my boss for several hours trying to decide what to do with the currently dead server.

Pretty much everything around here has bad juju out the wazoo.  I tried a flash drive and a USB drive (that's all the USB devices I had available atm) and it just listed this huge looping string of crap every time.  If you want a screenshot I can take one and post it up here.

To try to remedy the problem with a quick fix I went to Best Buy and bought one of those Dynex 4 port USB PCI cards.  I stuck that in there and the drive came to life!  So at least we can get to the files.  I'd still like to get those built in ports working though.  I'll check that BIOS "feature" out after my next restart.  It may very well be that they are disabled. Even when this thing had Windows 2000 on it they didn't work.

---

### Post by 47_MasoN_47 on 2008-07-16
Wow...wow...wow...talk about more of that bad juju... One of the hard drives in the RAID array just killed over in that server.

Anybody want some free shafts?  I seem to be having tons of them thrown my way today.

---

### Post by moore.bryan on 2008-07-16
for me, the issue was with the ehci-hcd module; try ```
sudo modprobe uhci-hcd
``` and then plug-in your device(s).

---

### Post by 47_MasoN_47 on 2008-07-18
I'll try this and see if it works.  I'll have to wait until Monday though.  We had a hard drive go bad so I'm waiting for a replacement.  I don't really want to mess with it until then in case another drive goes out.

---

### Post by moore.bryan on 2008-07-18
no worries... just hope it works for you. i'll be traveling out-of-state monday morning, but i'll be able to check-in later in the day to help troubleshoot if you still need it.

---

### Post by Arthur Archnix on 2008-07-18
> **47_MasoN_47 said:**
> I'll try this and see if it works.  I'll have to wait until Monday though.  We had a hard drive go bad so I'm waiting for a replacement.  I don't really want to mess with it until then in case another drive goes out.

It's a good idea that. The logs you're looking for are under /var/log .... just open up each one and have a look. It's a good thing to do from time to time to better understand the system.

The fact that it never worked under windows is a bad sign. It pretty much means cross your fingers and hope it's bios related, otherwise, buying the 4 port card was a really smart move.

Keep us posted.

---

### Post by DeeZiD on 2008-08-24
Well, it worked at least for me.:)

---

