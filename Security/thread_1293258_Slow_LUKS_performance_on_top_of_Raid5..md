---
title: "Slow LUKS performance on top of Raid5."
date: 2009-10-16
forum: Security
---

### Post by u-slayer on 2009-10-16
I set up my raid 5 server with 4 terabyte drives in raid 5 with an LVM and a LUKS partition on top of that. When I try to read from the encryption layer, it's 6 times as slow as the reading directly from the LVM or the raid device.

Now I know encryption can be slow. But, I tested that theory with a loop device with exactly the same encryption settings and I get transfer rates that are thee times as fast. 

Here are the encryption settings:
```
cryptsetup status x
/dev/mapper/x is active:
  cipher:  aes-xts-plain
  keysize: 256 bits
  device:  /dev/mapper/raid5-x
  offset:  2560 sectors
  size:    5860488704 sectors
  mode:    read/write

```



Here are my hdparm tests:
```
/dev/md127:
 Timing buffered disk reads:  688 MB in  3.00 seconds = 229.23 MB/sec
root@myth:/dev# hdparm -t /dev/raid5/x

/dev/raid5/x:
 Timing buffered disk reads:  680 MB in  3.01 seconds = 226.09 MB/sec
root@myth:/dev# hdparm -t /dev/mapper/x

/dev/mapper/x:
 Timing buffered disk reads:  128 MB in  3.03 seconds =  42.30 MB/sec

/dev/mapper/loop1:
 Timing buffered disk reads:  392 MB in  3.00 seconds = 130.56 MB/sec


```

Is there some setting I missed that will make LUKS work faster? I already doubled my LVM speed with the command: blockdev --setra 4096 /dev/raid5/x Is there a similar command for LUKS?

---

### Post by u-slayer on 2009-10-16
I set up my raid 5 server with 4 terabyte drives in raid 5 with an LVM and a LUKS partition on top of that. When I try to read from the encryption layer, it's 6 times as slow as the reading directly from the LVM or the raid device.

Now I know encryption can be slow. But, I tested that theory with a loop device with exactly the same encryption settings and I get transfer rates that are thee times as fast. 

Here are the encryption settings:
```
cryptsetup status x
/dev/mapper/x is active:
  cipher:  aes-xts-plain
  keysize: 256 bits
  device:  /dev/mapper/raid5-x
  offset:  2560 sectors
  size:    5860488704 sectors
  mode:    read/write

```



Here are my hdparm tests:
```
/dev/md127:
 Timing buffered disk reads:  688 MB in  3.00 seconds = 229.23 MB/sec
root@myth:/dev# hdparm -t /dev/raid5/x

/dev/raid5/x:
 Timing buffered disk reads:  680 MB in  3.01 seconds = 226.09 MB/sec
root@myth:/dev# hdparm -t /dev/mapper/x

/dev/mapper/x:
 Timing buffered disk reads:  128 MB in  3.03 seconds =  42.30 MB/sec

/dev/mapper/loop1:
 Timing buffered disk reads:  392 MB in  3.00 seconds = 130.56 MB/sec


```

Is there some setting I missed that will make LUKS work faster? I already doubled my LVM speed with the command: blockdev --setra 4096 /dev/raid5/x Is there a similar command for LUKS?

---

### Post by u-slayer on 2009-10-17
echo echo echo

---

### Post by aesis05401 on 2009-10-17
Hello, 

Sorry you are having an issue.  Can you tell me what the LUKS partition is sitting on all the way down to the physical volume?  Can you tell me the same thing for the file(s) you are mounting on the loop?

There are a good number of variables here, and I am not sure you should be seeing comparable seek times from the actual LUKS partition as with the loop device.  The first thing you should check is that the things you are comparing are dealing with similar conditions.  This means checking to make sure that the setup for each volume is comparable.  If you aren't careful you can do all sorts of silly things like striping across disks on the same controller for one volume while striping across disks on separate controllers for a second.  The second setup will be much faster.

Additionally, I don't know if you tried running badblocks before getting funky with your layout.  It is typically a good idea when dealing with technology that is big on fault tolerance... the correction part of tolerance will kill your throughput.

Finally, I am not sure where you were pointing that readahead command, but I can't imagine that would do anything positive on a LUKS setup.  I don't know too much about their on-disk specification, but increasing the sequential readahead value sounds like a bad idea...  I think there is also a possible issue that LUKS pads blocks under certain physical circumstances, so that throughput you are seeing could be all that is coming through after it strips the padding.  Depending on how you generated the files that you are mounting on loop this may not be an issue there.

Anyhow, hope this helps.

---

### Post by cariboo on 2009-10-18
Please don't start multiple threads on the same subject, I have merged your two threads.

---

### Post by fackamato on 2010-03-12
This makes me worried.

My friend is planning a setup with 8 1.5TB HDDs on a dedicated hw RAID card set up in RAID5.

The question is wether to run LUKS on that single device, or set up LVM first in 4 parts, run LUKS on each of them, then join them all together with a big LVM (this should gives us increase encryption/decryption performance as you're running 4 instances of kcryptd, but I don't know...)

See [http://lkml.org/lkml/2010/3/12/43](http://lkml.org/lkml/2010/3/12/43) for more info :popcorn:

---

### Post by jonta on 2010-04-10
Hello

I am also a bit interested in this.
I am running a LUKS encrypted twofish 128-bit partition on top of a RAID5 with three 1TB disks

hdparm on raid5 directly (/dev/md0)
Timing buffered disk reads:  354 MB in  3.00 seconds = 117.85 MB/sec

hdparm on LUKS partition (/dev/mapper/md0)
Timing buffered disk reads:  112 MB in  3.05 seconds =  36.72 MB/sec

As the previous posted says, this is quite a decrese in speed.

CPU: QuadCore Intel Xeon X3210  @ 2.13GHz
System: Ubuntu 10.04 beta2 (but same with previous ubuntuversion)
Kernel: 2.6.32-19-generic #28-Ubuntu SMP

---

### Post by u-slayer on 2011-05-10
I just doubled my speed to over 150MB/s. How? I upgraded to 64-bit. Same distro, same array, same lvm, just 64 instead of 32-bit edition.

Wow.

---

### Post by antymat on 2012-01-07
You might as well try changing the stripe_cache_size[FONT=Verdana], like here:
[http://dominik.honnef.co/posts/2011/10/linux_raid___dm_crypt__poor_write_performance/](http://dominik.honnef.co/posts/2011/10/linux_raid___dm_crypt__poor_write_performance/)
[/FONT]

---

