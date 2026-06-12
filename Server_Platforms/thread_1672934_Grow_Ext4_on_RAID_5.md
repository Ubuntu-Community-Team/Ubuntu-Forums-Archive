---
title: "Grow Ext4 on RAID 5"
date: 2011-01-21
forum: Server Platforms
---

### Post by Babyd3k on 2011-01-21
I've been looking around for an answer to this I can't find anything definitive. 

Is resize2fs safe to use to expand an ext4 partition? I see lots of claims of it working but lots of people saying that it corrupted all their data.

Is there any better/safer/other method to grow the size of an ext4 partition on an already expanded RAID5 that is running on an Ubuntu 10.04.1 server?

I read the man page for resize2fs and it seems to state that you can't do an expand on EXT4 while it is mounted only EXT3 is that correct? 

Do I have to explicitly state a system size with EXT4 or can I let resize2fs do that automatically?

---

### Post by psusi on 2011-01-21
> **Babyd3k said:**
> 
Is resize2fs safe to use to expand an ext4 partition? I see lots of claims of it working but lots of people saying that it corrupted all their data.

Yes.

> **Babyd3k said:**
> I read the man page for resize2fs and it seems to state that you can't do an expand on EXT4 while it is mounted only EXT3 is that correct? 

No, looks like the man page is a little out of date.

> **Babyd3k said:**
> Do I have to explicitly state a system size with EXT4 or can I let resize2fs do that automatically?

Let it do it automatically.

---

### Post by Babyd3k on 2011-01-22
resize2fs worked like a charm. Thanks for the answers. 

For anyone that cares. I unmounted the drive and ran.

resize2fs -p /dev/md0

Although the -p is supposed to put up some sort of status indicators it didn't for me and the system seemed to hang but I let it sit and after about 2 hours (I have a 8Tb array) it confirmed everything was ok.

---

### Post by mannen on 2011-05-20
Works for me on a RAID5.

root@server:~# resize2fs -p /dev/md0
resize2fs 1.41.11 (14-Mar-2010)
Resizing the filesystem on /dev/md0 to 1220949920 (4k) blocks.
Begin pass 1 (max = 14904)
Extending the inode table     XXXXXXXXXXXXXXXXXX----------------------

---

