---
title: "Slow mdadm RAID 5 write speeds"
date: 2010-08-13
forum: Server Platforms
---

### Post by steve0961 on 2010-08-13
I recently set up a 3 TB software RAID 5 array using Ubuntu 10.04 on 3 WD 1.5 TB green hard drives. All 3 drives were first run through the WD Data Lifeguard Diagnostic extended test and passed. The OS is installed to a 32 GB SSD and the RAID 5 array will be used as file server. I used the Palimpsest disk utility to set the array up (which uses mdadm) because I prefer using a GUI when it’s possible to. The array took ~8 hours to build and after I figured out how to fix a problem with the partitions being misaligned (due to the stripe size), I finally got the array partitioned and ready for usage. I ran the read benchmark test in the disk utility and got speeds basically at what I was expecting, an average of 136.5 MBps. I ran out of onboard SATA ports with the new array installed, so I have to copy over all the data I want on the array from the old 1 TB drive via an external USB enclosure. When I started the transfer (~300 GB) it zoomed through the first 700 MB or so fairly quickly, and then came to a screeching halt. It would then only write 50-100 MB at a time then pause for a few seconds. It kept repeating this process and I gave up after 5 GB.

I then tried to narrow down what the problem is by copying a ~6 GB folder from the external drive to the SSD that the OS is installed on. It zoomed right through the transfer at a steady 30-50 MBps. When I tried to copy the folder from the SSD to the RAID 5 array, it did the exact same thing as before (zoom through the first 700 MB and then go extremely slow). I then decided to delete the partition and the partition table from the array entirely and run the read/write test in the Disk Utility. Here are the results:

[IMG]http://imgur.com/WNDd4.png[/IMG]

I don’t understand how the write speeds can be this bad. I then reformatted the array and tried again with similar results. I checked the system monitor with the transfer running and nothing is maxing out the CPU or RAM, nor are any of the relevant processes doing anything out of the ordinary. I was told on a different forum that nautilus is a dependency of the Palimpsest disk utility and to try a different file manager. I downloaded and installed the Dolphin file manager and it gave the same results. I’m at a loss of what to do here; I can’t even think of what else the problem could be. Any help would be greatly appreciated.

---

### Post by Go3Team on 2010-08-16
I hate the WD Green Drive for this very reason.  My experience with the ones I have is they are very slow writers.  Speed started off ok, but always tapered off to a very slow speed.

---

### Post by LightningCrash on 2010-08-16
Have you tried just a plain dd to test it?

```
dd if=/dev/urandom of=/mnt/array/file.out bs=1M count=10240
```


then in another terminal
```
watch pkill -USR1 dd
```

It will give you transfer statistics (in MB/sec) in the dd window while the writing is going on...

It almost sounds like it's rebuilding the array in the background

```
cat /proc/mdstat
```
and see if it's ok...

---

### Post by Groodles on 2010-08-17
Are you copying the data between the USB drive and the Array via the Desktop GUI?

I think something in the Desktop environment doesn't like USB as I had a similiar problem.  To check this, open a terminal window and copy a large file using the CLI.

If it's suddenly faster, then it's the Desktop USB implementation that's the bottleneck, not the drive.

---

### Post by lg21 on 2012-06-22
Hello,


Got 3x 2TB WD Green EARX in RAID 5, have made some tests, results (sry for PL lang on screen):

[IMG]http://golcz.pl/.tmp/ubu.jpg[/IMG]


Some tests:
[PHP]
$ echo "Creating 1 GB file on RAID5" ; time dd if=/dev/urandom bs=1024 count=1000000 of=1GB.file ; echo "Copying 1GB file from RAID to SSD" ; time cp 1GB.file ~ ; rm ~/1GB.file ; echo "Creating 1GB file on SSD" ; time dd if=/dev/urandom bs=1024 count=1000000 of=~/1GB.file ; echo "Copying 1GB file from SSD to RAID" ; time cp ~/1GB.file /media/raid/
Creating 1 GB file on RAID5
1000000+0 records read
1000000+0 records written
copied 1024000000 bytes (1,0 GB), 61,0981 s, 16,8 MB/s

real    1m1.106s
user    0m0.084s
sys    0m55.679s
Copying 1GB file from RAID to SSD

real    0m7.526s
user    0m0.004s
sys    0m0.684s

Creating 1GB file on SSD
1000000+0 records read
1000000+0 records written
copied 1024000000 bytes (1,0 GB), 57,3593 s, 17,9 MB/s

real    0m57.361s
user    0m0.060s
sys    0m56.364s
Copying 1GB file from SSD to RAID

real    0m7.852s
user    0m0.008s
sys    0m0.780s
[/PHP]Generating urandoms is not good test of RAID speed. ;-)

I've used ext4 on RAID, PC is i7 with 8 GB of RAM, some basic tests and tuning have been described on my HP: [http://golcz.pl/Docs/HOWTO_RAID5_with_mdadm.txt](http://golcz.pl/Docs/HOWTO_RAID5_with_mdadm.txt)


Maybe someone will find this usefull at it took me some time to tune it.

cheers

---

### Post by rubylaser on 2012-06-22
I would strongly suggest [tuning your array]("http://ubuntuforums.org/showthread.php?t=1494846") if you haven't.  It really does make a big difference for most users.

---

