---
title: "RAID (mdadm) Degrades when copying files to drives"
date: 2013-07-11
forum: Server Platforms
---

### Post by joeluk on 2013-07-11
We have a Ubuntu 12.04 LTS server which is configured with a 2 disk software 1 RAID (mdadm). The disks are 3TB and partitioned with a 1MB GPT partition and with the remaining assigned to the RAID. The RAID partition is then allocated as LVM Volume Group and hosts three logical partition for the /boot, /, swap. Following the system being built we tested it by removing a disk and all worked well. We then replaced the disk and re-add the disk back into the RAID.
We have now installed SAMBA on the system and are trying to copy 200Gb of data to a subfolder of the root partition. Every time we do this the RAID degrades and one of the partitions sda2 or sdb2 drops off (removed).  I can't see any errors in the logs as to the cause for this.

Recommendations or suggestions as to where we may find the cause would be greatly appreciated.

---

### Post by CharlesA on 2013-07-11
Sounds like one of your drives may be dying. Have you check the SMART data for both drives?

```
sudo smartctl -a /dev/sdXY
```

It would probably also be a good idea to run a extended test on them as well.

```
sudo smartctl --test=long /dev/sdXY
```

Not esure how to do a verify with mdadm, but it would be a good idea to do one.

---

### Post by rubylaser on 2013-07-11
Checking an array can be done like this
```
[COLOR=#000000]echo check > /sys/block/md0/md/sync_action[/COLOR]
```

Also, what do these show?
```

cat /proc/mdstat

```

```

cat /etc/mdadm/mdadm.conf

```
```

mdadm -E /dev/sd[ab]2

```

When a disk drops out, it should show up in dmesg. Also, you will want to configure email alerts, because a degraded array should trigger an email to the system admin.

---

### Post by joeluk on 2013-07-11
Thanks for the fast reply Charles,

FYI - This is a new HP ML350p server (new disks).  I will run a SMART test against the server to be sure, however, the strange thing is that it seems to alternative between sda2 & sdb2 that fails. 

I wondered if there was an issue with the RAID caused by the initial disk (sda2) being removed.  I can't be sure on the exact steps we took when setting things up, however, I know the server was rebooted before it had finished re-syncing the drives (as we needed to relocate it) and from memory, I believe it booted from sda2 (the disk that was initial removed - could I be wrong), when I ran the re-add again it would have synced sdb2 with sda2. 

My questions are:
1. Is it likely the above is the issue
2. Would it be worth totally removing the degraded RAID, running a fsck and recreating the RAID from scratch.
3. The server was set-up with the use of GPT, 3TB disks, LVM, mdadm RAID, are there any obvious do's, don'ts or best practices we should look at.

Thanks for helping.  I will try the above suggestions along with any other suggestions tomorrow.

---

### Post by joeluk on 2013-07-11
Many thanks Rubylaser. I will look at this along with CharlesA suggestions tomorrow.

---

### Post by CharlesA on 2013-07-11
> **joeluk said:**
> 
My questions are:
1. Is it likely the above is the issue
2. Would it be worth totally removing the degraded RAID, running a fsck and recreating the RAID from scratch.
3. The server was set-up with the use of GPT, 3TB disks, LVM, mdadm RAID, are there any obvious do's, don'ts or best practices we should look at.

Thanks for helping.  I will try the above suggestions along with any other suggestions tomorrow.

I can't answer 1 or 2 as I don't use mdadm (yet), but as far 3, I found these tutorials very helpful when it comes to showing you the right way to create an array with mdadm:
[http://zackreed.me/articles?tag_id=22](http://zackreed.me/articles?tag_id=22)

The commands will be different as those are creating a RAID5 array and you are just using a RAID1.

---

