---
title: "Raid 0+1 Using  Webmin (mdadm)"
date: 2019-02-20
forum: Server Platforms
---

### Post by soulreaper11207 on 2019-02-20
So I have 3 1tb drives that I want to stripe together. Then I want to mirror this to a 3 tb drive. I tried doing this in Webmim's GUI version of mdadm. But it ends up using the 3tb as the primary and mirroring to the stripe of three. Any ideas on how I can get this done? I know I can just do a 0 of the three and then rysnc it to the one, but I'm stubborn lol. Thanks for any help.

---

### Post by darkod on 2019-02-20
I would never create any raid using webmin. It's not supported or dependable.

Have you tried doing this using ssh session and CLI?

---

### Post by soulreaper11207 on 2019-02-20
Yes it still does the same thing. I create the stripe and then and it to a mirror  md0 with sdb. Now I have swapped the order and Got a file system error. There are no partitions on that 3tb drive. Does that matter?

---

### Post by darkod on 2019-02-20
I always use partitions with mdadm, even when using the whole disk. Make a gpt table on the 3TB disk and create one big partition on it. Don't create a filesystem, just a partition. Then try it again.

I'm not 100% it works, I have never tried making an array from a partition and another array.

Try using --verbose with the --create command, it might give you more info why it fails.

---

### Post by soulreaper11207 on 2019-02-20
lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT              NAME        SIZE FSTYPE            TYPE  MOUNTPOINT
loop0        91M squashfs          loop  /snap/core/6350
loop1        91M squashfs          loop  /snap/core/6405
sda       931.5G                   disk
&#9492;&#9472;sda1    931.5G linux_raid_member part
  &#9492;&#9472;md0     2.7T linux_raid_member raid0
    &#9492;&#9472;md1   2.7T                   raid1
sdb         2.7T linux_raid_member disk
&#9492;&#9472;md1       2.7T                   raid1
sdc       931.5G                   disk
&#9492;&#9472;sdc1    931.5G linux_raid_member part
  &#9492;&#9472;md0     2.7T linux_raid_member raid0
    &#9492;&#9472;md1   2.7T                   raid1
sdd       931.5G                   disk
&#9492;&#9472;sdd1    931.5G linux_raid_member part
  &#9492;&#9472;md0     2.7T linux_raid_member raid0
    &#9492;&#9472;md1   2.7T                   raid1
sde       149.1G                   disk
&#9500;&#9472;sde1        1M                   part
&#9492;&#9472;sde2      149G ext4              part  /
 
This is what happened after I did what you had suggested. It still looks like it is setting the sbd as the primary of the mirror instead of the raid device md0. Like I stated before, I am trying to mirror the triple stripe to the single 3tb sdb disk.

---

### Post by darkod on 2019-02-21
What about
```
cat /proc/mdstat
```

What is the output?

And please post text output in CODE tags, it keeps formatting and is better to read.

---

### Post by soulreaper11207 on 2019-02-25
I ended up just Raid 0 and scheduled a daily rsync to the 4th drive as a fail over back up. But thanks for the info. 

Here is that output:
[HTML]cat /proc/mdstat
Personalities : [raid0] [linear] [multipath] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdd1[2] sdc1[1] sda1[0]      
           2929886208 blocks super 1.2 512k chunks
[/HTML]

---

