---
title: "Win Xp, Vmware Server Console And Usb Support"
date: 2007-12-01
forum: Virtualisation
---

### Post by fjodork on 2007-12-01
Hi.

Recently I got sick off dualbooting, and installed a vmware server console where i again installed win XP pro.. The most normal stuff works(internet, etc) but i got some programs that need a e-gate cyberflex usb dongle present in order to work or even start.

I added usb device in settings for the virtual machine and when booted up, i got to vm - removable devices - usb devices, but its empty,,,? 

I also uncommentet the lines 42-45 in this file: /etc/init.d/mountdevsubfs.sh, but didnt do any differnce...

so my question is: how can i make it work? or do i still have to dualboot?

---

### Post by Eagleorn on 2007-12-04
I'm having the same problem, I try to connect an USB device, but vm - removable devices - usb devices is empty. Did you find a solution?

---

### Post by fjodork on 2007-12-04
> **Eagleorn said:**
> I'm having the same problem, I try to connect an USB device, but vm - removable devices - usb devices is empty. Did you find a solution?

yes,,, You either need to reboot your system or restart the mountdevsubfs service like this:
```

sudo /etc/init.d/mountdevsubfs.sh start
```

Then it should work:P

---

### Post by dkjewel on 2008-01-10
No luck with that.  Any other ideas?

---

### Post by fjgaude on 2008-01-10
There's more to it than what you have done so far. You must uncomment four lines in that file, as you have already done:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Uncomment 42-45 lines starting with #mkdir -p /dev/bus/usb/.usbfs

 ```
        mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
 
```

You may wish to add this as a line in your fstab file:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Some have found this necessary for USB drives, likely a race issue.

Reboot and you should see your USB devices in VMware's Removable Devices menu.

---

### Post by dkjewel on 2008-01-11
fjgaude,

Thanks for your help, the edits to mountdevsubfs.sh did the trick!  As soon as I made the edits and rebooted, I had items show up in my USB devices list, unfortunately, the WD hard drive (the main goal of this exercise), was not among them!  But it was a start.

Well, I kept fiddling with it, and it seems that the devices need to be plugged in before you boot.  I'm not quite sure if they need to be plugged in before you boot into Ubuntu, or if they need to be in place before you boot the VM, but by having them plugged in before I rebooted allowed me to access both my external HD and my Canoscan LiDE 70 scanner (a model not supported by linux).

Having these two devices available to me removes two critical obstacles to migrating to full-time linux.

Many thanks, 
David

---

### Post by tom957 on 2008-01-13
fjgaude, it worked for me too. thanks a bunch!

---

### Post by rlsimpso on 2008-03-04
This worked for my as well.  Thank you very much.

---

### Post by JKeller1068 on 2008-03-11
Sorry to dig up an old thread, but THANK YOU!!!!

---

### Post by fjgaude on 2008-03-11
> **JKeller1068 said:**
> Sorry to dig up an old thread, but THANK YOU!!!!

You are welcome... I can take no special credit, for all comes from learning from other folks here on the forums.

Ain't life grand!

---

