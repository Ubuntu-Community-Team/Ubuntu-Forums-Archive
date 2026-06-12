---
title: "Write Protect Removable Disks (Pen Drives, CD/DVD)"
date: 2009-12-15
forum: Security
---

### Post by gvvsss on 2009-12-15
Hi
I am a windows Technician and new to Ubuntu.

I have five systems at our workplace and we had windows xp running.
I locked Write access to removable drives in windows by editing registry and applying nero burning rights.

I recently planned to shift from windows to ubuntu.
I could install and configure our systems to my needs but could not find a way to restrict users from writing to removable media.

Can anybody tell me how to get the same thing done in ubuntu.

---

### Post by bodhi.zazen on 2009-12-15
It is not so easy, start with these links :

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

[https://help.ubuntu.com/community/UsbDriveDoSomethingHowto](https://help.ubuntu.com/community/UsbDriveDoSomethingHowto)

---

### Post by gvvsss on 2009-12-16
Thanks for the quick reply,

I have read both the articles, but my requirement is somewhat different.

I want the flash drives (Any, not just which I configure with a serial number or so) to be automounted from all ports as it does now, but want the selected users to have just read-only access to it.

In windows this is done through defining "storagedevicepolicies->writeprotect=1"
in windows registry

I would like to know any equivalent kind of apllying policy based restrictions in ubuntu.

Is there a way to mention this in user previleges, like we have one to allow or deny use of removable devices. In the same way a choice to define whether they can write to it or not.

---

### Post by BkkBonanza on 2009-12-16
I would expect that using udev rules when it triggers to mount a usb device it could force a read-only mount option. I don't know the way to do that but I think that would be the game plan. When you mount manually you can specify read-only so it should be doable through udev.

---

### Post by BkkBonanza on 2009-12-16
I was very curious about this so I did some checking around and found out a few things. 

On Ubuntu the automounting is handled by gnome-volume-manager not simple udev rules. GVM doesn't appear to have options for readonly as far as I could find. On the server version GVM isn't installed (no Gnome), and so some people have been using ivman to do this. Since udev is already present I would have thought that's enough but perhaps ivman has more features. I did see that ivman allows customizing the mount command.

It appears as possible to add a udev rule for automounting with forced readonly and then removing GVM so it doesn't interfere. I was looking at automount rules on Arch linux as I couldn't find any for Ubuntu. Here is an potential example of a rule file to place in /etc/udev/rules.d,

KERNEL="sd[c-z][0-9]"
ACTION=="add", RUN+="/bin/mkdir -p /media/usbhd-%k", RUN+="/bin/ln -s /media/usbhd-%k /mnt/usbhd-%k"
ACTION=="add", RUN+="/bin/mount -t auto -o readonly /dev/%k /mnt/usbhd-%k"

I think this is the idea but some things are likely not right, and I'd prefer a better naming method for mounts. This triggers upon device insertion and creates amount point and mounts with forced readonly. I haven't tried it.

---

### Post by gvvsss on 2009-12-16
Thanks BkkBonaza

The idea seems good, I will try to do that.

Seems it takes time for me to implement since I am new to linux and I am trying to read about udev and gvm.

---

### Post by gvvsss on 2009-12-23
What I found is that GVM is not running in my Karmic at all, besides, I have read about udev rules and it is not so convincing to use any in my system.

I could not find a better guide or tutorial to use udev rules in special cases either.

---

### Post by BkkBonanza on 2009-12-23
I've looked at this again and almost got it working. The problem is a timing issue in the udev process that make the mount fail. So I'm going to dig in a bit more til I find a way around this.

The way I have done it is with a udev rule as follows,

KERNEL=="sd[b-z][0-9]", ACTION=="add", RUN+="/bin/mount -o remount,ro /dev/%k"

This does cause a remount to be done but because the original mount is not yet listed in the /etc/mtab file it fails the remount operation. I have done this manually at the command line and the remount does change usb removable devices to read only.

Another alternative would be to setup some mechanism that watches for mounted devices and remounts them when they occur. A simple script could do this with a sleep loop but it would be nice to fit it into the udev system properly. I probably just have something wrong with the rule that triggers it at the wrong time.

---

### Post by BkkBonanza on 2009-12-23
Ok. So some hours later I figured this out. I had some problem that was causing udev to not ever detach from scripts started by it. Very weird. Maybe related to debug mode logging... not sure. After a reboot it seemed to be behaving better. Then my solution here worked ok.

Create a udev rule file: /etc/udev/rules.d/automount-readonly.rules
Containing two rules:
```
KERNEL=="sd[b-z][0-9]", ACTION=="add", RUN+="/usr/local/bin/remounter /dev/%k"
KERNEL=="mmc*", ACTION=="add", RUN+="/usr/local/bin/remounter /dev/%k"
```

The second rule above is for SD cards which get silly names.

Now create the needed script: /usr/local/bin/remounter and chmod +x as well,
```
#!/bin/sh
{
/bin/mount -o remount,ro $1
while [ $? != 0 ]; do
	/bin/sleep 1
	/bin/mount -o remount,ro $1
done
} &

```

Run,
sudo udevadm control --reload-rules
to load the new rules.

Now plug in usb devices to try out. They should all load read only.
Note the rule would be different if more than one fixed hard disk (/dev/sda) is present so it may be nice to somehow determine this at runtime or as an install script maybe. I tried two usb keys, an external usb hard disk and an SD card. They all mounted read only. 

I think it's possible to add a mount option noexec to prevent executing programs on usb drives too. That may be a good security idea. It would be easy to make an installer as well that auto-detects the first mount point.

I just worked through this because I wanted to know how it works but hopefully it will help others out there.

---

