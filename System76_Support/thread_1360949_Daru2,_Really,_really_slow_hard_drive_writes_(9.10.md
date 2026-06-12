---
title: "Daru2, Really, really slow hard drive writes (9.10)"
date: 2009-12-21
forum: System76 Support
---

### Post by imhavoc on 2009-12-21
After upgrading to 9.10, I noticed some occasional slowness in the machine, but kept thinking it would get lined out with updates.

The last couple of days, I have been doing some very (very) intensive data manipulation on large files, and the system comes to a crawl.

It seems that my writes to hard drive are bottlenecking the whole system. I just used tar (no compression) to create a 3.4 GB file, which took several minutes to complete, during which time the system was unusable.

Memory and CPU usage were both well below 50% during this time.

This was not a problem until 9.04 and 8.10, so this is something new.

Could it be a problem with my hard drive?

---

### Post by jdb on 2009-12-21
> **imhavoc said:**
> After upgrading to 9.10, I noticed some occasional slowness in the machine, but kept thinking it would get lined out with updates.

The last couple of days, I have been doing some very (very) intensive data manipulation on large files, and the system comes to a crawl.

It seems that my writes to hard drive are bottlenecking the whole system. I just used tar (no compression) to create a 3.4 GB file, which took several minutes to complete, during which time the system was unusable.

Memory and CPU usage were both well below 50% during this time.

This was not a problem until 9.04 and 8.10, so this is something new.

Could it be a problem with my hard drive?

# I'm not using sudo because I'm logged on as root
# root can't read .gvfs if it is mounted
root@dartar:/# umount /home/dad/.gvfs
root@dartar:/# cd /
# linux is a separate file system
root@dartar:/# tar cf /linux/dog.tg --one-file-system .
root@dartar:/# ls -lh /linux/dog.tg 
-rw-r--r-- 1 root root 2.1G 2009-12-21 14:19 /linux/dog.tg

This was on my Daru2 on 9.10
It took 4.5 minutes but the machine was very responsive the whole time.

Edit: some useful info

If this is restored to a blank partition it won't work since it was
tarred from an active partition.
You can make it work by adding a few /dev entries.
An easy way to do this is to find a bootable but not active partition &
```
sudo cp -a /bootable_partition/dev /someplace
```
Then  untar to a blank partition & add the /dev entries:
```
cd /blank_partition
sudo tar xf /linux/dog.tg
sudo cp -a /someplace/dev .
```

BTW, for comparison:

With compression it took 5.5 minutes & the processor was close to 100%
but the system was still responsive.

root@dartar:/# tar cfz /linux/dog.tgz --one-file-system .
root@dartar:/# ls -lh /linux/dog.tgz
-rw-r--r-- 1 root root 861M 2009-12-21 15:04 /linux/dog.tgz



jdb

---

### Post by imhavoc on 2009-12-21
My IOwait states is pegged at 100% any time the system is writing to disk.

---

### Post by jdb on 2009-12-21
> **imhavoc said:**
> My IOwait states is pegged at 100% any time the system is writing to disk.

Are you using ext3 or ext4 partitions???

jdb

---

### Post by imhavoc on 2009-12-21
ext3

---

### Post by imhavoc on 2009-12-21
jdb,

What does your fstab line for the /home (or /) partition look like?

---

### Post by jdb on 2009-12-21
> **imhavoc said:**
> jdb,

What does your fstab line for the /home (or /) partition look like?

/dev/sda1 / ext3 errors=remount-r

I don't use UUIDs & deleted the <dump> & <pass> entries, they default to 0 which is what I want.
I don't use a separate partition for /home but I mount various
other partitions to /data /backup etc. .

jdb

---

### Post by jdb on 2009-12-21
> **imhavoc said:**
> ext3

This is the info on my ext3 partition.

```
21:21:24 ~ dumpe2fs -h /dev/sda1
dumpe2fs 1.41.9 (22-Aug-2009)
Filesystem volume name:   darter
Last mounted on:          <not available>
Filesystem UUID:          919a287c-ccbb-4de4-b545-227c309cad3c
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              704512
Block count:              2815383
Reserved block count:     140769
Free blocks:              2155409
Free inodes:              554442
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      687
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Fri Aug  7 18:11:05 2009
Last mount time:          Mon Dec 21 15:23:26 2009
Last write time:          Mon Dec 21 15:23:26 2009
Mount count:              2
Maximum mount count:      -1
Last checked:             Mon Dec 21 14:04:17 2009
Check interval:           864000 (1 week, 3 days)
Next check after:         Thu Dec 31 14:04:17 2009
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:	          128
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      3fd5216e-92d0-451c-b8cb-535cadf866da
Journal backup:           inode blocks
Journal size:             128M

```

I did a clean install.
Maybe something on your Daru2 got hosed in the upgrade.

jdb

---

### Post by imhavoc on 2009-12-21
Actually, this is a clean install. I'm wondering if there might be something wrong with my hard drive, or somewhere else in my computer...

---

### Post by imhavoc on 2009-12-22
This is a replacement drive. After looking things over, I realize that I replaced a 160GB 1.5 Gb/s SATA drive with a 3 Gb/s SATA drive.

Could this possibly be part of the problem?

I loaded up iotop and I've been watching. It seems that I'm read-limited, not write-limited. It's hitting 2 MB/s for reads most of the time with an occasional peak at ~6.5 MB/s

---

### Post by noctrex on 2009-12-22
Actually, I can confirm the performance drop for 9.10.
I have a mini-ITX system based on a VIA 1.2Ghz CPU, with 2 disks, one for the system and one for various data.
have been using 8.04, 8.10 and 9.04 with no problems whatsoever.
For 9.10, I did a clean install and used ext4 for the root partition, and mounted the existing ext3 data drive on /data.
The system is very responsive, but when accessing the ext3 drive, IOwait is at 100% all the time and the reads are VERY slow. A copy/paste operation for 4 large files didn't took 5 mins with the older ubuntu dists, but now it takes over 20.
Maybe there is a performance bottleneck for ext3... i don't know, but i've been thinking about converting the disk to ext4 also, and see if this problem persists.

---

### Post by jdb on 2009-12-22
> **imhavoc said:**
> This is a replacement drive. After looking things over, I realize that I replaced a 160GB 1.5 Gb/s SATA drive with a 3 Gb/s SATA drive.

Could this possibly be part of the problem?

I loaded up iotop and I've been watching. It seems that I'm read-limited, not write-limited. It's hitting 2 MB/s for reads most of the time with an occasional peak at ~6.5 MB/s

I don't know the stats on my drive, it's the original one.

Typical values during the tar operation:
iowait 45%
read 1.4 M/s
write 1.15 M/s

edit:

I measured these values using iostat.
I just loaded iotop & got bizare values ranging from from > 10 m/s to < 100 K/s

Just for the heck of it I untarred the files I built earlier.
dog.tg took a shade over 2 minutes
dog.tgz took about 1.75 minutes
The system remained responsive

jdb

---

### Post by noctrex on 2009-12-24
formatted a partition to ext4, and now it's official that the performance of ext3 partition is VERY poor on 9.10.
ext3 copy speeds are in the 1-2MB range,
ext4 copy speeds are in the 8-9MB range, just as ext3 was actually on older ubuntu distributions....

---

### Post by imhavoc on 2009-12-24
> **noctrex said:**
> formatted a partition to ext4, and now it's official that the performance of ext3 partition is VERY poor on 9.10.
ext3 copy speeds are in the 1-2MB range,
ext4 copy speeds are in the 8-9MB range, just as ext3 was actually on older ubuntu distributions....

That is not good news.... Oy! Although it is better than bad news. Reformatting my machine was not what I wanted to do for Christmas.

Thanks for the report!

---

### Post by jdb on 2009-12-24
> **imhavoc said:**
> That is not good news.... Oy! Although it is better than bad news. Reformatting my machine was not what I wanted to do for Christmas.

Thanks for the report!

Supposedly mounting an ext3 as an ext4 has some advantages.
I tried it & there was no speed up.

Like you, I'm thinking of going to ext4.

I'm still worried about data lose though.
I do a lot of experimenting & often get the system so locked up I have to do a power reset.
I've heard that ext4 is a lot more prone to cause corruption under those circumstances because
it keeps stuff in memory longer before it writes it to disk.
I'm going to do some reading & see if there's any way to tune it a bit so it's a little more forgiving.

jdb

---

### Post by imhavoc on 2009-12-24
jdb, If you would update this thread when you learn something, I would appreciate it.

noctrex, Thanks for the info!

---

### Post by jdb on 2009-12-24
> **imhavoc said:**
> jdb, If you would update this thread when you learn something, I would appreciate it.

noctrex, Thanks for the info!

From what I've read, any change from the default paramaters may
make an ext4 partition faster but will probably make it less safe.

The problem was pretty bad back in March but patches to the kernel
have improved things considerably.
But it's still more likely for a crash to cause corruption in an ext4
partition than in an ext3 partition.

I'm on the fence, but I think I'm going to wait a little longer.
I'm sure the day will come when all this is just a distant memory.

jdb

---

### Post by imhavoc on 2009-12-24
> **jdb said:**
> I'm on the fence, but I think I'm going to wait a little longer.
I'm sure the day will come when all this is just a distant memory.

(chuckle) I look forward to that day.

Merry Christmas to everyone!

---

### Post by noctrex on 2009-12-27
> **imhavoc said:**
> jdb, If you would update this thread when you learn something, I would appreciate it.

noctrex, Thanks for the info!

np bro.

tried remounting my ext3 partition with any option i can think of (noatime, nodiratime, sync, async) but no luck... might as well as keep my files in drawers and tell my tortoise to fetch em.

to get performance benefits from ext4, you must reformat the partition! only then are the files organized with all the new shiny feats of the filesystem. if you remount ext3 as ext4, all the old files are accessed with the same mechanism as ext3, so no rocket speeds there.

Actually I'm thinking of going back to 8.04 LTS, at least the disk performance was much more solid there.

---

### Post by riseringseeker on 2009-12-27
> **jdb said:**
> 
I do a lot of experimenting & often get the system so locked up I have to do a power reset.

jdb

Instead of holding the power button to restart the system, try this.

Hold down the left Alt key and the SysRq key and while doing so type RSEIUB (case is not significant).  Tom Aaron (who gave me the command) uses the mnemonic of "Raising Skinny Elephants Is Utterly Boring", or, another I have come across is "Restart System Even If Utterly Broken".

The above command is advertised [here]("http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html") to properly shutdown a running system, avoiding leaving files unclosed and the resulting file corruption

---

### Post by jdb on 2009-12-27
> **riseringseeker said:**
> Instead of holding the power button to restart the system, try this.

Hold down the left Alt key and the SysRq key and while doing so type RSEIUB (case is not significant).  Tom Aaron (who gave me the command) uses the mnemonic of "Raising Skinny Elephants Is Utterly Boring", or, another I have come across is "Restart System Even If Utterly Broken".

The above command is advertised [here]("http://mark.koli.ch/2009/02/linux-magic-sysrq-key-r-e-i-s-u-b-reboot-even-if-system-utterly-broken.html") to properly shutdown a running system, avoiding leaving files unclosed and the resulting file corruption

That is really cool, I'd never heard of it before.
Wikipedia has a good writeup on the "Magic SysRq key":

[http://en.wikipedia.org/wiki/Magic_SysRq_key]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

Thanks,

jdb

---

### Post by imhavoc on 2010-02-06
I seem to have solved this problem.

My Daru2 was ordered with 2GB of RAM. 2.5 years ago, that was sufficient for most things.

I finally determined that the slow drive performance was due mostly to memory swapping, and ordered 4GB of RAM for the machine.

With 4GB installed, the machine is snappy, drive performance is acceptable, IOwaitstates are down.

---

