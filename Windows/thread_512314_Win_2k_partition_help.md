---
title: "Win 2k partition help"
date: 2007-07-29
forum: Windows
---

### Post by goumples on 2007-07-29
I got a service call from a relative with a win 2k box.  The previous owner played with the drive a bit and now the drive is divided into a primary partition, and a few gigs of free space.. how do i go about merging the free space with the primary partition so that its usable?

edit: and without using a program such as "partition magic" that I'd have to pay for..

---

### Post by GarlicFish on 2007-07-29
First make a good backup of your win2k box ;-)
Next I suggest practicing by setting up a vmware or similar virtual machine with win2k.
This procedure is a bit brown trousers if you are unfamiliar with the commands!

read up on fdisk and ntfsresize
[http://man.linux-ntfs.org/ntfsresize.8.html](http://man.linux-ntfs.org/ntfsresize.8.html)

Boot up an ubuntu liveCD

launch a terminal

first you need to extend the partition table using fdisk
find out what disks you need to alter e.g. hda or sda.
use "cat /proc/partitions" to list the disks and partitions

read the man pages for fdisk!
if its the first pata disk:
fdisk /dev/hda

type p to print out the current partition table
Write down or screenshot the data here in case you hit the wrong key!
this will only work if there is free space after the ntfs partition
delete the ntfs partition!
create a new partition starting at the same location
set the partition to use all of the remaining free space
make sure you set the partition type to 7 (NTFS/HPFS)
print the partition table again with p and double check that the win2k partition looks the same as before but bigger.
If you are absolutely sure, write the partition table to disk "w"
you may need to reboot at this point back to the liveCD if the kernel does not pick up the new partition table.
DO NOT REBOOT to WIN2K yet

check for the ntfsresize command
switch to root using "sudo su -"
if its not there, install it using "apt-get install ntfsprogs" 

now you can extend the NTFS filesystem 
if your w2k partition is /dev/hda1
ntfsresize /dev/hda1 --no-action
this will go through a dummy run to allow you to check for errors
if it all goes well, run
ntfsresize /dev/hda1

now you should be safe to reboot to win2k
Checkdisk will run automatically, let it complete.
If all is well, you should now have some extra disk space :-)

You can shrink partitions as well but it's a bit more tricky!

Good luck

---

### Post by GarlicFish on 2007-07-29
You should also look up the windows utility "diskpart" it's built in to w2k3 and XP but I think it may be available as a resource kit utility for w2k.
This can extend NTFS partitions from within windows and its free.

---

