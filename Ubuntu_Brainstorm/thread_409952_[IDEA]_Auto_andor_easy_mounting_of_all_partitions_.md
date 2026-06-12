---
title: "[IDEA]: Auto and/or easy mounting of all partitions and drives"
date: 2007-04-15
forum: Ubuntu Brainstorm
---

### Post by aysiu on 2007-04-15
**Summary:**
Full graphical (and, in most cases, double-click) configuration of mounting of partitions and drives (both internal and external). Right now external drives seem to automount okay, and internal drives automount okay if they are unchanged since when Ubuntu was installed. But any changes make things more complicated.

**Rationale:**
A lot of mounting options are either not readily apparent to new users or require the manual editing of configuration files or the terminal.

**Scope and Use Cases:**
A relatively new Ubuntu user has finally made the full switchover and wants to get rid of the Windows partition on her dual boot. She deletes the Windows partition with GParted and creates a new Ext3 partition. She then has to post in the forums or do a Google search to find out how to use that new Ext3 partition. As far as I know, this involves creating a mount point manually, editing the /etc/fstab file to add a new entry, and then *chown*ing the new partition and possibly *chmod*ing it, too, to make it useful to the user. Wouldn't it be great if she could just see it as an available drive in the sidebar in Nautilus and then click on it. When she clicks on it, it mounts with read-only permissions? With a simple right-click on the drive icon, she can make it read/write.

A month after installing a dual-boot with Windows, Mina installs a new internal hard drive and formats it as FAT32. Ubuntu doesn't recognize the drive, of course. So she then has to make a mount point and manually edit the /etc/fstab and then *sudo mount -a* to use the partition in Ubuntu. Windows auto-detects the drive and makes it appear as E:\. Wouldn't it be great if the new drive would just appear in Ubuntu the way an external one would?

Bjorn has an NTFS drive (his Windows partition) in a dual-boot. When he installed Ubuntu, it was read-only. In order to make it read/write, he has to follow some long tutorial and copy and paste a lot of commands. Wouldn't it be great if he could just right-click the drive icon in the Nautilus side-bar and enable read/write mode, with a warning that he has to install NTFS-3G?

**Implementation Plan:**
I don't know what's involved, but you don't get very many people asking how to mount and view drives in Knoppix. It's pretty darn obvious. That's how it should be in Ubuntu, too.

**Blueprints**:
[https://blueprints.launchpad.net/ubuntu/+spec/auto-partition-detect](https://blueprints.launchpad.net/ubuntu/+spec/auto-partition-detect)
[https://blueprints.launchpad.net/ubuntu/+spec/mount-windows-partition-seamlessly](https://blueprints.launchpad.net/ubuntu/+spec/mount-windows-partition-seamlessly)
[https://blueprints.launchpad.net/ubuntu/+spec/useful-disks-manager-applet](https://blueprints.launchpad.net/ubuntu/+spec/useful-disks-manager-applet)

---

### Post by .t. on 2007-04-15
This spec has been around for a while, and Launchpad claims it is implemented: [https://blueprints.launchpad.net/ubuntu/+spec/mount-all-local-filesystems](https://blueprints.launchpad.net/ubuntu/+spec/mount-all-local-filesystems)

I don't have any other partitions than those detected by Ubuntu at installation, as my hard drive consists only of Ubuntu data. External devices seem to work quite well.

---

### Post by =0verlord= on 2007-04-15
This is great and hopefully addresses my old nemesis: determing WHICH device is the drive I'm trying to access.  And no, I don't really have anything to help with that :). 

*waves at aysiu*
I seem to be following you around ;)

---

### Post by PriceChild on 2007-04-16
Gnome's disk admin that disappeared soon after Dapper is I think what we're after? Needing an extra option to save to /etc/fstab I suppose.

It broke for various reasons and I'm not totally sure but I think work needs to be done on it at Gnome's end to fix/re-write things with new technologies.

---

### Post by finalbeta on 2007-04-16
I agree, I have internal HD racks on some PC's. Would be nice to insert the disk and have the data available. 
Like .t. said, there is a spec implemented that should do this. But at least for me, it doesn't work.

---

### Post by lolocaust on 2007-04-18
**Summary:**
Provide a GUI for mounting disks in a user specified path, as well as an option to have it mount on every boot (via fstab) and a way to mount image files.

**Rationale:**
Power users migrating from windows to linux who have their data on seperate partitions may like to choose how they are mounted, but do not know how to do it on the command line. Same with any CD image files they may have, although these probably shouldn't stay for longer than the session.

**Implementation Plan:**
Not entirely sure, but it should just be a GUI frontend to read/write to /etc/fstab, and a frontend to the command line utilities.

**Notes**
I'm sure there used to be a tool similar to this in a previous version (I can't find it in edgy), except that it wasn't possible to save to fstab, and anything that was mounted was for the current session only.

Also, during install, if you decide to manually edit the partition table, the installer lets you specify the mount points for the partitions it detects. This is similar to what I suggest except that there should be a way to access it from within the system itself.

---

### Post by aysiu on 2007-04-18
I've merged this with the other, similar thread.

---

### Post by brentcore on 2007-04-18
aysiu:

It's already been implemented!  When my external hard drive is plugged in but not mounted, it appears in the left pane of nautilus as "disk".  When I double click it, it automounts, changes it's name to "USB Disk" and then opens the top directory in the nautilus window.  Very slick!  Try it out, I guess you missed it :)

---

### Post by aysiu on 2007-04-18
> **brentcore said:**
> aysiu:

It's already been implemented!  When my external hard drive is plugged in but not mounted, it appears in the left pane of nautilus as "disk".  When I double click it, it automounts, changes it's name to "USB Disk" and then opens the top directory in the nautilus window.  Very slick!  Try it out, I guess you missed it :)
I'm not talking about external hard drives. Read the second sentence of the first post.

---

### Post by brentcore on 2007-04-18
> **aysiu said:**
> I'm not talking about external hard drives. Read the second sentence of the first post.

Oh sorry, I wasn't being clear :)

I believe this works not only with external hard drives, but anything recognized by fdisk -l .   I just deleted my fedora partition, so I can test it out right now, but I do remember this behavior with internal partitions as well (I'm not sure why nautilus would care if it's an internal harddrive's partition or an external harddrive's partition anyway, it exhibits this behavior either way IIRC).  Seriously, give it a try! :D

---

### Post by sicofante on 2007-04-26
I was researching about GUIs for this mounting issue when I stumbled upon this idea. I second it wholeheartedly.

I would suggest just adding mounting capabilities to Gparted. Just right-click on a partition and choose "Mount..." menu entry (or select partition and choose "Mount..." from the appropriate pull-down menu). Then choose mounting options from a comprehensive dialogue box.

(And while they're at it, they might as well change the name from Gparted to "Disk Manager" or anything without a 'G' in front of it...)

EDIT: Just a few minutes after posting, I found this: [http://flomertens.free.fr/disk-manager/features.html](http://flomertens.free.fr/disk-manager/features.html). They have called it "Disk Manager". Funny. :-) (I still believe some of the functionality in that nice app should be part of Gparted as described.)

---

### Post by Justy on 2007-05-17
When I'm using Live CD, fstab does not automatically mounts mountable devices. Such as my harddisk's ntfs partitation. In addition to this, when not using live cd, ubuntu doesnt automatically mounts some devices OR partitations.
A solution to that small usability hardness, i think there could be a GUI for this. 

By that user will be able to;
- Mount any partitation or device in the list shown on the screen
- Unmount any partitation or device mounted previously.

Wouldn't that just be great huh?
What you say guys?

~Justy

---

### Post by blazercist on 2007-05-17
sudo fdisk -l

this will give you a list of mountable devices.

then just sudo mount /dev/<device>  /media/<device>

---

### Post by Justy on 2007-05-17
Of course that command will list it.
But ubuntu must have a diffrence from other distros.
Wouldn't a GUI be awesome ?

---

### Post by blazercist on 2007-05-17
The reason its not automatically mount for you most likely is because that partition is NTFS.... you need to install ntfs-3g and  ntfs-config and configure it before it will automount.

---

### Post by Justy on 2007-05-17
Well i know all of them i dont mean them =)
What i am telling is, if there would be a  Graphical User Interface, you dont need terminal and commands ? do you!?

I think i am misunderstood .. This was just an idea ..

~Justy

---

### Post by aysiu on 2007-05-17
I suggested this a while ago. I've merged your thread with the earlier one. I've also linked to existing blueprints on the issue.

---

