---
title: "hard drive partion"
date: 2011-07-22
forum: System76 Support
---

### Post by shubham1 on 2011-07-22
i have a 500gb hdd in system running ubuntu linux i have to manage partions using gparted.
i have my 170gb ,90gb , 101mb harddrive unusable i have make 170 gb usable how can i create an extended partion aslo how can i combine partion.
rest all will be cleared by the image.

---

### Post by vanadium on 2011-07-22
You already have an extended partition, /dev/sda3. It contains your root partition, dsa4, and your "workspace" partition, sda5.

To "recover" the unused 93 GB, you could expand your existing ntfs partition, or you could create an additional partition in that space.

Other changes, such as moving extended and root partitions in front to occupy that 93 GB could work, but involve moving partitions, which will take a long time but also might be a bit risky.

---

### Post by oldfred on 2011-07-22
It actually looks like you only have swap which is not shown as sda5 in the extended partition. You cannot add any more primary partitions but can move the left side of the current extended to include all the unallocated. And then you can create any number of logical partitions in the unallocated space that is inside the extended partition.

I might suggest shrinking the windows partition and creating a shared NTFS partition for any data you want to share with Windows & Ubuntu. Windows does not like a lot of writing into its system partition from foreign systems.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

The little keys say the partitions are mounted. You have to use a liveCD and even then have to click on the swap partition and right click swap off to unmount it. LiveCDs often use a swap if found to speed things up but then you cannot use gparted with swap mounted.

---

### Post by shubham1 on 2011-07-22
i dont want to share with windows i have no windows in my system only folders are there i want to join the 90gb and 101mb partion and create a extended partion.

---

### Post by oldfred on 2011-07-22
You already have the extended and cannot have two extended partitions. Just expand the extended into the unallocated with gparted from the liveCD. You do have to swapoff the swap partition.

The 101MB may not be worth the effort to use. You can move a partition left, but it will copy & verify all data. If you have a lot of data in the partition it can take all night. If you interrupt a move like that then you destroy all your data.

---

### Post by vanadium on 2011-07-23
* The "extended" partition is only 4 GB and not used.
* I do not see a swap partition

You could delete the ntfs partition sda2 (making sure you have a good backup of the data on another medium). Then delete the extended partition sda3 (there is currently no logical partition nor data nor room for that in that extended partition).

This will free up all the space before sda4.

In the free space, create an extended partition.
In the extended partition, you can create one big ext4 data partition. If you care, you could add a 3 to 4 gigabyte swap partition into that extended partition as well.

A much more risky and slower procedure: delete all partitions as above, move sda4 to the front, move sda1 to the front, then do whatever you like with the free space at the end of the disk (create new partitions/expand workspace, ....). However, I quote oldfred in his previous post: "You can move a partition left, but it will copy & verify all data. If you have a lot of data in the partition it can take all night. If you interrupt a move like that then you destroy all your data. "

---

### Post by shubham1 on 2011-07-23
g parted does not allow me to delete the partions execpt workspace i cant create a exetended partion which live cd are you talking about.

---

### Post by vanadium on 2011-07-23
Write clearly. Consider we are not sitting on your system. Thus, we need all information from your posts.

Partitions can only be manipulated if they are not in use. Eventually, they must be unmounted first.

A liveCD is a CD from which you can boot a linux system. The Ubuntu installation CD is a live CD. Using a live CD, you are not running the system from your hard drive. Thus, your partitions are unused or at least can be unmounted, and be manipulated.

---

### Post by oldfred on 2011-07-23
I think the screen shot did not show the sda5 swap partition (it was just below as window was not large enough) but the display of the extended partition was typical of a swap inside the extended.

You have to use a liveCD so partitions are not mounted. But you still have to click on the swap partition and right click swapoff to unmount the swap partition.

---

### Post by shubham1 on 2011-07-24
i have done dual boot in windows and linux with usb drive first time it was hanged and my all partion in windows execpt c: was lost with there data 2nd time my linux was installed and my windows was lost but files were there but linux has too many problems so i reinstalled it.i dont have the usb drive right now from which i have done partion.

---

### Post by shubham1 on 2011-07-24
what does unmount mean what will it do.it is risky will there will be data loss.

---

### Post by shubham1 on 2011-07-24
what does unmount mean what will it do.

---

### Post by oldfred on 2011-07-24
If it is a removed-able drive like a USB and you do not unmount it, then you may have damage.

Windows also requires you to "safely remove", but they do not call it unmount. My XP has even popped up a window when I pulled out a flash drive without telling windows telling me to use software to turn it off first.

The computer checks that it has completed all writing activity and the file system is save to remove or unmount from system. If in the middle of doing something then you only have part of some data writing and that can damage the entire drive.

Even non removeable drives can have file errors from abnormal shutdowns. Windows uses chkdsk and Linux ext formats use e2fsck to repair if possible. Best to always shutdown normally.

---

### Post by shubham1 on 2011-07-25
my system is not shutting or hibernating normally.hibernate is very important for me and ok i understood it.i will remove windows file and copy the data then unmount but then  will i will be able to join the partions.

---

