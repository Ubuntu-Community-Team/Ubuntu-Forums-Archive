---
title: "Start up disk creator not working"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by thebelial on 2012-04-06
org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible  causes include: the remote application did not send a reply, the message  bus security policy blocked the reply, the reply timeout expired, or  the network connection was broken.

Getting that when trying to erase and format my Western Digital Passport external drive. The drive does work fine, and I previously formatted and installed Ubuntu 12.04 to it from Arch using the same start up disk creator, and everything worked fine.

Anyone else having this issue? I was trying to put Mint Debian on there and boot the iso from the external.

---

### Post by jerrylamos on 2012-04-07
Take a look at
[http://kitenet.net/~joey/blog/entry/Debian_USB_install_from_hybrid_iso/](http://kitenet.net/~joey/blog/entry/Debian_USB_install_from_hybrid_iso/)

Essentially, use gparted to format the USB to F32 then do
cat mini.iso > /dev/sdX
where sdX is sdb1 or sdc1 or ...
This assumes mini.iso is an "isohybrid" format like ubuntu.iso is.
That's quickest expecially considering USB flash memories are cheap.
Boot the USB....and you're up?

Another way is to copy mini.iso to your USB device, no formatting required assuming there's enough space.  I use USB hard drives which can range up to 100 GB so I can put lots of .iso's on them.
Then on the ubuntu you have booted make a file
```

sudo gedit /etc/grub.d/40_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Pangolin ISO sda5" {
set isofile="/precise-desktop-i386.iso"
loopback loop (hd0,5)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
Now do note the vmlinuz and initrd.lz file names have to be whatever your 
mini.iso uses.  I just browsed a debian live to find out
/live/vmlinuz1
/live/init1.img
replace casper with live
replace the 
precise-desktop-i386.iso
with whatever your iso name is.  
replace the (hd0,5) with whatever your USB device is, do a 
df
Then do
sudo chmod 777 /etc/grub.d/40_custom
sudo update-grub
sudo grub-install  
reboot and choose the iso file

Then if you want to install, do a
df
to see where the isodevice is,
then 
sudo umount -r -l /dev/sda1
or whatever you've booted on, select install and away you go...

I haven't done this with a debian for a while so it may take some experimentation and forum searches.  I've been doing it every few days on pangolin.  Once the 40_custom is set up, all I do is update the pangolin iso with zsync and reboot.

Now do note this ubuntu forum is a development forum for testers of "unstable" ubuntu's, so sometimes answers can be a bit complex...

Enjoy,

Jerry

p.s.  I don't bother with the USB, I just boot the .iso directly from the hard disk using a 40_custom entry as above.

---

### Post by cariboo on 2012-04-07
> **thebelial said:**
> org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible  causes include: the remote application did not send a reply, the message  bus security policy blocked the reply, the reply timeout expired, or  the network connection was broken.

Getting that when trying to erase and format my Western Digital Passport external drive. The drive does work fine, and I previously formatted and installed Ubuntu 12.04 to it from Arch using the same start up disk creator, and everything worked fine.

Anyone else having this issue? I was trying to put Mint Debian on there and boot the iso from the external.

I not sure the utility is meant for use with an external hard drive. When using it, all you are doing is essentially setting up the same as a Live CD on your external hard drive. I'd suggest you just do a regular installation on it, and make sure you put grub on, that way you can boot from your external drive, when you move to a different computer.

**Note:** To be able to install grub where-ever you want you need to use the manual partitioning option -- *Something Else* from the installation menu.

---

### Post by nm_geo on 2012-04-07
Doing more testing here.  Okay I just made a USB with Startup Disk Creator placed Linux Mint 9 on it that was the only mint iso I had on my computer.  Anyway it did complete and works. What I can't do is make it persistent that was the limitation I remembered.

---

### Post by VinDSL on 2012-04-09
> **thebelial said:**
> Anyone else having this issue?
Yeah, sorta...

I just tried to make a bootable USB drive using Startup Disk Creator.  I tried 4 times.  Every time it stopped at 28% complete.

I thought it might be because I'm running on top of Linux 3.4, so I restarted in Linux 3.3... same thing... stopped at 28% complete.

Next, I restarted in Ubu 10.10 Maverick.  Bingo!  Created a bootable USB drive with persistence, with no problem.

Looks like the Startup Disk Creator in Precise is janky...  ;)

---

### Post by VinDSL on 2012-04-09
As an aside, I forgot how clunky Gnome 2 is.  LoL!  :D

Okay, switching back to Unity...

---

