---
title: "raid5 repair partition table"
date: 2011-02-27
forum: Server Platforms
---

### Post by PW-toXic on 2011-02-27
I have done a big fault.
I opened GParted to create a new partition on a new drive. He wanted me to create a partition table first which I did, and it was created directly without any prompt like im used to see when creating partition. 
So I recognized too late, that i actually created a MBR on one of my 6 1TB raid5 drives.
Not beeing sure if the ne MBR was really written, I have opened ubuntu disk utility and clicked on the check raid button. It directly made a resync.
After the resync, mdadm --detail /dev/md0 told me everything is ok and synced. Then I wanted to mount it with:
mount /dev/md0 /mnt
Then I get the following error:
"mount: wrong fs type, bad option, bad superblock on /dev/md0, 
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so"
I think I just killed my raid5 ;(

I shouldnt work on my server when im tired and when I actually have no time ;(
My last hope is the fact, that "Disk Utility" shows that there is a .0 TB ext4 volume on my raid (see screen below)
[http://files.webthesia.de/raid5.jpg](http://files.webthesia.de/raid5.jpg)

I hope someone can rescue my raid5..

---

### Post by PW-toXic on 2011-02-27
[http://serverfault.com/questions/168046/failed-mdadm-array-with-ext-4-partition-e2fsck-unable-to-set-superblock-flags](http://serverfault.com/questions/168046/failed-mdadm-array-with-ext-4-partition-e2fsck-unable-to-set-superblock-flags)

I have done this, and the same happens - no solution ;(

---

### Post by YesWeCan on 2011-02-27
Don't panic!
If you have just messed up 1 drive then you can rebuild the RAID 5 array, at least in theory.

Would you post the output of:
cat /proc/mdstat
cat /etc/mdadm/mdadm.conf
sudo mdadm --detail /dev/md0

---

### Post by PW-toXic on 2011-02-27
all drives are synced (mdadm --detail).
Finally I got an fsck to run trhough and it found a LOT of errors, but for now i can mount it, and i couldnt find one corrupted file till now. Lets soo how much is damaged.

---

### Post by Vegan on 2011-02-27
Good to see, I have warned users often, hope you have a backup

---

### Post by PW-toXic on 2011-03-02
No I dont have a backup of most of those files, because 5TB is just too much to backup. I only have backups of the most important things.

---

