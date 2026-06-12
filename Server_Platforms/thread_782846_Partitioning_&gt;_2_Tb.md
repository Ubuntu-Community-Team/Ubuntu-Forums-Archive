---
title: "Partitioning &gt; 2 Tb?"
date: 2008-05-05
forum: Server Platforms
---

### Post by smileypaul on 2008-05-05
Hi Guys,
   I know this topic has been beaten to death, but i still dont have a reliable solution.

I have a RAID 5 setup using a 3ware card. its 4 x 1tb effectively giving me approx 3Tb.

Currently, i formatted as ReiserFS, because at the time (sometime last year), this was the simplest way to effectively get above 2tb.

Now, as of recently, dmesg reports some errors with ReiserFS

```
ReiserFS: sda1: warning: sh-2029: reiserfs_read_bitmap_block: bitmap block (#301268992) reading failed
```


So, naturally, this scares me. Not being able to find a valid solution to this, i want to jump ship to another Filesystem type. 

That being said, I've done some research, and hav found information on EFI/GPT, but as i understand it, Debian/Ubuntu doesnt support this out of the box like RedHat does.

So..

Can anyone give me some info on how they are successfully partitioning > 2Tb??

Thanks.

---

### Post by bluefrog on 2008-05-06
look like a filesystem and/or harddrive problem to me.

You could try ext4 depending on how crucial is your server.

As for GPT, not sure why you mention it. You can use it with Ubuntu if you want but what does it have to do with your filesystem format?

James Dupin

---

### Post by smileypaul on 2008-05-06
I believe it is a filesystem problem :|

The server is very crucial, it receives daily backups, therefore I would prefer to avoid disaster before it happens.

Im just looking for a solution

Thanks for your reply

---

### Post by smileypaul on 2008-05-06
Well,
  I copied all of the data to another disk, blew away the 3tb Reiser partition. I used parted to setup the disk as GPT, and created an EXT3 partition of 2.99Tb. 

Everything seemed fine, copied the data over, rebooted to be sure..

and sure enough, upon reboot, the partition mounted, but my dad seems to be useless. when i ls -al , I receive Question Marks (?'s) for the owner, group, permissions, size etc .. :(

---

### Post by dean123 on 2008-05-13
> **smileypaul said:**
> Well,
  I copied all of the data to another disk, blew away the 3tb Reiser partition. I used parted to setup the disk as GPT, and created an EXT3 partition of 2.99Tb. 

Everything seemed fine, copied the data over, rebooted to be sure..

and sure enough, upon reboot, the partition mounted, but my dad seems to be useless. when i ls -al , I receive Question Marks (?'s) for the owner, group, permissions, size etc .. :(


There is a bug in parted v1.7.x. You need to use parted v.1.8.x or later. Ubuntu has not fixed it so download the latest version of parted, and recompile it.

---

### Post by licensedorchid on 2008-05-13
If the files are large-ish, I would probably use XFS. It can handle 8 exabytes, and is journaling, as well as tuned for large files.
If they are small files, I would use reiserFS, since it can handle 8 TB, and is journaled. I don't know if that helps, since the discussion seems to be going the other way, but that is my two cents.

---

### Post by tamoneya on 2008-05-13
not sure how much this helps but I have RAID 5 1.5 TB (4x500GB).  I have done the partitioning with ext3 and had no problems with it.  It should scale alright up to 3 TB.

---

### Post by psusi on 2008-05-15
Is this a hardware raid or a software raid?  Does it show up as /dev/sda, or /dev/md0?

If it is a hardware raid, then you should not have been able to create a reiserfs partition that large in the first place without using GPT, since MBR can only handle 2 GB disks.

If you reinstalled and then copied the old files back, the owner information is unknown since the old users don't exist on the new system ( or their IDs may belong to someone else now ).

---

