---
title: "Major RAID5 failure :("
date: 2012-02-06
forum: Server Platforms
---

### Post by cheechy on 2012-02-06
ok here we go - apologies for jumping onto here for help without first contributing. I'm not a major ubuntu user but do try to help colleagues and friends wherever possible with my limited knowledge.
 
To lay out the position I'm in I have a fairly simple software RAID 5 config using a boot disk and 4 2TB Samsung drives (1 spare). Its being used as a file server and sits as a VMware client. 
 
I've had it running successfully for almost a year but have had periodic single disk failures. The disk has been added back into the Raid ok thus far. Last night however the server seemed to be slow to react and I did some initial checks - or at least I tried to. VM vsphere client could not get any response from the Ubuntu server but I left it for a day to see if it could. Came back tonight with the server showing no signs of coming back so decided I only had the option of pulling the plug.
 
So now its back - first off the server would not restart unless I removed one of the datastore - I'm assuming its a failed disk. Moreover it seems that the boot disk part has lost its superblock. I'm assuming Ubuntu got its knickers in a twist trying to resync a failed disk for some reason and when I pulled the plug the block became corrupsted.
 
It now gets confusing - I still have 3 active disks but when I try to reassemble....
```
mdadm: /dev/md1 assembled from 3 drives = not enough to start the array while not clean - consider --force
```
 
Using --force doesn't seem to have any affect. Using Watch it seems the server is making no attempt to reassemble the array. So the question is around how I rescue the array without loosing data?
 
Any ideas - I did see a post from a couple of years back about "cleaning" the superblock but in all honesty I'm not really sure what that entails.
 
Help 8-[

---

### Post by cheechy on 2012-02-06
Oh just to add running ```
mdadm -E /dev/sd[abcd] 
``` returns:
```

active sync /dev/sdb
active sync /dev/sdc
active sync /dev/sdd
active sync

```
So it looks like the array is still pointing to a device which is no longer defined.

---

### Post by cheechy on 2012-02-06
Edit : Post Removed. 
 
Posts 1 and 2 still relevant though :(

---

### Post by rubylaser on 2012-02-06
What's the output of these commands?

```
cat /proc/mdstat
cat /etc/mdadm/mdadm.conf
```

Also, what's the exact command you are trying to use to assemble the array?

---

### Post by cheechy on 2012-02-06
> **rubylaser said:**
> What's the output of these commands?
 
```
cat /proc/mdstat
cat /etc/mdadm/mdadm.conf
```
 
Also, what's the exact command you are trying to use to assemble the array?
 
 
Rubylaser - found one of your posts from around a week ago:
 
> mdadm --assemble --run --force /dev/md0 /dev/sd[bcd]
 
This works!!
 
Now I have to find out what the story is with the non-working disk and also back up data - not done a backup for a couple of months.
 
Thank you! :D

---

### Post by cheechy on 2012-02-06
Ignore post once again! The array has sorted itself out now it seems and the array is back in degraded status with the evil failed disk removed.
 
Just by appearing in the thread you helped me fix my issues. Many thanks :-)

---

### Post by rubylaser on 2012-02-06
No problem, that was easy :)

---

### Post by meadmarc on 2012-02-06
If you ever have a hard drive failure like that again- you can use Spin Rite on a single drive if you pull it out from the raid, and hook it directly to the motherboard or a card.  If it can fix the offending drive, you may get your raid back long enough to recover the data or get an image off it.

Oh...  and use crontab -e and rsync for a backup to an external drive, just in case!  ;)

[http://www.grc.com](http://www.grc.com)

---

### Post by Krupski on 2012-02-07
> **cheechy said:**
> Ignore post once again! The array has sorted itself out now it seems and the array is back in degraded status with the evil failed disk removed.
 
Just by appearing in the thread you helped me fix my issues. Many thanks :-)


I'm glad yours came back. A while ago I had a failed drive and in trying to find which one it was, I pulled each SATA cable individually and looked to see which "/dev/sd?" went away.

Well MDADM saw each pulled cable as a failed drive and to make a sad story short, I lost all of my data.

In hindsight, I could have recovered it, but I was so shook up and nervous that I did everything wrong and wrecked it.

Now excuse me while I dry my eyes again... :(

---

### Post by rubylaser on 2012-02-07
> **Krupski said:**
> I'm glad yours came back. A while ago I had a failed drive and in trying to find which one it was, I pulled each SATA cable individually and looked to see which "/dev/sd?" went away.

Well MDADM saw each pulled cable as a failed drive and to make a sad story short, I lost all of my data.

In hindsight, I could have recovered it, but I was so shook up and nervous that I did everything wrong and wrecked it.

Now excuse me while I dry my eyes again... :(

This is the biggest problem for most people with mdadm.  It's so easy to set up, but most people don't spend time to really understand how things work and the commands to use when they don't.  Try it out, and fail drives, etc before you move your data to the array, so you can troubleshoot it, so when you lose a disk, you'll know what to do.

When in doubt, it's best to leave the array unmounted, and leave the array as read only as possible.  If you don't know what to do, post here on the Forum and someone else, or I will be happy to help.

---

