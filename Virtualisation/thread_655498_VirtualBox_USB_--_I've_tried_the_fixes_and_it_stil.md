---
title: "VirtualBox USB -- I've tried the fixes and it still doesn't work"
date: 2008-01-01
forum: Virtualisation
---

### Post by A-dogg on 2008-01-01
Like the title says, I've added usbusers group, added the line 

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

to fstab, changed 40-permissions.rules to

# USB devices (usbfs replacement)
#SUBSYSTEM=="usb_device",              MODE="0664"
SUBSYSTEM==”usb_device”, GROUP=”usbusers”, MODE=”0664&#8242;&#8242;

changed mountdevsubfs.sh to remove the #'s so it's

	#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb

(question -- should there be 2 dashes before rbind above? mine has two but most directions i've seen seem to show one... not sure if that matters...)

but it still won't work. xp will recognize new hardware and attempt to install it (sometimes successfully -- as far as it says), but the drives still don't show up in My Computer.

Any advice?

---

### Post by fjgaude on 2008-01-01
There should be two dashes infront of rbind. That's the only question I can answer because I use vmware server.

Happy New Year!

---

### Post by rbprogrammer on 2008-01-01
> **A-dogg said:**
> 
...
changed mountdevsubfs.sh to remove the #'s so it's

	#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
...

just out of curiousity, did you remember to reboot after you modified mountdevsubfs.sh ??  i had to for mine to work..

---

### Post by A-dogg on 2008-01-01
90% sure I rebooted right after i made the change, but I've rebooted a number of times since then and nothing. It's weird, XP says it's installed the new hardware and recognized it, but it doesn't show up.

Oh, well... for now I've just created a shared folder and transfer stuff from my usb drive to linux to the shared folder and into xp. not that annoying.

happy new year back!

---

### Post by 50words on 2008-01-01
I would really like to find the definitive fix, as I have had no luck with the "fixes," either, and I want to use USB software like my scanner through Windows XP on VirtualBox.

---

### Post by Wiebelhaus on 2008-01-13
> **50words said:**
> I would really like to find the definitive fix, as I have had no luck with the "fixes," either, and I want to use USB software like my scanner through Windows XP on VirtualBox.

yea , this is asinine.

---

