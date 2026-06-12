---
title: "Accidently ran pvcreate or lvm on existing luks drive"
date: 2012-03-10
forum: Security
---

### Post by bababooey on 2012-03-10
I have a encrypted external usb drive, encrypted using luks, or cryptsetup. Made a huge mistake of running lvm apps possible pvcreate, pvchange, thinking I was working on another drive(recovering a lvm/luks drive at the time, but the drive Im having problems with, is just a luks encrypted drive no lvm intended to be setup)

One good thing is the luks header is still on the drive, I did a luksDump and my keys are there, I can unlock the drive too. I just cant mount it. Using blkid, when the drive is unlocked,  i noticed that the mapper device for the partition, is not showing the TYPE=ext3 but showing  TYPE="LVM2_member"  now. So when I mount the mapper for the drive, it says mount: unknown filesystem type 'LVM2_member'
 
Another positive thing is that i used the -f or fake switch and can see the drive still has data, and i think its a matter of changing the way my oneiric system sees the drive. What can I try to do to change the type back to crypto_Luks without data loss because it does have data, lots of almost 100% used. Using mount -f to do a fake mount, i can see the partition properties and its accurate. Although I have a few ways I think I could fix it, I rather ask the ubuntu comminity for help to prevent another error again. 

Also just to add, my fdisk shows the drive properties, no problems there.

---

### Post by bababooey on 2012-03-11
Is there a way to remove the way it sees the luks encrypted drive back to luks and not LVM2_Member?  I did some digging and it might be possible to use blkid itself to change the type to luks, but then again im not clear if it will fix how the system sees the drive. I dont have another drive available with 750g free space to make a img just in case something goes wrong. Is it even possible to remove lvm properties if I created a lvm PV volume on accident? I know that for sure theres no  logical volumes. Since the drive only has 1 partition, and in fdisk its still showing that 1 partition as a ext3. So that sounds promosing to repair. Anyone been through such a situation without wrecking the luks header? I mean I can back it up, but I have no clue how to remove the pv safely

---

