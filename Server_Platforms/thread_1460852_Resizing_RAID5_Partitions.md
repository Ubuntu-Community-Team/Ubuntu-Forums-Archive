---
title: "Resizing RAID5 Partitions?"
date: 2010-04-23
forum: Server Platforms
---

### Post by flatline on 2010-04-23
I have a server currently running Ubuntu Server 9.10 x64, which has / installed on a 320GB drive, and /home located on a 4TB RAID5 array (shared over my local network).  I've realized that my 4TB RAID isn't enough though, and I don't want to just band-aid it by adding 2 more 1TB drives (the most my current mobo can support without delving into extra SATA controllers).  I'm currently backing up my windows gaming PC, Macbook Pro, wife's laptop, and HTPC to the RAID array, hence why it's filling up faster than anticipated.

Is there a safe/reliable/relatively uncomplicated way to resize my RAID5 array and transition all the 1TB drives to 2TB models, even if I have to do it one drive at a time and wait until the array heals?  With only 2 SATA slots free, I could possibly create a degraded RAID5 using 2x2TB, but I'd prefer to just resize the current array unless it's going to prove to be excessively complicated.

Thanks in advance!

---

### Post by ratcheer on 2010-04-23
The only safe, reliable way to do it is to backup the data on your current RAID array, drop it, create your new RAID array, and restore your data. But, I suspect that you have nothing capable of holding such a backup.

I am having trouble understanding your current configuration. Is it 4 - 1 TB drives striped as RAID 5? 

Tim

---

### Post by flatline on 2010-04-23
> **ratcheer said:**
> The only safe, reliable way to do it is to backup the data on your current RAID array, drop it, create your new RAID array, and restore your data. But, I suspect that you have nothing capable of holding such a backup.

I am having trouble understanding your current configuration. Is it 4 - 1 TB drives striped as RAID 5? 

Tim

Yes, I have the main system installed on my 320GB drive, and then 4 1TB drives in a RAID5, giving me something like 2.87TB of usable space for /home.

I was afraid that blowing it all away would be my only option.  I suppose all that's left is to figure out what I **really** need to keep and save that to external drives, then drop the 4TB RAID like it's hot (I'm thinking 5x2TB should be enough, that would give me like 8.5TB usable space).  Good thing my newegg preferred account is 12 months no interest... (assuming I can get 5 2TB drives for $120/each, which is about the best I've seen them, that's still $600.  ouch.  I'll just have to remind my wife what happened before when she didn't have any backups.)

*really wishes Drobo's BeyondRAID wasn't proprietary and would get merged into mdadm*

---

### Post by ratcheer on 2010-04-23
I didn't say it is the only way, but if you don't want to put your data at risk, it is the best way. Heck, you should make a good backup even if you intend to try to resize the array.

Do you use any kind of LVM software?

Tim

---

### Post by flatline on 2010-04-23
> **ratcheer said:**
> I didn't say it is the only way, but if you don't want to put your data at risk, it is the best way. Heck, you should make a good backup even if you intend to try to resize the array.

Do you use any kind of LVM software?

Tim

No, I'm not using LVM.  I don't fully understand it (never taken the time to read up on it I guess), and therefore never gave it that much thought.  What can LVM do for me?  One thing I would like is the ability to individually restrict the max size for a given directory - so that one machine's backup doesn't grow rapidly to take up 90% of the available storage.  I *think* LVM can do something like this, using logical partitions instead of physical?

As far as backups, I understand, but most of this data is *already* backups of *other *data.  Believe me, I have bad enough luck that I wouldn't put it past my machines to all fail simultaneously, but there's only so much I can do.

---

### Post by theeldest on 2010-04-23
> **flatline said:**
> Yes, I have the main system installed on my 320GB drive, and then 4 1TB drives in a RAID5, giving me something like 2.87TB of usable space for /home.

I was afraid that blowing it all away would be my only option.  I suppose all that's left is to figure out what I **really** need to keep and save that to external drives, then drop the 4TB RAID like it's hot (I'm thinking 5x2TB should be enough, that would give me like 8.5TB usable space).  Good thing my newegg preferred account is 12 months no interest... (assuming I can get 5 2TB drives for $120/each, which is about the best I've seen them, that's still $600.  ouch.  I'll just have to remind my wife what happened before when she didn't have any backups.)

*really wishes Drobo's BeyondRAID wasn't proprietary and would get merged into mdadm*


I assume you're using mdadm?

What I've done (switching from 4x 640GB to 4x 1.5TB disks) is:
1. Remove one drive.
2. Insert new larger drive; Format, Partition & Mount
3. Add to array and rebuild using the new drive.
...
4. Repeat 1-3 for all drives.
...
5. After you have larger drives installed, the array will still be the same size. mdadm has a command for growing the array to take up all additional space. (I'll find the link if you want it).


Obviously, with 4 rebuild steps in there, there are quite a few opportunities to lose all of your data. Ideally, you want everything backed up. 

But if you're feeling adventurous, you can give this method a try. ;-)

---

### Post by ratcheer on 2010-04-23
> **flatline said:**
> No, I'm not using LVM.  I don't fully understand it (never taken the time to read up on it I guess), and therefore never gave it that much thought.  What can LVM do for me?  One thing I would like is the ability to individually restrict the max size for a given directory - so that one machine's backup doesn't grow rapidly to take up 90% of the available storage.  I *think* LVM can do something like this, using logical partitions instead of physical?

As far as backups, I understand, but most of this data is *already* backups of *other *data.  Believe me, I have bad enough luck that I wouldn't put it past my machines to all fail simultaneously, but there's only so much I can do.

I used LVM (mostly Veritas, but some Sun) in enterprise systems for years and it definitely makes tasks like resizing and most everything else easier. But, I've never used it on small systems, either.

I understand about the backups. It is difficult to have all the resources needed to always do things exactly right.

Tim

---

### Post by flatline on 2010-04-23
Thanks for the replies.  I think I'm going to go ahead and mark this as solved since there doesn't appear to be a quick, easy, safe solution currently in mdadm.  I was going to ask about using LVM and encrypting my RAID5 /home directory, but I'll read up on it first myself and if necessary create a separate thread with a matching title.

---

