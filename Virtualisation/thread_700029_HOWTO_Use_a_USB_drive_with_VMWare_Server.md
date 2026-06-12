---
title: "HOWTO: Use a USB drive with VMWare Server"
date: 2008-02-17
forum: Virtualisation
---

### Post by Belak on 2008-02-17
Ok, here's the easiest method I found for getting a USB drive to work in VMWare server. I really only wanted this to work because I wanted to run iTunes and Winamp since they work better for CD ripping.

ANYWAY.

I got this to work with:
SimpleDrive 250GB External Hard Drive
Xubuntu 7.10 Gutsy (The 'flavor' shouldn't matter)
VMWare **Server** 1.0.4

Here we go...

First, make sure your USB drive is mounted in Ubuntu (if you don't already know the 'dev location').
If it isn't then I'm sure you can find a guide to help you mount it... it doesn't have to be mounted for the VM to access it, though.

Second (also if you don't already know the 'dev location'),
run the mount command in a terminal with no options to get a listing of all the mounted file systems.
This may change when you mount it again... there is no way to set it automatically so you may have to change it every time... sorry (fixes?)
Find your USB drive by the place it was mounted (The out put will be in the format of 'dev location' on 'mounted loaction' then extra options) and take the dev location (I'm only calling it that because it should be /dev/sdx)

Next,
open up your VM Server and go to the settings of your XP OS then click on 'Edit Virtual Machine Settings'.
Click on Add and select hard drive then physical disk then enter in the 'dev location' for the device. The usage setting is your preference, but I think the whole disk is better.

The disk file doesn't really matter. It's just where the config settings for that drive will be stored.

Just click Finish and boot into your virtual machine.

Cheers,
Belak

---

### Post by K.Mandla on 2008-02-19
Moved to Virtualization.

---

### Post by Zalbor on 2008-02-19
Someone posted a method which I think is the best, but I can't find it right now...
It had to do with editing a configuration file and uncommenting 4 lines in it, then restarting the service. All USB devices appear in the VM menu then, including drives.

---

### Post by fjgaude on 2008-02-19
> **Zalbor said:**
> Someone posted a method which I think is the best, but I can't find it right now...
It had to do with editing a configuration file and uncommenting 4 lines in it, then restarting the service. All USB devices appear in the VM menu then, including drives.

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Add this line to your /etc/fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

That seems to solve all the issues people have had over the months.

---

### Post by Belak on 2008-02-20
> **fjgaude said:**
> ```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment lines 42-45 starting with #mkdir -p /dev/bus/usb/.usbfs

```

    	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Add this line to your /etc/fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

That seems to solve all the issues people have had over the months.
Ok, I tried that and it didn't work. That's why I came up with my own solution. I'm currently trying other ideas and trying virtualBox as well.

This is my work around solution for when all else fails.

---

### Post by boeing777 on 2008-03-04
good!! i tried the other solution, i didn't work. this one works, thank you!!!

---

### Post by monoufo on 2008-07-12
but where did you find a copy of XP with the scsi driver?

---

### Post by dcstar on 2008-07-13
> **monoufo said:**
> but where did you find a copy of XP with the scsi driver?

Installing VMware tools installs all required drivers.

---

### Post by monoufo on 2008-07-13
i was messing with the beta version of vmware workstation and they claimed that there was no scsi driver in windows so I couldn't even install xp.  later it turned out, that plan wasn't going to work anyways.

---

