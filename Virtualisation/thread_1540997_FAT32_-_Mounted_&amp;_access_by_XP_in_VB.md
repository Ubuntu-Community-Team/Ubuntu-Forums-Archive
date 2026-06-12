---
title: "FAT32 - Mounted &amp; access by XP in VB"
date: 2010-07-28
forum: Virtualisation
---

### Post by edwardLS on 2010-07-28
I have Lucid Lynx installed (AMD64), VirtualBox installed (3.2.6) and a Windows XP VM.  All seems to be working well and I have no complaint.  However, prior to trying what I would like to do I would appreciate some advice.  I really don't want to mess things up.

I have a FAT32 Logical partition mounted (always) in Lucid and I prefer it to be mounted always.  I would also like to have the Windows XP VM to have access to that logical partition.  Am I headed for trouble?  Is this possible?  Any help would be greatly appreciated.

---

### Post by TheFu on 2010-07-28
Have the hostOS mount the partition, then use vbox folder sharing to make it visible to any client VMs that you like. The vbox manual covers this "sharing" as do at least 15 other posts here.

Or, if the hostOS is Linux, share it with samba. This is more useful when you have machines that are on the network and you want both client VMs and other machines to access the shared folders with the same permissions.

This stuff is extremely standard and works. The only thing that I'm not certain about is the fat32 partition.  I know that NTFS host partitions and EXT4 and JFS host partitions can be shared between Linux and Windows VMs. I've never tried vfat or fat16 or fat32 myself.

---

### Post by Meow27 on 2010-07-30
ntfs-3g can handle ntfs pretty well. why do you need fat32? if you are trying to hold a big file (4GB+) you will suffer performance issues.

and to answer to you major question:

-you need guest additions installed on the guest OS
- you need to enable a shared folder on the hosts end (last menu option under the configuration menu)
- in XP guest, press [start button]+ [e] to open up an explorer window, on the side pane you will see a network folder thing, expand it and you will see something like a vbox server folder, keep expanding until you get to that shared folder you created.

edit--
sorta misread your psot, so if that fat32 comment doesn't apply, ignore it :P

---

### Post by edwardLS on 2010-07-30
Thank you both for your responses.  The FAT32 is a bit of a hold-over from my Dual-boot days when NTFS was not considered reliable in Linux.  I have been experimenting with Ubuntu for some time now, but I am now placing it into my 'production' system and abandoning dual boot.  I have a couple apps which I still need Windows XP for.  It is my plan, if I can get it all figured out, to run Windows XP only in a VM.  
VirtualBox and Virtualization is a relatively new concept to me.  I have been reading and studying and learning a lot.  My biggest weakness is my "search" capability.  It seems I have not mastered searching for topics and solutions well at this time.

---

### Post by Meow27 on 2010-07-31
have you tried out Wine?

its a windows compatibility layer for linux

to get the latest release, [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

you can browse the compatibility on the web by searching google

```
[name of program] appdb
```

---

