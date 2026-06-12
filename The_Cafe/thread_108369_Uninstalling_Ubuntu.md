---
title: "Uninstalling Ubuntu"
date: 2005-12-25
forum: The Cafe
---

### Post by Fallen2 on 2005-12-25
May I please have the STEP-By-STEP instructions on uninstalling Ubuntu?  Thank you very much.  And Merry Christmas!

---

### Post by Adrenal on 2005-12-25
Just format the partition back to ntfs or fat32 or whatver it is you crazy kids are using these days

---

### Post by Fallen2 on 2005-12-25
[QUOTE=Adrenal]Just format the partition back to ntfs or fat32 or whatver it is you crazy kids are using these days[/QUOTE]

How do I format them though.  that's what Idon't understand how to do.

---

### Post by anil_robo on 2005-12-25
First of all, let me advise you to back up all important data before you go ahead with deleting any OS from your hard disk. Grab some blank CD/DVDs and burn all important stuff to them.

To delete Ubuntu from your hard disk, you will need the following things:

0. Ubuntu/Knoppix live CD for rescue, just in case if you screw up everything!
1. Install CD of any OS (to delete ubuntu partition)
2. Boot floppies and CDs of another OS (to replace Ubuntu)
3. Make sure the boot floppies and CDs of "another OS" have fdisk on them.

The best way to uninstall Ubuntu is to format the partition where Ubuntu lies. But be aware that if you have other OS installed, they'll be gone because GRUB won't find Ubuntu and it'll refuse to boot your system, spitting an error message.

If you want to delete all operating systems from the hard disk, you can safely use any OS installation disk to delete all partitions, create new partitions for the new OS, and install the new OS on them.

Do you have another OS installed on your system with Ubuntu? If yes, do you want to keep it? If you want to uninstall just Ubuntu and keep the other one (I guess it's windows), you should have a boot CD/floppy ready for the other system. For example, if you have windows and you want to keep it, you should have its bootdisk ready.

GO ahead and delete the partition where Ubuntu lies (you can use XP install/boot cd to do this) - just delete the ubuntu partition, and create a new one in its place. But don't install windows on it - simply power off your computer after making and formatting a new partition in ubuntu's place.

When you reboot, wait and watch - most likely GRUB will fail. If it's the case, simply pop in your XP boot **FLOPPIES**, and choose REPAIR a previous windows installation, and type ```
fdisk /mbr
``` 
You'll be done.

---

### Post by Fallen2 on 2005-12-25
I don't know what a boot floppies are?  Do they come with the computer when you first purchase it?  If they do mine didn't.

---

### Post by Fallen2 on 2005-12-25
Here's is screen shot of my desktop with disk information.  It shows 4 other un-used hard disks.  Is it possible to install windows xp in one of them?

---

### Post by zenwhen on 2005-12-25
You only have Ubuntu installed. What you need to do now is install Windows, which will surely do the trick as far as "uninstalling Ubuntu" goes. No Ubuntu or Linux related information is needed at this point and this should not have been posted in community chat to begin with. 

Since this is a support thread and it does not meet the criteria for any of our support categories, I will now close it.

---

