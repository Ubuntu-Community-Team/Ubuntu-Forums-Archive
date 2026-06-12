---
title: "mdadm resync painfully slow"
date: 2014-02-13
forum: Server Platforms
---

### Post by greyday on 2014-02-13
Hi all--I've read through several of the threads on slow resync times and haven't found an answer; I tried setting the min and max values higher and higher, as well as trying the bitmap trick (ended up having the resync drop to about 10% the lowest speed without (literally 12K at one point), destroyed and rebuilt the RAID without).  I am stumped; info on the setup and situation:

Resyncs have always been slow on my server but I always assumed it was a result of the build being a simple dual-atom setup.  I just retired a main workstation and swapped it into the case, it is now a gigabyte P55a-ud3 (1156) with a quad core i7 2.8gHz processor and 8gb ram.  There are three RAIDs, all run off the intel chipset on the motherboard running from a 12 driverack case (2 5-port multipliers and 2 direct), just using straight esata-->sata converters (the system drive is a hardware RAID0 of two small SSDs, running off the marvel chipset--yes, I know it's a faulty sata3 chipset, but both drives are sata2 and seems to deliver decently).  This was by choice, as I was having problems with the pcie esata cards I was using on the old build (multiple drive failures with drives that tested clean using smartmontools).  The new setup is definitely more reliable; however, the lag is ridiculous, the resyncs are running slower than the atom setup, and the system is reporting 7% of RAM used and pretty much 0% cpu usage DURING the rebuild.  I have two RAIDs resyncing and one running:

md0=RAID5, 4x1tb (active)
md1=RAID5, 3x2tb (rebuilding, average speed around 2000k/sec)
md2=RAID6, 5x1.5tb (initial sync after zeroing all superblocks, average speed around 400k/sec)

Currently running headless (removed the graphics card entirely to cut down on energy consumption). Fresh install of Ubuntu 12.04.4 lts. Only added installs are mdadm (obviously), plexmediaserver, and smartmontools.  Did a minimal base install, only selecting samba.

Part of the point of swapping to a less energy-efficient system was to improve performance (and reliability, so I'm 1 for 2 so far). I just don't get why, with all the processing power and memory available, the resyncs are running so slow.  Even allowing for the port multipliers, doing the math all 8 drives working are running at wayyy less than a single drive would.  Any ideas?

---

### Post by greyday on 2014-02-18
Just as an update--md2 had a drive that kept failing; dropped that drive and changed from a RAID6 to a RAID10 this afternoon. It is resyncing fine I guess, around 2000-3000k/s, but now md1 has dropped down to around 200k/s, so general speed still seems way too slow. Any thoughts?

---

### Post by greyday on 2014-02-23
Well, since nobody seems to have any suggestions beyond things I've already tried, I'll just post one final note for anyone who googled this problem like I did but ended up here:

rebuild took a week for a 4gb, 3 drive RAID5.  Everything is fine, data is not corrupt, all good.  Just took way too long, and was ridiculous slow to access during the rebuild (slower than I've ever experienced).

The ONLY thing that sped it up slightly (from, on average, around 1-2mb/s to 2-4mb/s) was increasing the stripe_cache_size significantly.  If your server is not as slow as mine but syncing slowly, that would be a good place to start.  To do it, run:

```
[FONT=Menlo]echo 8192 > /sys/block/md1/md/stripe_cache_size
```

Where 8192 is the new stripe cache size (from the default of 256).  That is just the size I chose, play with it and find what works for you; and md1 is the RAID array, so replace that with whatever yours is numbered.  Hopefully that might help someone.[/FONT]

---

### Post by rubylaser on 2014-02-23
Hello, sorry I missed your thread.  Super slow resyncs like this are typically the result of a hardware issue.  Failing disk, bad SATA connection, or a series of port multipliers.  Can you post the output of the SMART data for each disk, and what do sequential read / write speeds to each array look like?

```

sudo -i
apt-get install smartmontools -y
smartctl -a /dev/sdX

```

```

dd if=/dev/zero of=/mount/path/of/array/testfile.out bs=1M count=64000
sync
dd if=/mount/path/of/array/testfile.out of=/dev/null bs=1M

```

**CAUTION:** This will create a 64GB testfile.  It's large enough to rule out RAM caching on your system.  As an example, this command would look like this on my machine.
```

dd if=/dev/zero of=/storage/testfile.out bs=1M count=64000
sync
dd if=/storage/testfile.out of=/dev/null bs=1M

```

It would also be nice to see your mdadm.conf file
```

cat /etc/mdadm/mdadm.conf

```

---

### Post by greyday on 2014-02-24
Oh, no apologies necessary; I figured there just wasn't a solution.  To answer specifics:

I ran thorough smartctl tests before rebuilding the server on each individual drive, and removed any with the slightest failures for further analysis/less intensive uses.

Read/writes looked pretty normal for WD Green drives.  There doesn't seem to be any lag in performance now that all RAIDs are up and running (final sync ended this afternoon).

I checked all the cables as well; though the esata adapters COULD be creating a slowdown due to the lesser power/push nature of SATA ports vs. eSATA ports.  I'm thinking that the move to onboard SATA ports is the problem, which is sad since I moved from a $60 all in one atom setup to a $250 mobo, but I'm going to do some tests next weekend with the old PCIe cards and see if there's any difference...

HOWEVER, this is my third motherboard, I have tried several tricks with this server, and have NEVER seen good resync rates, even when one of them were all internal drives.  When everything is up and running?  All good.  But resyncs tend to grind things to a halt, and it would be good to fix that...

mdadm.conf output:
```
[FONT=Menlo]# mdadm.conf[/FONT][FONT=Menlo]#[/FONT]
[FONT=Menlo]# Please refer to mdadm.conf(5) for information about this file.[/FONT]
[FONT=Menlo]#[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# by default (built-in), scan all partitions (/proc/partitions) and all[/FONT]
[FONT=Menlo]# containers for MD superblocks. alternatively, specify devices to scan, using[/FONT]
[FONT=Menlo]# wildcards if desired.[/FONT]
[FONT=Menlo]#DEVICE partitions containers[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# auto-create devices with Debian standard permissions[/FONT]
[FONT=Menlo]CREATE owner=root group=disk mode=0660 auto=yes[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# automatically tag new arrays as belonging to the local system[/FONT]
[FONT=Menlo]HOMEHOST <system>[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# instruct the monitoring daemon where to send mail alerts[/FONT]
[FONT=Menlo]MAILADDR root[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# definitions of existing MD arrays[/FONT]
[FONT=Menlo]ARRAY /dev/md/0 metadata=1.2 UUID=3985233e:b96a8e88:32466255:05ae4572 name=monkeyserver:0[/FONT]
[FONT=Menlo]ARRAY /dev/md/1 metadata=1.2 UUID=fe58cecc:f27d8092:368b331b:98dc1cc0 name=monkeyserver:1[/FONT]
[FONT=Menlo]ARRAY /dev/md2 UUID=53593334:e55188a9:6895e992:300f835c[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]# This file was auto-generated on Thu, 13 Feb 2014 01:42:32 -0800[/FONT]
[FONT=Menlo]# by mkconf $Id$[/FONT]

```

---

### Post by rubylaser on 2014-02-24
Your mdadm.conf file looks fine.  I would like to see the smart data on the disks even if they are all healthy, it doesn't hurt to have another set of eyes look at them.  Also, have you had a chance to run the sequential dd test I showed above?  I'd like to see what the sequential throughput looks like on the system.  

As a test on low end hardware, I just setup a test on my dual core Celeron 847 (a very weak processor) with 8GB of RAM with (8) of my old 1TB disks in a RAID6 and I get sync speeds in the 65 MB/s range.  These disks are all attached to an IBM m1015 flashed to IT mode on Ubuntu 12.04 server.  This is why I mentioned that super slow sync speeds are normally bad hardware.  Troubleshooting this is hard for me to do without empirical data to look at, so if you get a chance, I'd love to see the other things I asked for.

---

