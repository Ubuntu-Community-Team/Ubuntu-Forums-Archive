---
title: "Best storage option"
date: 2013-08-16
forum: Server Platforms
---

### Post by ads2996 on 2013-08-16
Hi, 
I recently set up a home server for my family, and u was wondering the best option for storage currently the server has 2 1tb drives in it, and hopefully in the near future there will be another 2 1tb drives, it also has a 250/320gb drive and a 80gb os drive, I had originally tried to used raid 0 from the data controller in my pcie bay but it was causing a problem with booting as the raid array became hdd0 whereas before it was the 80gn driven plugged directly into the mobo. 
Any help greatly appreciated.

---

### Post by papibe on 2013-08-16
Hi ads2996.

A few thoughts:
[LIST]
[*]I would put a bootable disk with the OS out of the raid and connected directly to the motherboard.
[*]I can hardly think of an scenario where you need raid 0 for a home server. That is for raw speed, but since files will be serve over the network, it looses its advantage. Also, it would be very vulnerable to data lost since if any drive fails, you loose everything.
[*]raid 1 would provide redundancy, but that won't take care of one of the most common requirements of a home server: to be able to grow in space capacity.
[*]I would personally would go with raid 5 for the data. This would allow you both to have redundancy and the capacity to grow. Note that the minimum partitions/disks for a raid 5 array is 3.
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

---

### Post by lukeiamyourfather on 2013-08-16
I've been considering setting up a home server recently so I'm in a similar situation. I've come to the conclusion that I'm going to use ZFS for the data storage with RAID Z and a separate drive for the OS. No need for a hardware RAID controller, any old SATA ports will do.

---

### Post by ads2996 on 2013-08-16
i bought a raid controller due the lacking of sata ports on my mobo there is only 2. I am unfamiliar with zfs i wiil look into it.

---

### Post by papibe on 2013-08-16
> **lukeiamyourfather said:**
> No need for a hardware RAID controller, any old SATA ports will do.
+1

You can also use the RAID card as just an expander and use software RAID.

Regards.

---

### Post by ads2996 on 2013-08-16
I would plan to have a 500gb redundant raid setup maybe 5 or 6 to store my photos and personal documents (i would probably need to buy or aquire 2/3 identical drives), then have non redundant storage for my music and videos as they are unimportant and doesn't matter if they are lost

---

### Post by lukeiamyourfather on 2013-08-16
If you don't want to lose files think about a backup plan. RAID is not backup.

---

### Post by ads2996 on 2013-08-16
They would also be backed up on an external drive it is just so they can be accessed easily and raid would just make it easier

---

