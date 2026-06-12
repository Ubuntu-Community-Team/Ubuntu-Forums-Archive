---
title: "Add HDD to Server Ubuntu 14.04 LTS"
date: 2017-03-14
forum: Server Platforms
---

### Post by poliman-pl on 2017-03-14
Hi. I have ISP with one website + database (which is growing). This  is VPS with Ubuntu 14.04 LTS with 10GB SSD. Currently there is 2,8GB  free. I would like to buy one more disk drive (ovh.net provide an option "additional disk") but I am not sure what  will be with next amount of data when whole space on first disk (this  10GB SSD) will be used. Do the data will automatically be saved on the  second disk? What to do if they will not? How to make visible secondary disk in ubuntu?

---

### Post by TheFu on 2017-03-14
How you add the 2nd disk, plus any file systems, depends on the current setup.  If you used LVM, then it is easy. If not, then you'll have to manually decide where to add the new partition(s).  

For example, my blog server ran out of the initial storage I provided.
```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1       7.1G  3.7G  3.1G  55% /
/dev/vda2       2.3G  1.1G  1.1G  49% /var/www
```

vda1 actually ran out of i-nodes. Because the blog software is ruby, it has lots and lots of tiny files which eat up i-nodes.  The blog software is stored in /var/www, so I decided to add more storage there - see vda2?  I could have added it to /var/, but that would have been harder, since a running OS writes to /var/.  Only the website uses /var/www/ - easy to take down for a few minutes, move the files to the new storage, mount the new storage to the correct spot, and bring the blog back up. Took a few minutes with the rest of the system still running.

Of course, if you can boot off alternate media, then you can do whatever you want without the same risks.

Many people would add it to /home/ . This machine doesn't have any real users who can login, so /home uses about 10MB of storage.  /usr/ is another option. On this machine, /var/ was the largest directory by file size and was the only area I expected to keep growing.

It isn't pretty, but I didn't start by using LVM.  That new storage was added 4+ yrs ago and has been working all this time perfectly.

If you need detailed steps: [https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux](https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux)  I don't know anything about your VPS provider.

---

### Post by darkod on 2017-03-14
To add to what TheFu wrote above, just be careful planning and executing your steps. From your question whether the OS will start writing automatically on the new disk/partition, we can see that you have very little idea how linux partitions and mount points work.

Be careful because a wrong command can mess up things, sometimes very seriously.

---

### Post by TheFu on 2017-03-14
Forgot to mention - backups and know you can actually recover before starting.  It is very common for people to make a tiny mistake that completely destroys/loses all their data until you are very familiar with these things. Always begin with a backup and **test restore to a different machine.**

If you aren't certain, ask for more help, but please do your homework and test this on a VM.

---

### Post by mastablasta on 2017-03-17
wouldn't the ovh.net handle it for you?

---

### Post by TheFu on 2017-03-17
> **mastablasta said:**
> wouldn't the ovh.net handle it for you?

Wouldn't it be possible to bring up a 2nd instance with more storage, then just backup/restore to the new location and kill off the old VM?  Running 2 VMs for 1-2 hrs isn't likely to break any budgets.

---

