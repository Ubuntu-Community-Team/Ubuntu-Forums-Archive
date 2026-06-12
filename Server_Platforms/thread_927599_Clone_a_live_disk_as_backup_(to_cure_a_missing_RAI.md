---
title: "Clone a live disk as backup (to cure a missing RAID)"
date: 2008-09-23
forum: Server Platforms
---

### Post by isync on 2008-09-23
Hey folks,

I've got a running system here but upon setup of the box I did not think about founding it all on a redundancy solution of some sort, first choice would have been a RAID 1. Anyway, now I am here with the problem that my main drive might fail any time.

Moving data to a temp location, re-setting-up the system, and moving data back is *currently* no option. But installing another harddrive and mirroring all data as a sort of "near RAID 1" would be an option.

No, what technique would you recommend to copy or clone my main drive? I could think of a near-realtime solution, with a cron, let's say every 20 minutes, to copy/identify new data. But what tool can help me with that? 

And- is there a way to exactly clone the drive, including bootrecords etc. so in a case of failure of drive 1, I just need to switch cables over to drive 2? Is there a way to do it incrementally, so the clone process doesn't start from scratch each time (peformance!)

Any hints and tool recommendations welcome!

---

### Post by fjgaude on 2008-09-23
Use the **dd** command to copy the whole disk to another disk.

Then use **rsync** to incrementally copy only the changes.

---

### Post by isync on 2008-09-23
Any ready-to-use command and options suggestions for that solution?

---

### Post by fjgaude on 2008-09-23
First, of course, you have to install dd and rsync if they are not already on your system.

# disk image, clone
```
sudo dd if=/dev/hda of=/dev/hdb bs=4096 conv=notrunc,noerror

```

I use **grsync**, not rsync, and don't have it in a **cron** script:

```
sudo rsync -r -t -p -o -g --delete /home/raid/ /media/backup/raid/
```

I trust you can understand these powerful commands. I would study the man pages for both before using them.

You have to learn cron to put the rsync command in it. I don't use cron and know little or nothing about it. Others here do know all there is to know. Let them speak out. <smile>

---

### Post by isync on 2008-09-23
Thanks for your effort!

BTW: do I have to unmount the main disk before dd (which would be undesireable). Rsync has no problems with disk changes while it runs, afaik (due to its upfront file list gathering)

---

### Post by fjgaude on 2008-09-23
Regarding **dd**, I think it would be a good idea to have both drives unmounted. But the man pages may give a note on the need to do that.

I never unmount my raid5 when using grsync.

---

### Post by koenn on 2008-09-23
been there, done that - or at least i tried it once in a test environment (vmware)
[http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm](http://users.telenet.be/mydotcom/howto/linux/diskfakeraid.htm)

---

### Post by fjgaude on 2008-09-23
Very well done, and good too. Thanks, koenn!

---

