---
title: "Removable Media Tools GUI"
date: 2008-05-25
forum: Ubuntu Brainstorm
---

### Post by musther on 2008-05-25
There are a few little nagging problems with ubuntu when it comes to USB drives:

All of these things can be done, but take command line experience and should really be possible with a GUI.  Thus, I propose the Removable Media Tools GUI for Ubuntu, probably accessed through the places menu.  

It should:
Show currently connected removable media, mounted and otherwise.
Allow easy mounting and unmounting of media.
Allow formatting/partitioning with FAT, NTFS or EXT2/3.
   Solve the permission issue created when using ext2/3, so if a user formats their USB drive with ext2/3, they can actually write to it by default.
   Should also possibly remove the 5% reserved space for root on ext3 partitions, this (as far as I am aware) doesn't serve any purpose on removable media.
Allow labels of FAT and NTFS partitions to be changed.

It should not:
Get into complex partitioning, people who want to can use GParted for that.
Get into setting partition flags.
What else shouldn't it do?

Anyone interested in trying to put something like this together.  All the tools exist (and are installed by default), we just need a well made GUI for them.

---

### Post by chrisccoulson on 2008-05-25
Some good points. My thoughts on them:
> Show currently connected removable media, mounted and otherwise.
Allow easy mounting and unmounting of media.
I don't think we need anything extra here. 'computer:///' shows everything that is accessible from the local machine (local filesystems, removable filesystems, network filesystems etc). It also allows for easy mounting and unmounting of removable media. Mounting of removable media should be completely transparent to the user anyway (the user plugs in their removable media, and it just works)

> Allow formatting/partitioning with FAT, NTFS or EXT2/3
I agree we definately need something here. Although I'm not sure it would need to be a separate tool. It could be achieved by extending something like gfloppy, or adding an option in the right-click menu in Nautilus (allowing you to right-click the media icon in computer:/// and selecting Format)

> Solve the permission issue created when using ext2/3, so if a user formats their USB drive with ext2/3, they can actually write to it by default
I haven't used ext2/3 on removable media, so I can't comment on that.

> Should also possibly remove the 5% reserved space for root on ext3 partitions, this (as far as I am aware) doesn't serve any purpose on removable media
I agree that the 5% reserved space is useless for removable media. That could be something which could be handled by the tool that formats and creates the filesystem in the first place.

> Allow labels of FAT and NTFS partitions to be changed.

We shouldn't need a separate tool for that. We should be able to change labels by right-clicking on the media icons in computer:/// I think

---

### Post by stadt on 2008-05-25
To be complete the GUI should support DVD-RAM too, e.g. with UDF-formatting

Okay there is the KDVD-Ram Tool, but it's not in the repositories and it's not Gtk. 

No I don't have anything against KDE.

---

### Post by musther on 2008-05-25
> **chrisccoulson said:**
> 
I don't think we need anything extra here. 'computer:///' shows everything that is accessible from the local machine (local filesystems, removable filesystems, network filesystems etc). It also allows for easy mounting and unmounting of removable media. Mounting of removable media should be completely transparent to the user anyway (the user plugs in their removable media, and it just works)

I was under the impression that if something isn't mounted, it's not visible in computer:///, but it turns out I'm wrong as I just tried it.  What about something which currently has no recognised filesystem on it, or one which is damaged, which is therefore going to need (re)partitioning and formatting?

> **chrisccoulson said:**
> I agree we definately need something here. Although I'm not sure it would need to be a separate tool. It could be achieved by extending something like gfloppy, or adding an option in the right-click menu in Nautilus (allowing you to right-click the media icon in computer:/// and selecting Format)

I agree, if we can include this functionality purely in computer:/// that would be great.

---

### Post by musther on 2008-05-25
Yep, just checked, drives with no partition are still shown in computer:///, but it's pretty useless as it is, you just get a "can't mount file" message.

---

### Post by smartboyathome on 2008-05-25
You should suggest this to Nautilus.

---

### Post by Gina on 2008-05-26
I certainly think labelling should be available in the standard GUI.  It would help if it was included in GParted as a second choice.  As it is, you need to install a command line app to label a partition or removable media.

I'm not sure formatting HDs should be available too easily - in any case it should be an admin task and not available to non-admin user accounts.

Currently with Hardy, partitions are not mounted automatically unless you add them by hand to fstab - not a newbie-friendly process.  I believe this should be rectified.

No space should be reserved by default on devices that don't need it.

---

### Post by chrisccoulson on 2008-05-26
> **Gina said:**
> I certainly think labelling should be available in the standard GUI.  It would help if it was included in GParted as a second choice.  As it is, you need to install a command line app to label a partition or removable media.

I'm not sure formatting HDs should be available too easily - in any case it should be an admin task and not available to non-admin user accounts.

Currently with Hardy, partitions are not mounted automatically unless you add them by hand to fstab - not a newbie-friendly process.  I believe this should be rectified.

No space should be reserved by default on devices that don't need it.

Formatting internal disks should be an administrator task, but any user should be able to format an external USB pen drive or an external disk

---

### Post by musther on 2008-05-26
Currently, formatting anything (USB disks included) is an admin task, because it uses the same system.  Allow non-admins to format USB drives might be a good idea for everyday multiuser systems, but maybe we'd need an option for them to be admin-protected?

---

