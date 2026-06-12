---
title: "Mdadm add a few disks"
date: 2015-02-06
forum: Server Platforms
---

### Post by adamjseed on 2015-02-06
Hi, 

I have used mdadm for a while now and fairly comfortable with it but I need to go my array and have the following questions:

1) Is it possible to add, say 3 disks to a raid-5 MDADM array and grow it one go? 
2) Should I use a backup file during the process? does that get large?
3) What kinda time will it take to grow a 4x4tb raid-5 to 7x4tb raid-5 (currently the 4x4 is full) 
4) And finally can it be rebuilt while still having access to the data? 


Thanks

---

### Post by kpatz on 2015-02-06
1.  Yes it's possible.  The array will have to rebuild itself with the new disks added.  Note that after adding the disks and rebuilding the array, you'll have to resize your partitions or volumes if you're using LVM to utilize the added space.
2.  It's always a good idea to back up your data before making changes to the array, in case something goes wrong, so you don't lose your data.
3.  It'll take a while, depending on the speed of your drives and hardware.  As much as a few days.
4.  Yes, you should still be able to access the data already on the array while it's rebuilding, but it'll be a lot slower since all the disks are going to be read and rewritten.

You might want to consider using RAID 6 instead of 5, reserving 2 disks for parity, since the odds of having more than one drive fail increases as you add more drives to the array.

Another option is to keep your 4x4 array as it is, and make a new 4x3 array with the new drives, and (assuming you're using LVM) expand the volume across the new array.  Then if something happens, you shouldn't lose anything on the 4x4 array.

---

