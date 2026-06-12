---
title: "Complete System Transfer - reality check"
date: 2013-01-25
forum: Server Platforms
---

### Post by chrisguk on 2013-01-25
For some unusual reason my disks in my RAID 5 config have started failing.  Now they haven't all failed at once, and i they did I would be looking at the RAID controller as the cause.  I noticed the other day that two or three disks had an orange light.

This prompted me to take some drastic action because I wanted to upgrade the disk sizes anyway.  I have ordered 6 new hotswap disks and a new RAID controller as my old controller is not compatible with the larger disks.

I have looked at some ghost image software but wanted to know what the community thinks my best options are to transfer my completed system to the new disks?

Any yes this has been a real expensive problem for me financially :(

---

### Post by tgalati4 on 2013-01-25
I've always had luck with:

```
sudo cp /dev/sda /dev/sde
```

Be sure you use the correct drive designators and use gparted to expand the partition or add new partitions.  You may get an error:  "Current partition doesn't end on a cylinder boundary, would you like to fix?"  "Why yes, I would."

This may or may not work with drives that are striped for RAID5, but it's worth a shot.

---

### Post by chrisguk on 2013-01-25
> **tgalati4 said:**
> I've always had luck with:

```
sudo cp /dev/sda /dev/sde
```

Be sure you use the correct drive designators and use gparted to expand the partition or add new partitions.  You may get an error:  "Current partition doesn't end on a cylinder boundary, would you like to fix?"  "Why yes, I would."

This may or may not work with drives that are striped for RAID5, but it's worth a shot.

Ive been reading that Mondo seems to be the best option as it supports RAID hardware configuration.

---

### Post by hawkmage on 2013-01-25
I usually don't try to do a replication of everything.  I will usually backup data and configuration for each application. Install the applications on the new server and then restore the data and configs.

---

### Post by chrisguk on 2013-01-25
Probably the best thing I have done is document the whole server config and steps to configure it on my own Mediawiki held locally.

I guess to start from scratch wont be that bad but it does feel like a pain in the butt.

I managed to carry out a full backup using bacula tonight.  Will I be able to restore from that if needed or is it too risky?

---

### Post by tgalati4 on 2013-01-25
Haven't used bacula (well I have, but for home directory backups not a server restore point) so I can't comment, but printing out your mediawiki with your log/configuration is a good way to go.  I use zim for taking such notes--quite helpful.  

What was the raid controller?  What do the orange lights mean?  How did you determine that the controller was failing?  What symptoms were the disks giving to indicate failure?  Did you have SMART monitoring on the drives?

---

### Post by chrisguk on 2013-01-25
Ye my mediawiki is a valuable tool and lucky it's on a different server though I always back my PHP dev stuff to two locations ( basically everything under /var/www) the reason I created the wiki was to start a scripting project and make a script that will install all the repos and configure the server. It's a long way off but I'm getting there.

So I ended up using mondo and I'm impressed, I now have the server in iso format ready to write to DVDs .


I'm running a HP proliant.  The great thing about this server is it comes with some great tools for fault finding.  Those tools along with orange light told me the 3 disks were bad .

---

