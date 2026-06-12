---
title: "Using SMB with removable media"
date: 2007-01-04
forum: Server Platforms
---

### Post by Macskeeball on 2007-01-04
Hello. This is my first post here, so I'll begin with a paragraph about myself and my thoughts on Ubuntu so far. I'm a Mac user at heart, and have been for a decade now. As it stands right now, Mac OS X is currently favorite OS for the desktop. However, as a bit of a power user I am not afraid of the Unix-y side of the Mac, and I've been keeping a close eye on Linux for about a year or two now. At first that was limited to briefly playing around with various Live CDs, but for a few months now there's been a PC in the house that's on 24/7 running Ubuntu Server, and I've begun switching my dad from XP to Kubuntu. Linux has greatly impressed me with its astounding rate of progress and bang for the buck, and within 5-10 years from now I am confident that it will be ready for me to switch to it full time as my desktop OS (it's very close now).

I recently had an idea of yet another thing I could use the PC for: sharing removable media inserted in it over SMB to the Macs on the LAN. Neither Mac has a floppy drive, and in the unlikely event that someone hands me a floppy disk, it would be nice if I could use the PC to access it on the Macs. Also, my brother is planning on getting a Nintendo Wii which uses SD cards. The PowerMac that my brother uses has all of its USB ports used up and any PCI card I install would likely fry from the heat all of the internal upgrades I've made, so it would be nice if I could do the same with a card reader installed in the PC.

I don't have any floppies or SD cards (or an SD card reader, for that matter) yet, but I'd like to test the idea with CDs. I have an SMB share for a folder on the HD already working, and I've been able to use the CD-RW drive before for burning and ripping, so I know the drive works. However, I've been unable to figure how to manually mount and unmount the drive from the commandline. I know the device path is /dev/hdc and that in /media I have cdrom, cdrom0, floppy, and floppy0. I'm using Ubuntu Server 6.10, and any help with this would be greatly appreciated.

---

### Post by aragorn2909 on 2007-01-04
Easy, to mount /dev/hdc via command line,```
 sudo mount /dev/hdc
```

As for sharing that drive via samba, its exactly the same as sharing a local folder on the HD, just edit your smb.conf file appropriately

A.B.

p.s. - welcome to the forums

---

### Post by Macskeeball on 2007-01-04
Ah, I see. I had tried that before, but apparently what had been causing the error message I was receiving was that I was trying with an Audio CD. I had assumed that the CD would just mount and show all the tracks as files like my Macs do, but after a small amount of searching I learned that it can't be done in Linux without cdfs. No big deal, as I don't see a need to do that anyway. I tried a data CD and it worked just fine. Thanks for the help.

---

### Post by aragorn2909 on 2007-01-05
My pleasure.  I regularly share mp3 disks via samba, and it works like a charm.

A.B.

---

### Post by xdefconx on 2008-01-30
huhuhu...it is here anyone had done succesfully to share your pendrive/USB drive on ur Ubuntu over the LAN ? huhuhuhu may i know how to do that?

Thanxs

---

