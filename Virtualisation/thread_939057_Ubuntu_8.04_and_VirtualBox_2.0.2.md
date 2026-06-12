---
title: "Ubuntu 8.04 and VirtualBox 2.0.2"
date: 2008-10-05
forum: Virtualisation
---

### Post by Matt_TX on 2008-10-05
Hi,

I'm new to Ubuntu and VirtualBox and I'm having some problems that I hope the good people of this forum can help me with.

I'm running Ubuntu 8.04 (Hardy) and VirtualBox 2.0.2.

I've managed to install VirtualBox without any issues, I have a Windows XP guest running, guest additions are installed and everything appears to be working fine.  I made the changes to /etc/init.d/mountdevsubfs.sh to enable the code that provides USB support.  However, I want to be able to connect my cellphone to to the Windows XP so I can use "ActiveSync" and copy files back and forth.  I've tried everything I can find to get this to work, and no matter which solution I try, I get one of two issues...

Either A) I get the "Not permitted to open the USB device, check usbfs options." or...
B) As soon as I start my Windows VM my keyboard and mouse lock up and I have to reboot my entire system (cold boot - removing power cord).  It's like VirtualBox takes control of them and won't allow me to go back to my desktop.

I have tried making the changes described to /etc/udev/rules.d/40-basic-permissions.rules, including changing the "MODE" value to "0666" from "0664".  I've also tried adding "GROUP="vboxusers" to the line in the file.  It has no effect whatsoever.  Here is a copy paste of it currently looks like (returned to default after changes did not work):

> # USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"


Additionally, I have edited the /etc/fstab file.  This causes my keyboard and mouse to lock as soon as I start my Windows VM. I added the following line:

> 
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0


I tried various options for this line, including changing it to say devmode=666, and creating a separate group called "usbusers" as described in this tutorial:
[http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

It's been two days now, and I still can't figure this out.  I have been on every forum, read nearly all the posts and nothing seems to work - I always get one of the two outcomes described above.  

In terms of hardware, I have a run-of-the-mill Dell desktop and a wireless Dell keyboard and mouse.

If anyone can help, I would really be grateful.  This is new to me and I am trying as hard as I can to get everything to work.

Thanks in advance for your help...

---

### Post by howefield on 2008-10-05
Have you installed the OSE version of Virtualbox from the repository, or did you get the PUEL version from the virtualbox website ?

---

### Post by Matt_TX on 2008-10-05
> **howefield said:**
> Have you installed the OSE version of Virtualbox from the repository, or did you get the PUEL version from the virtualbox website ?

I downloaded the non-OSE version from this link:
[http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb](http://download.virtualbox.org/virtualbox/2.0.2/virtualbox-2.0_2.0.2-36488_Ubuntu_hardy_i386.deb)

I believe this is a package specially designed for Ubuntu Hardy (8.04).

---

### Post by howefield on 2008-10-05
Yeah, that's fine.

try the following command

```
echo "none /proc/bus/usb usbfs devgid=$(grep plugdev /etc/group | sed 's/plugdev:x:\(.*\):.*/\1/'),devmode=664 0 0" | sudo tee -a /etc/fstab
```

Taken from this thread

[http://ubuntuforums.org/showthread.php?t=828927](http://ubuntuforums.org/showthread.php?t=828927)

---

### Post by Matt_TX on 2008-10-05
> **howefield said:**
> Yeah, that's fine.

try the following command

```
echo "none /proc/bus/usb usbfs devgid=$(grep plugdev /etc/group | sed 's/plugdev:x:\(.*\):.*/\1/'),devmode=664 0 0" | sudo tee -a /etc/fstab
```

Taken from this thread

[http://ubuntuforums.org/showthread.php?t=828927](http://ubuntuforums.org/showthread.php?t=828927)

That didn't work, it caused my keyboard and mouse to lockup again and I had to do a hard reboot.  Basically, from what I can tell, it just added this line to my /etc/fstab:
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

Any other ideas?

---

### Post by krauser530 on 2008-10-05
try this:

sudo su

then:

VBOX=$(grep vboxusers /etc/group | sed 's/vboxusers:x:\(.*\):.*/\1/')

then:

mount -t usbfs -o devgid=$VBOX,devmode=664,nodev,noexec,nosuid none /proc/bus/usb

and restart

---

### Post by lannatwin on 2008-11-02
Did you ever find a solution?  I'm having similar problems.

---

