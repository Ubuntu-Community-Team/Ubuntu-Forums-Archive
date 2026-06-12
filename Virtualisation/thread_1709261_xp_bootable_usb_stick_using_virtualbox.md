---
title: "xp bootable usb stick using virtualbox"
date: 2011-03-18
forum: Virtualisation
---

### Post by cyberboy109 on 2011-03-18
oki i dont have a dvd drive and i wanna install xp on my desktop as a 2nd os so i thought this would work
1 install xp os in virtual box
2. install files on xp to make bootable usb stick

but my problem is virtal box does show any of the usb sticks..no matter wat slot i plug the usb stick into it doesnt appear (its in fat)
iv even went into virtualbox setting and nothing comes up for usb any ideas?

---

### Post by Hedgehog1 on 2011-03-18
There is the USB setup on your VM:
 
[IMG]http://img683.imageshack.us/img683/2255/vboxusbsetup.png[/IMG]
 
 
[SIZE=3]**And add yourself as a Vbox user: [How-to-Fix-VirtualBox-USB-Support]("http://news.softpedia.com/news/How-to-Fix-VirtualBox-USB-Support-111715.shtml")**[/SIZE]
 
 
 
***The VIRTUAL Hedge***
 
:KS

---

### Post by varunendra on 2011-03-19
VirtualBox OSE (Open Source Edition) does not have USB support while the PUEL (Personal Use & Evaluation License) version does.

So if you need the USB support (as shown in the snapshot in the above post), you'll need to uninstall the default version (in ubuntu) , and install the PUEL version.

To do so, open Synaptic, select VirtualBox-OSE > mark for uninstall ("complete removal" not required) and apply the changes. Then open terminal, and type
```
sudo apt-get install virtualbox
```You may have to add additional repositories from virtualbox's website : [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Note that Virtualbox = PUEL version
and, VirtualBox-OSE = OSE version

Except for the USB thing, there is no difference AFAIK.




**_PS_:**

VirtualBox (PUEL) is already available in Linux-Mint repositories.

However, I don't think XP can be installed on or through USB disk in normal ways. But I've heard it is possible. If it becomes a problem for you (although it shouldn't) then here's one of my own ways (extremely crude one, so consider it the last resolution) to do it: [http://ubuntuforums.org/showpost.php?p=9190079&postcount=11](http://ubuntuforums.org/showpost.php?p=9190079&postcount=11)

---

### Post by Hedgehog1 on 2011-03-19
> **varunendra said:**
> ...

However, I don't think XP can be installed on or through USB disk in normal ways. But I've heard it is possible. If it becomes a problem for you (although it shouldn't) then here's one of my own ways (extremely crude one, so consider it the last resolution) to do it: [http://ubuntuforums.org/showpost.php?p=9190079&postcount=11](http://ubuntuforums.org/showpost.php?p=9190079&postcount=11)

Initial install of an OS to a USB stick is possible with a USB enabled Vbox 4.0.4.  To do it, you create a Vbox with no hard drive; select the ISO for the OS you want to load and select a USB device to install the OS onto.

Vbox will ***(for initial install only)*** treat the USB stick as /dev/sda (or 'C:' for XP).  After that, you can reboot off the USB and finish OS updates.

As a note, if you install Ubuntu on a USB drive (**Ubuntu-On-A-Stick!**) and do not want the PC hard drive's OSes as part of the USB Stick's Grub menu, you can delete the **30_op-prober** from ***the USB Stick*** before you do your first round of updates:

```
sudo rm /etc/grub.d/30_os-prober
```

***The Hedge***

:KS

---

