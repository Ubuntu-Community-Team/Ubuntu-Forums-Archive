---
title: "Ubuntu server 18 installer can't mount raid6 at /"
date: 2020-04-09
forum: Server Platforms
---

### Post by honeycombs_big_yahyahyah on 2020-04-09
Hi all,

I'm trying to install server 18.04.4 (using the alternative installer) on my machine with existing raid1 (for /boot) and raid6 (for /) devices set up. I set the partitioner to format the raid1 ext4, and it seems fine. I set it to not overwrite the ext2 raid6 (i have data i want to keep). The installer chokes when trying to mount the raid6 (/dev/md127) at /. The syslog has the following error:
```
mount: mounting /dev/md127 on /target/ failed: Invalid argument
```I'm not sure how to get more detailed information than that, however. e2fsck indicates the array is clean. I'm able to mount the array in the shell and access the files. Just not sure why the installer is having a hard time. Any thoughts greatly appreciated.


Thanks, Allie

---

### Post by lvm on 2020-04-09
You are saying that raid6 is md126 but error message mentions md127 - should be the first array, raid1 as md numbers devices from 127 down? Is it possible that installer asks all installation parameters first without doing anything, then starts installation and fails to mount the future /boot?

---

### Post by honeycombs_big_yahyahyah on 2020-04-10
Sorry, it sometimes switches which raid devices gets assigned md126/md127.  md127 is currently the raid6 i want to mount at /, and md126 is currently the raid1 i want to mount at /boot...

I'm not sure what you're asking, lvm... I'm in the partition stage, I select manual, and select the raid1 to be mounted at /boot (ext4, formatting it clean), and the raid6 to be mounted at / (ext2, no formatting).  It specifically says that it cannot mount the root drive (/)... i get no error related to /boot...

[ATTACH=CONFIG]285478[/ATTACH]

---

### Post by slickymaster on 2020-04-10
*Thread moved to **Server Platforms**.*

---

### Post by slickymaster on 2020-04-10
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by darkod on 2020-04-10
Can you please show the manual partitioner step screen? Like this it is difficult to know at which point you receive that error.

Also, you say you want new installation but NOT to format root. Ubuntu allows you to do that (I think) but personally I would never do it like that. For me it makes no sense making new installation but not formating the system root partition.

If you want to keep important data across reinstalls then you should rearrange where you keep your data. Don't make one huge array to sirve as / and then you can never format all of it because you don't want to lose the data.

---

### Post by honeycombs_big_yahyahyah on 2020-04-11
Thanks Darko,

See screen photos attached here.

To answer your question, the reason I mount my raid6 at / is because 1) if one separates his system off onto another drive or partition and it fails, your system goes down.  So, I want the system on a raid too.  2) Separating out the system from data so each go onto their own raid is a pain, as data goes in various places - e.g. /home, /opt, /media, etc.  Maybe there's a better way to manage data locations; I'd be all ears for better solutions.  Not sure if LVM would help me in that regard.

Thanks...

[https://i.imgur.com/k8x4zNW.jpg](https://i.imgur.com/k8x4zNW.jpg)
[https://i.imgur.com/3SmZgim.png](https://i.imgur.com/3SmZgim.png)
[https://i.imgur.com/DFvD97B.png](https://i.imgur.com/DFvD97B.png)
[https://i.imgur.com/0xVqWy7.png](https://i.imgur.com/0xVqWy7.png)
[https://i.imgur.com/35RQHiA.png](https://i.imgur.com/35RQHiA.png)
[https://i.imgur.com/fDjYe0n.png](https://i.imgur.com/fDjYe0n.png)
[https://i.imgur.com/OLQXl2s.png](https://i.imgur.com/OLQXl2s.png)
[https://i.imgur.com/FKkqTVD.png](https://i.imgur.com/FKkqTVD.png)
[https://i.imgur.com/2tNLSMr.png](https://i.imgur.com/2tNLSMr.png)

---

### Post by darkod on 2020-04-11
Well from the screenshots you seem to be doing it right. I don't know why it complains honestly...

To answer your other questions, yes, LVM would help you a lot. You can make reasonably large raid1 array for root (for example 32GB). That is big enough if you only keep basic OS on root.

The rest can be raid6 array used as physical device for LVM. And in the LVM you create logical volumes for each main mount point you wish (like /home, /var, /usr, etc).

---

### Post by honeycombs_big_yahyahyah on 2020-04-11
Thanks Darko...  So, I suppose I could shrink my raid6 a bit and add another raid1 for /...  Which top level directories would you recommend I put on the raid6 vs smaller raid1?  And, thinking ahead to the installation, do i set up LVM in the installer, telling it to put, say, /lib on the raid1, and /var on the raid6?  Doesn't that defeat the purpose of being able to format the system installation drive?

@everyone else: any thoughts about what i might do to resolve the failure of the installer to mount my raid6?

---

### Post by honeycombs_big_yahyahyah on 2020-04-12
Update: partman detects the raid6 as an ext2 filesystem.  However, when I run blkid or mount it from the shell, it is reported as having an ext4 filesystem.  I don't honestly remember how it set it up years ago.  I suspect it is actually ext4, but that partman thinks it is ext2 for some reason.

I've tried mounting it from the shell and then allowing partman to continue, but partman then tells me that there are partition changes scheduled for the raid6, so i have to back out.  I've tried telling partman that it's an ext4, but it then warns me that it will be destroying data, since (I assume) it thinks it has to convert from ext2 to ext4.

Any thoughts here?  I suspect I have found the issue, but perhaps it's actually something else altogether...

---

### Post by darkod on 2020-04-12
Unfortunately I don't see an easy way out of this. I was also wondering why does it say ext2 and whether you really use that filesystem instead of ext4.

If your OS was on different disk/array you could have installed the OS first and then mount the big data array and see how it gets detected by the OS. But since your OS is on the same array currently you can't do that.

---

### Post by honeycombs_big_yahyahyah on 2020-04-13
Is there a way to force partman to treat the array as ext4?  i.e. overriding its apparently-erroneous determination of it being an ext2?

update: the ubuntu 18 live installer correctly recognizes the raid6 as being ext4 formatted.  there seems to be something up with partman not recognizing it as ext4, though i'm not sure if that's what's keeping it from mounting it.  Any help greatly appreciated... please?

---

