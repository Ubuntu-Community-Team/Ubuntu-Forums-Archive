---
title: "RAID-5 and LVM (and LVM recovery)"
date: 2009-06-11
forum: Server Platforms
---

### Post by capnjim on 2009-06-11
I currently have a 3TB non-RAID LVM system, and of course the worst has happen, the primary drive in the LVM group has started to fail. Fortunately I can still access the disk to pull data off, and have the LVM metadata backed up.

So, having confirmed my suspicion I was being an idiot using LVM without RAID, my plan now is to rebuild using LVM over RAID-5. This will be my first RAID setup, and I have a few questions.

I have available to hand 2 x 1.5TB HDD's, 1 x 1TB HDD, and 1 x 750GB HDD. I understand that the capacity of a RAID-5 system will be equal to (n-1) * S where S is the capacity of the smallest drive in the array. I also saw somewhere that when building a software RAID system that one does not so much build it on HDD's, but across partitions. So I was thinking, if I paritioned the drives so that they form a group of 8 x 750GB partitions (and leave the extra 250GB partition on the 1TB drive out of it) I could use all these drives and retain use of most of the storage space.

However, and here's my first question, if an HDD was to fail (as opposed to a single corrupt partition) then I could loose up to 3 partitions, and I assume this would render my RAID array non-recoverable? If so, I guess this would officially be a bad idea?

Question number 2: If I combined the 750GB drive and the 1TB drive using LVM to make a single 1.5TB logical partition, could I then use this as one of the drives for a 3x1.5TB software RAID-5 setup? Kind of LVM-on-RAID-on-LVM? Or is this just not possible/just plain stupid? My thinking is that if it is possible, then a failure of either the 1TB or 750GB HDD would result in a failure of a "single drive" from the RAID system, and so it would still be recoverable?

Question number 3: One of the 1.5TB HDD's I want to use for the RAID setup is already in use in the existing LVM setup that I am recovering. Are there any cute ways for migrating the data on the disk into the new RAID-5 setup, or do I have to clear everything off the disks and start from scratch?

Final question: Am I just being a dork and should go and shell out a couple of hundred bucks to buy another 1.5TB drive and be done with it?

Thanks to anyone who has the stamina to read through the above and still be willing to reply. J.

---

### Post by drave99 on 2009-06-12
err. i can count 6 partitions not 8

if you made 2 partions on a 1.5 TB drive and the drive failed you'd be stuffed. (3 partions?? how??) bad.

LVM on RAID on LVM == no no no

fraid youll have to wipe and start from scratch

having all same sized disks just makes everything way easier and you dont loose space, also the more disks you use the better. with 3 disks usable space is 2/3, with 4 3/4, with 10 9/10

---

### Post by grantemsley on 2009-06-12
> **capnjim said:**
> I currently have a 3TB non-RAID LVM system, and of course the worst has happen, the primary drive in the LVM group has started to fail. Fortunately I can still access the disk to pull data off, and have the LVM metadata backed up.



Backup whatever you can now, before the drive fails completely. At least make sure you get any really important stuff copied to a different drive

> 

So, having confirmed my suspicion I was being an idiot using LVM without RAID, my plan now is to rebuild using LVM over RAID-5. This will be my first RAID setup, and I have a few questions.

I have available to hand 2 x 1.5TB HDD's, 1 x 1TB HDD, and 1 x 750GB HDD. I understand that the capacity of a RAID-5 system will be equal to (n-1) * S where S is the capacity of the smallest drive in the array. I also saw somewhere that when building a software RAID system that one does not so much build it on HDD's, but across partitions. So I was thinking, if I paritioned the drives so that they form a group of 8 x 750GB partitions (and leave the extra 250GB partition on the 1TB drive out of it) I could use all these drives and retain use of most of the storage space.

However, and here's my first question, if an HDD was to fail (as opposed to a single corrupt partition) then I could loose up to 3 partitions, and I assume this would render my RAID array non-recoverable? If so, I guess this would officially be a bad idea?


NO! One partition per drive per array.  Otherwise you don't have any redundancy and may as well just leave RAID out of the equation.  mdadm will warn you if you try to have 2 partitions on the same drive as part of the array (it will still let you do it if you really want to though).

You can however make a 4x750GB raid 5 array, a 3x250 raid 5 and a 2x250 raid0 or raid1 if you want to.

Personally I would use 3x1TB (the 2 1.5's and the 1tb drives), 3x500 (left over 500TB from the 1.5's, and 500 from the 750), and 250GB non raided on the rest of the 750.
> 



Question number 2: If I combined the 750GB drive and the 1TB drive using LVM to make a single 1.5TB logical partition, could I then use this as one of the drives for a 3x1.5TB software RAID-5 setup? Kind of LVM-on-RAID-on-LVM? Or is this just not possible/just plain stupid? My thinking is that if it is possible, then a failure of either the 1TB or 750GB HDD would result in a failure of a "single drive" from the RAID system, and so it would still be recoverable?


I'm not sure if it is technically possible or not...but I would hate to be the one who has to figure out what to do when a drive starts failing in that setup.
> 
Question number 3: One of the 1.5TB HDD's I want to use for the RAID setup is already in use in the existing LVM setup that I am recovering. Are there any cute ways for migrating the data on the disk into the new RAID-5 setup, or do I have to clear everything off the disks and start from scratch?


There is a very DANGEROUS way to do it, if you can clear off 2 of the 3 drives needed to build a raid5 array. See my thread here: [http://ubuntuforums.org/showthread.php?t=1166909](http://ubuntuforums.org/showthread.php?t=1166909)

I don't recommend it, but I did it myself.
> 
Final question: Am I just being a dork and should go and shell out a couple of hundred bucks to buy another 1.5TB drive and be done with it?

Thanks to anyone who has the stamina to read through the above and still be willing to reply. J.

I would definitely add RAID to your setup...because that's a lot of data to lose if a drive fails.

Buying more drives is always nice...you'll eventually need the space, and if you replaced the 750 with a 1.5TB drive it would make things a bit less convoluted to setup and still use all the space. I'd also test the other drives to make sure they aren't getting to old or having any issues.

Hope this helps.

---

### Post by overclocker on 2009-12-07
I have a better idea, if you have different size hdds you can group them in pairs (or 3 or 4) by mdadm in raid0 to achieve the same (ore more) size logical devices and after that build yor raid5 over this created mdX devices and hdds with max size. For example I have a set of hard drives and try to build a raid-5 array with 2x1.5TB and 3x500GB and 2x750GB First of all we should prepare logical units for raid5 array. For example our hdds in system are:

sda - 500GB
sdb - 500GB
sdc - 500GB
sdd - 750GB
sde - 750GB
sdf - 1.5 TB
sdg - 1.5TB

Lets do it:
First of all we have to create partitions with types 0xfd for sda-sde disks but NOT sdf and sdg tell you why little later

mdadm -C /dev/md0 -L 0 -N 3 /dev/sda1 /dev/sdb1 /dev/sdc1
after that we have /dev/md0 with 1.5TB capacity
mdadm -C /dev/md1 -L 0 -N 2 /dev/sdd1 /dev/sde1
another 1.5TB /dev/md1
and now!!!
mdadm -C /dev/md2 -L 5 -N 4 --force --spare-devices=0 /dev/md0 /dev/md1 /dev/sdf /dev/sdg

As a result we have 4.5TB md2 raid 5 array build on 4 block devices /dev/md0, /dev/md1, /dev/sdg and /dev/sdf
after that we should create or edit /etc/mdadm.conf to start md2 array

If we partition sdg and sdf hdds as first 5 hdds with partition types 0xfd  our raid5   will not even start if kernel is made with raid support because it will init listed block devices at startup at the same time and md2 raid 5 array couldn't find md0 and md1 devices

But if we build md2 from md0, md1 and sdf, sdg without partitions with type 0xfd,  md0 and md1 devices will init at kernel startup and md2 device will start after mdadm.conf is processed... What do you think about this method?

---

### Post by capnjim on 2010-01-01
I never followed up on this post to say what I did. Thanks for all the responses. I n the end I decided that cute and complicated was a bad idea, so went out and bought some more 1.5TB drives. I am now running two RAID-1's (each 2x1.5TB) which I have put LVM over so I can easily add in more later. One disk from each RAID-1 pair is on the same controller, so if a disk controller failed I would still have a working system to recover from. I know not a perfect setup, but my primary goal has been to protect from HDD failure, since that is what has bitten me time and time again over the years, and hopefully this will do that.

---

