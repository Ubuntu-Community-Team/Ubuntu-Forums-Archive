---
title: "Unable to delete/repartition hard disk during install"
date: 2012-08-15
forum: Server Platforms
---

### Post by drewbuntu2 on 2012-08-15
I've been having some problems installing Ubuntu 12.04 64 bit server edition on my new machine.  In the process of experimenting towards resolving various problems I installed Ubuntu on hard disk 4.  In the end I want to set up a RAID 5 configuration on four disks, but installing it on just one seemed to be the logical step in diagnosing and resolving another problem (which turned out not to be RAID related anyway.)

Long story short, having now resolved the old problem I want to install onto my RAID 5 configuration.  Now when I attempt the installation from the bootable CD, I make it through initial steps to the 'Partition disks' step.  I choose  the Manual option.  I then see my four disks come up (denoted as SCSI devices,) as well as two LVM devices, 'root' and 'swap,' apparently left over from my last installation.  When I go through my disks trying to create new partition tables I run into a problem only on disk 4.  When I select on disk 4 the screen turns red and a dialog box pops up saying:

"Partition in use
No modifications can be made to the partition #5 of device SCSI4 (0,0,0) (sdd) for the following reasons:

In use by LVM volume group myservermachine"

So how do I get rid of this partition and make Ubuntu treat the disk like all the rest in my intended RAID array?  Is there a way to do this from inside the Ubuntu install program?  If not what's the simplest way of taking care of this? Maybe downloading a bootable DOS image and trying to reformat the disk from within DOS?

Many thanks for any suggestions!

---

### Post by LHammonds on 2012-08-17
In the past, I have been able to wipe out prior installs by selecting "manual" and then deleting the partitions.

LHammonds

---

### Post by Tobeus on 2012-08-17
Ok, so I've been through this myself, so I'll see if I can pay it forward.  Two solutions come to mind immediately:

1.  Download Darik's Boot and Nuke, DBAN iso from [www.dban.org](www.dban.org) and burn it to disk.  Boot to the disk and wipe the drive by hand.  This should destroy any remnants of your old install.  BE CAREFUL!  If you leave the cd to boot and don't interrupt the process I think it goes into "oh, so you want to destroy everything mode?"  Stay at the keyboard so you can tell it which drive to wipe.  I like to unplug all but the drive I'm going to wipe to make sure I don't mess anything up.

2.  Boot into the Ubuntu installer and choose to manually configure the drives.  Then you have to remove any logical volumes and then delete any volume groups that encompass the drive.  I can't remember the exact terminology, but you should be able to google the exact procedure, or perhaps one of the LVM gurus will take over for me on this one.

Given that you want to re-purpose the drive, I would just DBAN it and move on, but it is up to you.  I found it interesting learning how LVM works back then, but you see how much of it has remained in my head.  :)

Good luck!

-Tobeus

---

### Post by Bucky Ball on 2012-08-17
Be _***VERY***_ careful with DBan. ;)

---

### Post by SJR Dorset on 2012-08-17
Trying using the live version of GParted:

[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

### Post by Bucky Ball on 2012-08-17
> **SJR Dorset said:**
> Trying using the live version of GParted:

[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

+1. Try that way first. Boot from a LiveCD (the install CD) and launch Gparted. Right click on the partitions in question and unmount if they're not already. Delete. If that doesn't work, go for something more drastic. 

You can also download the bootable Gparted ISO from the link provided by SJR Dorset.

---

### Post by darkod on 2012-08-17
I think something similar happened to me in one VBox test install. Out of what ever reason, the swap LV of the LVM seem to be mounted automatically when starting the install process. Maybe the point is to have faster install process using the swap only the problem is what if you want to delete that partition. :)

For swap you don't use the umount command, so try something like swapoff, with and without entering the LV after that. So, something like:
```
swapoff
swapoff /dev/VGroupName/LVName
```

You can switch to a new terminal during the server install with Ctrl+Alt+F2. Do that immediately after the server install process starts, unmount swap, and then continue the install and in the partitioning stage it should allow you to delete any partitions.

Not sure if you needed to delete the LVs and VG before, in which case it might be easier booting the server with the standard desktop live CD, destroy the LVM, and then boot with the server cd and install.

---

