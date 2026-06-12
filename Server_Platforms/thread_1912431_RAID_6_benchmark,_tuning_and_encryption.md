---
title: "RAID 6 benchmark, tuning and encryption"
date: 2012-01-20
forum: Server Platforms
---

### Post by alfonso78 on 2012-01-20
ok since I was rebuilding my RAID 6 array anyway, I decided to do some tests to see how much tuning makes a difference in performances.

big thanks to [rubylaser]("http://ubuntuforums.org/search.php?searchid=85091903") for helping me understand a lot of these things!

background:
- I have a RAID 6 of 4x disks Seagate Barracuda Green SATA Revision 3.0 &#8211; 2 TB.
- I already managed to correctly align partitions for the 4k issue ([click here for more info]("http://ubuntuforums.org/showpost.php?p=11619661&postcount=1"))

Now I'd like to understand how much tuning the filesystem changes things and how much LUKS encryption impacts performances.

For each test, I will run the following simple script to test speed:

```
#!/bin/bash
#
# Please note this test requires 30 GB of free space
# in your RAID md volume
#
# this is your mount point for the RAID
MNT=/storage
# this are the disks which are part of your drive
# use "cat /proc/mdstat" if you are not sure
# and don't worry because if you type a wrong 
# list here it only affect the tests, not your system
RAID=/dev/sd[b-e]
if ! [ -d $MNT/lost+found ]
then
  echo
  echo $MNT is not a file system! Did you forget to mount?
  echo ABORT
  exit 1
fi
echo 
echo flush the cache before each test
echo writing tests:
hdparm -f $RAID > /dev/null
dd if=/dev/zero of=$MNT/testfile1.out bs=100kB count=100000 2>&1 | grep copied
hdparm -f $RAID > /dev/null
dd if=/dev/zero of=$MNT/testfile2.out bs=1MB count=10000 2>&1 | grep copied
hdparm -f $RAID > /dev/null
dd if=/dev/zero of=$MNT/testfile3.out bs=10MB count=1000 2>&1 | grep copied
echo reading tests:
hdparm -f $RAID > /dev/null
dd if=$MNT/testfile1.out of=/dev/null bs=100kB count=100000 2>&1 | grep copied
hdparm -f $RAID > /dev/null
dd if=$MNT/testfile2.out of=/dev/null bs=1MB count=10000 2>&1 | grep copied
hdparm -f $RAID > /dev/null
dd if=$MNT/testfile3.out of=/dev/null bs=10MB count=1000 2>&1 | grep copied
rm $MNT/testfile1.out
rm $MNT/testfile2.out
rm $MNT/testfile3.out

```

Also note these are not scientific tests at all, just informative...
so I don't try to overwrite everytime the disks or try the test many times...
This is just to get a general idea...

```
# mkfs.ext4 /dev/md0
# mount /dev/md0 /storage
# bash /path/to/script.sh
flush the cache before each test
writing tests:
10000000000 bytes (10 GB) copied, 57.2609 s, 175 MB/s
10000000000 bytes (10 GB) copied, 60.5786 s, 165 MB/s
10000000000 bytes (10 GB) copied, 61.162 s, 164 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 51.9925 s, 192 MB/s
10000000000 bytes (10 GB) copied, 51.5314 s, 194 MB/s
10000000000 bytes (10 GB) copied, 50.8105 s, 197 MB/s
# umount /storage

```
for the next test we will give some parameters to mkfs
(if you wonder why these parameters, check [http://ubuntuforums.org/showpost.php?p=11621331&postcount=6](http://ubuntuforums.org/showpost.php?p=11621331&postcount=6) )
the tool linked on that page calculates stride and stripe-width as follows:
stride = chunk size / fs blocksize
stripe width = stride * number of EFFECTIVE drives in RAID array (so total - 2 for RAID 6, total - 1 for RAID 5 and so on)

in fact I realized that **for my particular system** this test is pointless since mkfs.ext4 already assumes the right options for block, stride and stripe width.
if you wonder what are the settings of your md device, use dumpe2fs -h /dev/md0

```
# mkfs.ext4 -b 4096 -E stride=16,stripe-width=32 /dev/md0
# mount /dev/md0 /storage
# bash /path/to/script.sh
flush the cache before each test
writing tests:
10000000000 bytes (10 GB) copied, 56.7898 s, 176 MB/s
10000000000 bytes (10 GB) copied, 56.8056 s, 176 MB/s
10000000000 bytes (10 GB) copied, 58.2627 s, 172 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 51.9094 s, 193 MB/s
10000000000 bytes (10 GB) copied, 50.1558 s, 199 MB/s
10000000000 bytes (10 GB) copied, 50.1116 s, 200 MB/s

```
you can see... very similar results...

I tried a couple of hours later and I can confirm the test is a bit unstable:

```
flush the cache before each test
writing tests:
10000000000 bytes (10 GB) copied, 63.3618 s, 158 MB/s
10000000000 bytes (10 GB) copied, 66.4716 s, 150 MB/s
10000000000 bytes (10 GB) copied, 65.469 s, 153 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 62.009 s, 161 MB/s
10000000000 bytes (10 GB) copied, 63.7376 s, 157 MB/s
10000000000 bytes (10 GB) copied, 60.9301 s, 164 MB/s

```
but since I test everytime just after creating the file system with mkfs
I think it still gives some indications...

Now, an other topic. Tuning hard disk hardware settings...
Look at [this post]("http://ubuntuforums.org/showpost.php?p=11622143&postcount=22")

Please note that these changes do not resist reboot. Let's first see what happens when you run the script...

I'm running my version of the script using these parameters:

```
## parameters ##
LOGFILE=/tmp/tune_raid.log      # just a log file
BLOCKSIZE=4                     # of file system in kb
NCQ=disable                     # disable, enable. ath. else keeps current setting
NCQDEPTH=31                     # 31 should work for almost anyone
FORCECHUNKSIZE=true             # force max sectors kb to chunk size > 512
DOTUNEFS=true                   # run tune2fs, ONLY SET TO true IF YOU USE EXT[34]
EXECUTE=false                   # if "true", run actual commands. Otherwise only inform you

```
I'm only pasting relevant parts:

```
RUN blockdev --setra 1024 /dev/sdb /dev/sdc /dev/sdd /dev/sde
your current value for readahead is 256 256 256 256
RUN blockdev --setra 4096 /dev/md0
your current value for readahead is 512
RUN echo 128 > /sys/block/md0/md/stripe_cache_size
current value of /sys/block/md0/md/stripe_cache_size is 256
RUN echo 64 > /sys/block/sde/queue/max_sectors_kb
current value of /sys/block/sde/queue/max_sectors_kb is 512
RUN echo 64 > /sys/block/sdc/queue/max_sectors_kb
current value of /sys/block/sdc/queue/max_sectors_kb is 512
RUN echo 64 > /sys/block/sdd/queue/max_sectors_kb
current value of /sys/block/sdd/queue/max_sectors_kb is 512
RUN echo 64 > /sys/block/sdb/queue/max_sectors_kb
current value of /sys/block/sdb/queue/max_sectors_kb is 512
RUN echo 1 > /sys/block/sde/device/queue_depth
current value of /sys/block/sde/device/queue_depth is 1
RUN echo 1 > /sys/block/sdc/device/queue_depth
current value of /sys/block/sdc/device/queue_depth is 1
RUN echo 1 > /sys/block/sdd/device/queue_depth
current value of /sys/block/sdd/device/queue_depth is 1
RUN echo 1 > /sys/block/sdb/device/queue_depth
current value of /sys/block/sdb/device/queue_depth is 1

```
you can see almost all parameters are different from the ones the script suggests
So I will now run it with EXECUTE=true and run the benchmark script again.
I also recreated the file system with mkfs after changing the value to 
better confront tests.

```
flush the cache before each test
writing tests:
10000000000 bytes (10 GB) copied, 177.563 s, 56.3 MB/s
10000000000 bytes (10 GB) copied, 178.791 s, 55.9 MB/s
10000000000 bytes (10 GB) copied, 180.766 s, 55.3 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 58.111 s, 172 MB/s
10000000000 bytes (10 GB) copied, 57.537 s, 174 MB/s
10000000000 bytes (10 GB) copied, 58.9937 s, 170 MB/s

```
so you can see the tuning didn't really go well.
so now I'm setting everything as it was:

```
blockdev --setra 256 /dev/sdb /dev/sdc /dev/sdd /dev/sde
blockdev --setra 512 /dev/md0
echo 256 > /sys/block/md0/md/stripe_cache_size
echo 512 > /sys/block/sde/queue/max_sectors_kb
echo 512 > /sys/block/sdc/queue/max_sectors_kb
echo 512 > /sys/block/sdd/queue/max_sectors_kb
echo 512 > /sys/block/sdb/queue/max_sectors_kb

```
and run the tests again:

```
flush the cache before each test
writing tests:
10000000000 bytes (10 GB) copied, 62.8404 s, 159 MB/s
10000000000 bytes (10 GB) copied, 63.1712 s, 158 MB/s
10000000000 bytes (10 GB) copied, 61.4708 s, 163 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 54.5586 s, 183 MB/s
10000000000 bytes (10 GB) copied, 57.4676 s, 174 MB/s
10000000000 bytes (10 GB) copied, 55.2215 s, 181 MB/s

```
so I can confirm that the suggest tuning is actually negative for my system.

Final note: the size of files you copy during the test
greatly changes results. 
I tried to copy 1GB instead of 10GB and see what happens:

```
flush the cache before each test
writing tests:
1000000000 bytes (1.0 GB) copied, 7.18986 s, 139 MB/s
1000000000 bytes (1.0 GB) copied, 6.64327 s, 151 MB/s
1000000000 bytes (1.0 GB) copied, 6.14189 s, 163 MB/s
reading tests:
1000000000 bytes (1.0 GB) copied, 0.243477 s, **4.1 GB/s**
1000000000 bytes (1.0 GB) copied, 0.234785 s, **4.3 GB/s**
1000000000 bytes (1.0 GB) copied, 0.338234 s, **3.0 GB/s**
```

so you can see that the reading went incredibly faster...
not sure which is the real value: 180 MB/sec or 4GB/sec?
I guess they are both real...
**UPDATE:** as someone made me notice, the super fast speed with 1GB is probably thanks to cache (I have 4GB of RAM).

next post will cover the test after encryption

---

### Post by alfonso78 on 2012-01-26
After these test I did some more optimization (I wrote [a separate post about tuning]("http://ubuntuforums.org/showthread.php?p=11646960")) and at the end I got the following performances:

```
flush the cache before each test
writing tests:
10000000000 bytes (10 GB) copied, 43.2269 s, 231 MB/s
10000000000 bytes (10 GB) copied, 42.6841 s, 234 MB/s
10000000000 bytes (10 GB) copied, 42.7605 s, 234 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 47.1383 s, 212 MB/s
10000000000 bytes (10 GB) copied, 45.6447 s, 219 MB/s
10000000000 bytes (10 GB) copied, 47.9234 s, 209 MB/s

```

And now you can see that encryption has a huge impact on performances.

To encrypt I used the default settings:

```
sudo cryptsetup --verbose --verify-passphrase luksFormat /dev/md0
```

```
$ sudo cryptsetup status storage
/dev/mapper/storage is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/md0
  offset:  2304 sectors
  size:    7814047232 sectors
  mode:    read/write

```

and these are the results:

```
flush the cache before each test
writing tests:
10000000000 bytes (10 GB) copied, 77.0688 s, 130 MB/s
10000000000 bytes (10 GB) copied, 78.0028 s, 128 MB/s
10000000000 bytes (10 GB) copied, 78.8374 s, 127 MB/s
reading tests:
10000000000 bytes (10 GB) copied, 108.115 s, 92.5 MB/s
10000000000 bytes (10 GB) copied, 108.255 s, 92.4 MB/s
10000000000 bytes (10 GB) copied, 108.135 s, 92.5 MB/s

```

what's impressive is that writing seems less penalized than reading. I'm really surprised.

---

