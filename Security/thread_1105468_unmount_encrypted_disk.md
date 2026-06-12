---
title: "unmount encrypted disk"
date: 2009-03-24
forum: Security
---

### Post by darkhammer8108 on 2009-03-24
I am trying to make it so i have an encrypted removable hard disk.
I have it setup to not automatically mount the partition so i have to do it by hand. the problem is when i want to unmount it. 
```
$ sudo cryptdisks_start hemmar
 * Starting crypto disk...
 * hemmar (starting)
Enter passphrase to unlock the disk /dev/sdb1 (hemmar):
key slot 0 unlicked.
Command successful.
 * hemmar (started)

```
------ at this point the disk is added to /dev/mapper/ and i can mount the items in the volgroup and such. once i unmount everything in there i want to remove the device so if someone else comes along they have to enter the password too. -----
```
$ sudo cryptdisks_stop hemmar
 * Stopping crypto disk...
 * hemmar (busy)...

```
-----The device was never removed from /dev/mapper so anyone who can mount devices can just mount the items in the volgroup without a password.-----

how do i remove a device from the /dev/mapper?

---

### Post by darkhammer8108 on 2009-03-24
kinda figured out a work around here. it wasnt letting me unmount it because i was using lvm inside of it which i dont need for just 1 partition. i just reset it up as an encrypt ext3 partition. 
i would like to know what it takes to remove an lvm partition though. for instance if i was to mount my os disk that contains an encrypted lvm with my root and swap in it inside of a live cd. if i unmount the root partition and turn the swap off, how would i remove /dev/mapper/<volume> from there so i can do a cryptdisks_stop on the encrypted partition?

---

### Post by bodhi.zazen on 2009-03-24
You will have to copy the data and re-format the partition to remove the LVM. Then make a crypt w/o LVM.

---

### Post by darkhammer8108 on 2009-03-24
that doesnt really answer the question.
what i want is i boot up and sdb1 is unmounted
so i type cryptdisks_start hemmar and type in the pass phrase
this adds hemmar, hemmar-part1, and hemmar-part2 and to /dev/mapper.
i mount /dev/mapper/hemmar-part1. umount it. 
now i want to make it so i cant use anything on the disk without the password. so i type cryptdisks_stop hemmar but i get that hemmar is busy. im assuming there is another command in between unmount the volumes and unmapping the encrypted partition. i assume that it has to do with unmounting the volgroup on sdb1.

---

### Post by bodhi.zazen on 2009-03-24
Now I am not sure what you are asking. I thought you were asking about how to remove LVM, now it seems you are asking about how to manage LVM.

At any rate, see if some of the steps in this thread help you :

[ResizeEncryptedPartitions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ResizeEncryptedPartitions#preview") 

If you are wanting information on LVM, check out this link :

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

### Post by darkhammer8108 on 2009-03-24
when i do a cryptdisks_start it adds a device to /dev/mapper. 
i want to be able to run crypdisk_stop which removes this device from /dev/mapper. 

if i set it up so it is an encrpyted partition with ext3 inside it this works fine. 

problem arises when this is an LVM volgroup inside of an encrypted partition. 
so if i run the cryptdisks_start it adds the device to /dev/mapper, like normal, but it also adds the LVM volumes to /dev/mapper. im assuming this is why when i run cryptdisks_stop it tells me that the device is still busy. what i want to be able to do is run cryptdisks_stop on a system that has an LVM partition.

what i want to do is make it so when im done using the hard disk it requires a password to use it again which is why i encrypted the disk in the first place.

---

### Post by RansomStark on 2009-03-25
So, why don't you just use truecrypt to create an encrypted disk, which you can then just mount as and when you want it entering the passphrase at the time of mounting. An advantage with this is the device can be mounted in both Windows and Linux which can be useful if you're main system is ever unavailable.

---

### Post by darkhammer8108 on 2009-03-25
truecrypt looks like my best bet for my extra storage. i wanted to encrypt my root filesystem too though and that means i have to use two programs for the encryption since truecrypt can only encrypt windows system drives. i guess ill use an ecrypted LVM for my root system and truecrypt for my extra storage since there is no way i would be unmounting my root system anyways.

---

### Post by darkhammer8108 on 2009-03-25
figured out what i was trying to do. i had to deactivate the LVM to stop the encrypted partition. 
Process:
umount <all mounts from disk>
vgchange -a n <volgroup name>
cryptdisks_stop <encrypted partition>

---

