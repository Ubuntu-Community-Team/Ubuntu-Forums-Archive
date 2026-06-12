---
title: "Raid failed - missing physical disk"
date: 2010-11-23
forum: Server Platforms
---

### Post by SkyHiRider on 2010-11-23
My raid array has failed. I have two disks /dev/sda and /dev/sdb.

/dev/sdb has failed and I could not rebuild the array(madm returned that the device is busy) so I rebooted the machine. After that, the whole sdb disk went missing, as it now only shows sda in fdisk -l. 

Did the disk went totally dead or my raid glitched?

---

### Post by arsnova on 2010-12-21
bump!

---

### Post by Vegan on 2010-12-21
Unfortunately your array is now toast.

I have regularly counseled against using software RAID.

Hope you have a backup.

---

### Post by coffee412 on 2010-12-21
> **Vegan said:**
> Unfortunately your array is now toast.

I have regularly counseled against using software RAID.

Hope you have a backup.

Kinda doubt its a mdadm issue here. If Fdisk doesnt show the disk then I would say the disk died or something similar.

A 2 drive array does not have much protection unless they are in a mirrored arrangement. 

I have been running software raid (5) for over 6 years with no problem. 

Go figure?

coffee

---

### Post by psusi on 2010-12-21
Yep, drive is toast.  I hope that was a raid1 and not a raid0.

---

### Post by arsnova on 2010-12-22
Similar situation here with a software RAID 1 array. Drive sdb was removed from the server and cool to the touch. We have a replacement on its way this morning. Seems to me that mdadm is doing what it should and reporting degraded arrays notices. In our case, the disk redundancy is in addition to tape backup.

---

### Post by psusi on 2010-12-22
> **arsnova said:**
> In our case, the disk redundancy is in addition to tape backup.

As it should be ;)

RAID is not a replacement for backups; it is a means of maintaining uptime despite hardware failure.

---

### Post by arsnova on 2010-12-22
Right--and it pays! Nice to see the relative non-impact in practice. :)

---

### Post by coffee412 on 2010-12-22
Ive always enjoyed the benefits of software raid. Just to recap for those that dont realize.

1. Using the built in raid on motherboards is not true raid. There are differences in raid controllers and sometimes can cause problems when you have to switch to another controller.

2. Actual hardware raid is expensive. Also, If you have to replace the card you will want an exact replacement to make sure the raid actually comes up with no problems. Of course there is the "Dell from Hell" raid cards that I have seen alot of them fail and you get to play with firmware then.

3. Software raid is easy to setup and maintain. Doesnt really matter what controller you switch to as its software controlled. 

The only dissadvantage I really see with software raid is that its going to be slower ( in the case of raid5) than hardware raid. So, You do want a good processor. But I have been running my raid5 on a AMD single core processor with 2 gigs memory for years. Im running 4 seagate 320 gig drives with it. Of course since I mentioned it watch a drive drop off the raid now! :D


Merry Christmas Everyone!

---

