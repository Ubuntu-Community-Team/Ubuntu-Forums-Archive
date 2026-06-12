---
title: "Read Only Disk - Cannot Delete"
date: 2009-01-04
forum: Security
---

### Post by measekite on 2009-01-04
I booted Intrepid 8.10 Live CD. I attempted to create a USB boot drive according to the instructions in the dialog of the Live CD.  It Failed!

Now I want to delete whatever is left on the Lexar USB stick drive.  It mounts OK.  I went to a folder and clicked delete.  I received a permissions error.

I then rt clicked on the folder.  Choose the Permissions Tab.  And tried to change the folder permissions.  It said I did not have permission and yet I was listed as an owner.

I then went to terminal and tried gksu and choose nautilus and the file manger came up under root.  I then went and tried to change the permission and was denied.  The system said it was a read only disk.

I would like to reclaim the space.  How can I get rid of these unwanted files?

---

### Post by cdenley on 2009-01-05
If for whatever reason you cannot mount the filesystem as writable, you should be able to reformat it.
System>Administration>Partition Editor
Are you sure you didn't flip a small switch on the side of the drive?

---

### Post by measekite on 2009-01-05
> **cdenley said:**
> If for whatever reason you cannot mount the filesystem as writable, you should be able to reformat it.
System>Administration>Partition Editor
Are you sure you didn't flip a small switch on the side of the drive?

I manage to use Gparted and reformatted in fat32  the USB flash drive.  It gave the name of Label.  I could then copy files to it and delete it BUT
I could not change the disk label from disk to Lexar.

I did solve that problem but should not have had to do what I did.

I went to Win2k after the format in Ubuntu.  At first I could not write to the drive or do anything but I was persistent and finally it came up under Disk Manager in windows.  I then reformatted the drive under fat32 and was able to choose the disk label I wanted (Lexar) and could read and write to it in Windows.  I then tested it in Ubuntu and all was well.

First I do not understand why I was not able to change the disk label in Gparted.   The box for changing that under properties was READ ONLY and could not be changed but under Windows I could change it.

Then I do not understand why I could not change the permissions using nautilus other than the fact that fat32 is a problem in Linux.
[B]
If that is the case how can one ever ditch Windows if they need it occassionally to perform these tasks.[/B]

And you have to use fat32 to get the most out of a flash drive so you can use it on most any computer and we do live in a Windows world.  If 95% of the computers could read and write ext3 then I would not have a problem.

Does anybody know if I would have used the command line I could have solved the problems or is the command line method for changing permission has the same restrictions as nautilus?

---

### Post by cariboo on 2009-01-05
You probably couldn't change the device label, because it was still mounted. When you want o make any changes using gparted, you have to umount the device first.

Jim

---

