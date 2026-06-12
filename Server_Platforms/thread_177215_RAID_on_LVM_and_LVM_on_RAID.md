---
title: "RAID on LVM and LVM on RAID"
date: 2006-05-15
forum: Server Platforms
---

### Post by Bubba Ho-Tep on 2006-05-15
I know that LVM on RAID (making LVM volumes from underlying disks that are in a raid array) can be done cos I've seen tutorials but can RAID on LVM be done?

I've a 320G drive I want to RAID1 and I want to use 
x1 160G and 
x2 80G 
drives which are in a LVM volume 

so I'm aiming for a config of having md0 which is made up of x1 IDE disk and x1 LVM vol 

I'm using:

sudo mdadm --create /dev/md0 -n2 -l1 /dev/mapper/vgmusic-lvmusic /dev/hdg

where vgmusic-lvmusic is the LVM vol (I know crap name I gave it) and hdg is the 320G 

I get 2 problems - 

mdadm can't open the LVM vol cos it's busy 
[tried a lazy umount of the LVM vol but this didn't work and get same error)

mdadm says hdg1 has an ext2 filesystem on it
[it doesn't cos I used cfdisk to make it type "FD" the ummm RAID autodetect thingo type. hdg1 is at present not mounted]

Does anyone know if it's just cos RAID on LVM straight up can't be done - or if it can be done and I'm just buggering it up?

BH-T

EDIT:repost from 'nother category

---

### Post by waster on 2006-05-16
I don't think this is possible. However, if you were using Sun's ZFS (wiki.ubuntu.com/ZFS), you would do little more than plug the new drive in.

You would have to reformat your disks to do LVM on RAID. With three disks of different sizes, you could have one RAID5 stripe set, one RAID0 or 1 pair, and one unmirrored area, although this is not at all optimal.

You could do a raid linear which would combined the 80 and 160 drives. you could then add software raid 1 using the linear array and the first 240GB of teh 320GB drive...

---

