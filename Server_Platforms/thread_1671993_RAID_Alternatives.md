---
title: "RAID Alternatives"
date: 2011-01-20
forum: Server Platforms
---

### Post by Ranger_Joe on 2011-01-20
Hey Everyone,
I'm setting up my first server today. I only have one hard drive, so I can't RAID yet... although I'd like to use RAID 1 in the future.

Here's my question: What is the best RAID 1 alternative or backup strategy? I know I should assume that what can go wrong, WILL go wrong. How do I reconcile that with my budget?

Thanks!

---

### Post by hawk2010 on 2011-01-21
RAID 1 means mirroring. Ideally you should have two hard drives. You have three options

1. Get a 2nd hard drive and do RAID 1
2. Do software based RAID.
3. Back up to an off site location via network.

---

### Post by idny on 2011-01-21
As Hawk2010 Said.

> **hawk2010 said:**
> 
1. Get a 2nd hard drive and do RAID 1
2. Do software based RAID.
3. Back up to an off site location via network.

1. Raid 1 on Hardware Card = Durable but Expensive
2. Software RAID = free using mdadm, fairly reliable but can be slower.
3. Offsite = Most resiliance but expensive. Need a VPN if connection to offsite location uses the internet.

---

### Post by cascade9 on 2011-01-21
> **hawk2010 said:**
> RAID 1 means mirroring. Ideally you should have two hard drives. You have three options

1. Get a 2nd hard drive and do RAID 1
2. Do software based RAID.
3. Back up to an off site location via network.

2? What, make a RAID system with a single drive? You might be able to do some silliness with partitions to have some 'single drive RAID1' setup, that is a great way to increase overheads, decease the usable siz of your HDD, and get nothing back for the effort. Hmm, maybe if you get a bad sector it might help, but thats all I can think of. 

There are a few more options. 

4- backup to removable drive. Either an eSATA drive, a USB drive, a firewire drive or even an internal drive that you install then remove afterwards. 

Aside from actually needing to hook up the drive to do backups it would be more reliable than RAID1. One big power spike or surge can fry your whole system, its a lot harder to fry a HDD thats not powered up or connected to the system. 

5- backup to a 2nd HDD that is permanently hooked up. Again, you would need to manually backup (or you could do it from a script) and if you get a surge, you could lose all data, same as with RAID1.

6- backup to CD/DVD/blu-ray. Dont. Just dont.  

7- backup to a 2nd machine locally via network. Same power surge issues, but slightly less risk. Only very slightly though.

---

### Post by CharlesA on 2011-01-21
+1 to not backing up to CD/DVD/Bluray. Bad idea.

The way I do my backups is that I just rsync my storage array to an external hard drive and store it in a safe place.

---

### Post by Boondoklife on 2011-01-21
If you are going for a RAID 1 setup, then you can just go ahead and setup the RAID now and then when you get the next disk, just add it to the RAID setup with mdadm. RAID 1 is able to run just fine with one disk.

You may want to consider RAID 5 if you might expand the storage later, as well as LVM. In the case of RAID 5, you can grow your array by adding another disk at a later time. You also get the redundancy of RAID 1 with a bit of a speed boost like RAID 0. The speed boost gets better the more disks are in the RAID. RAID 5 does require at least 3 disks.

I would suggest RAID 5 with 5 disks (4 Live, 1 Spare) if you are going for a secure and speedy setup. If you are just looking for a simple redundancy, then RAID 1 will be your best bet.

---

