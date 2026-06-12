---
title: "Does VirtualBox require the SATA drivers to load XP?"
date: 2010-01-16
forum: Virtualisation
---

### Post by frogotronic on 2010-01-16
This is a superNOOB question:

If I have to use a floppy that contains a disk image of my SATA HDD driver to install M$ Windows XP on a DELL Dimension 8400; do I also need to mimic (load the floppy SATA driver at the appropriate point in time) this same procedure if I am now trying to install XP as a guest O/S using VirtualBox wherein Ubuntu Karmic Koala is the host O/S?

In other words, VirtualBox doesn't automagically fix M$'s lack of a SATA driver, does it?

Thanks,
CH

---

### Post by jocampo on 2010-01-16
Not sure if I understand your question but only thing you need to install XP as a guest is your Os disk. You map that via VBox so your soon to be created virtual machine can boot from CD. After that, the process is seamless. VBox uses its own drivers in order to create the "fake" partition or hard disk.

---

### Post by AlexandreP on 2010-01-18
VirtualBox creates a new virtual machine, which is litterally a new "fake computer" residing inside your computer. A virtual machine acts the exact same way a real computer does.

So if, in a real computer, the Windows XP installer needs a SATA driver to recognize SATA disk drives, then yes, you will need to provide such drivers to Windows installer to correctly install Windows XP into a virtual SATA drive in the virtual machine.

To avoid this, you could simply "plug" your virtual disk as IDE instead of SATA. You can configure this in your VM's preferences. (I don't know exacly where, because I don't have VB in English, but you can configure this in your VM's preferences. Just search a bit.)

---

### Post by frogotronic on 2010-01-18
> **AlexandreP said:**
> VirtualBox creates a new virtual machine, which is litterally a new "fake computer" residing inside your computer. A virtual machine acts the exact same way a real computer does.

So if, in a real computer, the Windows XP installer needs a SATA driver to recognize SATA disk drives, then yes, you will need to provide such drivers to Windows installer to correctly install Windows XP into a virtual SATA drive in the virtual machine.

To avoid this, you could simply "plug" your virtual disk as IDE instead of SATA. You can configure this in your VM's preferences. (I don't know exacly where, because I don't have VB in English, but you can configure this in your VM's preferences. Just search a bit.)

Hi,

  Thanks for this - that's exactly what I did, I choose the IDE and VirtualBox was smart enough to deal with the issue.

  Of course I now have another issue - I only have 512 MB on the entire machine (both host and guest), so now the guest O/S slows the whole machine down and then ultimately aborts.  I've read that XP SP3 requires about 512MB for decent operation, so I'll be getting that RAM upgrade I've been putting off - I'm thinking 2 GB and assigning 1GB to the guest O/S.

- CH 

:P

---

### Post by mister_playboy on 2010-01-19
It's well worth setting up your VM to use SATA, as it runs quite a bit faster that way.

You can still upgrade your VM to use SATA even after you install.  Boot the XP machine with the ACHI controller turned on, and install "Intel Matrix Storage Manager" version 7.8.0.1012 (get it right [here](http://drivers.softpedia.com/get/Other-DRIVERS-TOOLS/INTEL/Intel-DX48BT2-Intel-Matrix-Storage-Manager-7801012.shtml)).  After install, shut the machine down, move the HDD from the IDE to the SATA controller, and it should boot.

The only downside to this is that it always shows the HDD as an attached device in the systray... that is avoided if you load the SATA drivers during the initial VM install.

The process is very similar for Win2000, but you need a different floppy image (for a new install) or executable (upgrading current install) called Intel Matrix Storage Drive version 7.0.0.1001.

Actually, this thread better explains the install on a fresh VM: [http://forums.virtualbox.org/viewtopic.php?f=2&t=9575](http://forums.virtualbox.org/viewtopic.php?f=2&t=9575)

---

### Post by frogotronic on 2010-01-19
Thanks, that's really helpful and thanks for the link.

- CH    :popcorn:

---

