---
title: "Luks-Lvm Partition Gone"
date: 2010-02-23
forum: Server Platforms
---

### Post by ztripez on 2010-02-23
Ok,
Here is my Setup:

Drives:
/dev/sda  160 Gb
/dev/sdb  1 Tb
/dev/sdc  1.5 Tb
/dev/sdd  1.5 Tb
/dev/sde  200 Gb

Partitions:
/sda1  154 Gb Ext4 (/ /boot etc)
/sda5  6 Gb  Swap
/sdb1  1 Tb LUKS -> mapped to /mapper/sdb1_crypted
/sdc1  (Should be) 1.5 Tb LUKS -> mapped to /mapper/sdc1_crypted
/sdd1  1.5 LUKS -> mapped to /mapper/sdd1_crypted
/sde1 200 Gb LUKS -> mapped to /mapper/sde1_crypted

LVM
PV:
/mapper/sdb1_crypted
/mapper/sdc1_crypted
/mapper/sdd1_crypted
/mapper/sde1_crypted

LV
/storage/home 180 Gb Ext4
/storage/Fatty  [theRest] Gb Ext4



Ok, so i had a uncrypted LVM Group with all drives in them, but since my company has started to handle more sensitive data I decided to chage to a LUKS-LVM solution instead.

Here how i did it.
1. I started to remove all uncesseary data from the old LVM. 

2. After i cleaned up enough space I removed one of the drives from LVM,

4. Random data write and created an partition (unformated).

5. Cryptsetup luksFormat

6. Added it back to the LVM with pv create.

7. I created a new LV group an added the new crypted pv.

8. Formated it as Ext4.

No problem there worked at like a charm. I repeated the task for all drives, but instead creating a new LV i extended it and instad of removing data i moved over to the crypted LV.

All drives was scrambled,crypted and added to the LVM, and I know it all worked (i trippelchecked like four times (yeah thats 3*4 ;P))..

..until i had to reboot, for some reason the LV never got mounted.
Ok i probly added the wrong key file in crypttab. But no there was the right one.
That when i realised that the system hadn't found my /dev/sdc1 partion, a 1.5 Tb crypted partion that is gone.
I tried to reboot, but no the partition didn't show up.

Guys, I'm in panic mode.. what to do?

It's almost 4Tb of data gone....


I'm doing a Testdiskt atm, hope it will tell me something.
Got a message about
"Partition sector doesn't have the endmark 0xAA55."

I've google it but what i can tell that errormessage is about a broken MBR on FAT partitions....



Please Help!

---

### Post by ztripez on 2010-02-24
Oboy what a lucky guy I am.


By folowing this guide: [http://www.novell.com/coolsolutions/appnote/19386.html](http://www.novell.com/coolsolutions/appnote/19386.html)

I was hoping to save some of the files from the LV
I reformated the sdc drive as a Luks.. added it to the pv with the same UUID as the lost drive.
Did a vgscan
and a filesystem check on the LV

and

TADA!

EVERYTHING was back!

Omygood i'm  a happy camper now ;P

---

