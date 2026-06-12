---
title: "WDC Advanced format drives and MDADM question"
date: 2012-07-08
forum: Server Platforms
---

### Post by Krupski on 2012-07-08
Hi all,

I've got a little file/web server box that runs Ubuntu 12.04 64 bit server with five 2TB Western Digital hard drives.

The drives are the "Advanced format" type (i.e. 512/4096 byte sectors).

Now, my setup is a RAID-6 array (**/dev/md0**) made up of **/dev/sda** thru **/dev/sde**.

The hard drives have NO partitions. The RAID array is assembled out of **/dev/sda** etc.... NOT **/dev/sda1** etc....

If I check the **/dev/md0** array with parted, it shows that the array starts at byte 0 (I did a **u b** [units/byte] command).

Since the drives are not partitioned, I am assuming that access to them starts at byte 0 as well and, therefore, the 4K alignment requirement is satisfied.

But there's no way (that I know of) to test it. Using parted doesn't work on the **/dev/sd**X drives because they have no partition... so I can't use the "a" (check alignment) command.

Anyone know if this setup is aligned and/or if there's a way I can test to see if it is?

Thanks!

-- Roger

Edit to add: If you're wondering "how do I boot?" - I have a small 16GB solid state PCI-E drive (**/dev/sdf**) that holds the OS exclusively. The hard drives are RAID data only - no OS.

---

### Post by rubylaser on 2012-07-08
It would be better, performance wise, to have partitions properly aligned to sector 4096.  But, if you already have data on the array, and if it performs well enough to saturate a gigabit connection, who cares? :)  What are you read and write speeds to the array?

This will write and then read a 40GB file.

WRITE
```
dd if=/dev/zero of=/raidmountpoint/testfile.out bs=1M count=40000
```

READ
```
dd if=/raidmountpoint/testfile.out of=/dev/null bs=1M
```

---

### Post by Krupski on 2012-07-10
> **rubylaser said:**
> It would be better, performance wise, to have partitions properly aligned to sector 4096.  But, if you already have data on the array, and if it performs well enough to saturate a gigabit connection, who cares? :)  What are you read and write speeds to the array?

This will write and then read a 40GB file.

WRITE
```
dd if=/dev/zero of=/raidmountpoint/testfile.out bs=1M count=40000
```

READ
```
dd if=/raidmountpoint/testfile.out of=/dev/null bs=1M
```


OK here's what I got:

```

root@storage:/# dd if=/dev/zero of=/home/shared/testfile.out bs=1M count=40000
40000+0 records in
40000+0 records out
41943040000 bytes (42 GB) copied, 280.104 s, 150 MB/s
root@storage:/# dd if=/home/shared/testfile.out of=/dev/null bs=1M
40000+0 records in
40000+0 records out
41943040000 bytes (42 GB) copied, 143.454 s, 292 MB/s
root@storage:/#

```

Then I ran the same test on a single drive that I just partitioned and formatted. This drive is not part of the array, and it IS aligned to a 4096 byte boundary:

```

root@storage:/# dd if=/dev/zero of=/home/backup_external/testfile.out bs=1M count=40000
40000+0 records in
40000+0 records out
41943040000 bytes (42 GB) copied, 370.36 s, 113 MB/s
root@storage:/# dd if=/home/backup_external/testfile.out of=/dev/null bs=1M
40000+0 records in
40000+0 records out
41943040000 bytes (42 GB) copied, 339.739 s, 123 MB/s
root@storage:/#

```

Now I'm totally confused.... this isn't what I expected.

(btw, the external test drive is connected via an ESATA cable, so it should be as fast as an internal SATA link... I assume).

---

### Post by rubylaser on 2012-07-10
This isn't a huge shock to me :)  Have you [tuned ]("http://ubuntuforums.org/showthread.php?t=1494846")your array?  If not, I would expect your mdadm performance to rise.  If you have tuned your array, what does the system load look like when you run that test?

Since you have a 5 disk RAID6, you do have a pretty big parity calculation performance hit and you don't have a lot of spindles, so your results aren't terrible, but I think they could be a little better.

---

### Post by Krupski on 2012-07-10
> **rubylaser said:**
> This isn't a huge shock to me :)  Have you [tuned ]("http://ubuntuforums.org/showthread.php?t=1494846")your array?  If not, I would expect your mdadm performance to rise.  If you have tuned your array, what does the system load look like when you run that test?

Since you have a 5 disk RAID6, you do have a pretty big parity calculation performance hit and you don't have a lot of spindles, so your results aren't terrible, but I think they could be a little better.

No, I haven't tuned the array (didn't even know that was possible!).

As far as parity calculations and such, I doubt that those are having much of an impact because the server has a quad core 2.66 ghz CPU which runs under the "conservative" governor and it idles at 1.536 ghz (and doesn't come up during intensive disk I/O). If the RAID overhead were a problem, I would expect to see a lot of CPU usage (right?)

I'm going to have to reboot into Linux (I'm in Windoze right now) and try out the script... then I'll let you know what I get.

And thanks for all the help so far!

-- Roger

(edit to add) Script doesn't work. It hangs in this part:

```

# get all devices
DEVSTR="`grep \"^$MDDEV : \" /proc/mdstat` eol"
while \
 [ -z "`expr match \"$DEVSTR\" '\(\<sd[a-z]1\[[12]\?[0-9]\]\((S)\)\? \)'`" ]
do
  DEVSTR="`echo $DEVSTR|cut -f 2- -d \ `"
done

```

...and I'm not well versed enough in Bash to figure out why. :(

---

### Post by rubylaser on 2012-07-10
Take a look further down that thread.  There are a few revisions of that script.  One of the users was experiencing a similar problem.

---

### Post by Krupski on 2012-07-11
> **rubylaser said:**
> Take a look further down that thread.  There are a few revisions of that script.  One of the users was experiencing a similar problem.

OK did that and ran the script. WHAT AN IMPROVEMENT!!! Take a look:

```

root@storage:/# dd if=/dev/zero of=/home/shared/testfile.out bs=1M count=40000 
40000+0 records in
40000+0 records out
41943040000 bytes (42 GB) copied, 156.268 s, 268 MB/s
root@storage:/# dd if=/home/shared/testfile.out of=/dev/null bs=1M
40000+0 records in
40000+0 records out
41943040000 bytes (42 GB) copied, 145.559 s, 288 MB/s
root@storage:/# 

```

BIG improvement in write speed... almost double!

I took the parameters that the script suggested and put them into a script that I call at boot time. This is what the script turned out to be:

```

root@storage:/# cat /usr/sbin/tune_md
#!/bin/bash
echo 16384 > /sys/block/md0/md/stripe_cache_size
blockdev --setra 128 /dev/sd[abcde]
blockdev --setra 4096 /dev/md0
echo 256 > /sys/block/sda/queue/max_sectors_kb
echo 256 > /sys/block/sdb/queue/max_sectors_kb
echo 256 > /sys/block/sdc/queue/max_sectors_kb
echo 256 > /sys/block/sdd/queue/max_sectors_kb
echo 256 > /sys/block/sde/queue/max_sectors_kb
root@storage:/# 

```

Thanks so much for the tip!

-- Roger

---

### Post by rubylaser on 2012-07-11
No problem :)  Glad you got it working as it should be.

---

### Post by soomon on 2012-11-29
this is good stuff!!
i was able to also double my write speed and my read spead went up by 50%
thanks very much for this thread! :guitar:

---

### Post by rubylaser on 2012-11-29
> **soomon said:**
> this is good stuff!!
i was able to also double my write speed and my read spead went up by 50%
thanks very much for this thread! :guitar:

I'm glad it was able to help you out.

---

