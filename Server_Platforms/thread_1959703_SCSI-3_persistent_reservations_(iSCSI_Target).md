---
title: "SCSI-3 persistent reservations (iSCSI Target)"
date: 2012-04-16
forum: Server Platforms
---

### Post by acidrop on 2012-04-16
I have been wanting to experiment with Windows clustering systems  so I need a free, preferably open source, iSCSI Target that can support 2k3 and 2k8 fail-over and possibly High availability clustering. I have tried the ubuntu iscsi target package in a vmware environment, but it fails at the 2k8 tests.

---

### Post by smarsha on 2012-04-26
I was attempting the same project with the same results.  Any new revelations? or should i just give up?

---

### Post by joeinbend on 2012-06-19
Hey guys,
I'm on the same path: I need a Ubuntu/Debian iSCSI target that supports ISCSI-3 Persistent Reservations. So far I am coming up empty. Anyone find a solution for this?

In common distro's, the only thing I can find is FreeNAS. If anyone recognizes my name, you know I did one of the popular RAID-5 guides around here, using MDADM. I want to keep using that! Let me know if you have solved this one.

---

### Post by Chookah on 2012-07-03
I recently ran into a WORLD OF HURT attempting to use FreeNAS with a Win2008r2 cluster.

[LIST]
[*]Volumes over 2TB would take too long to bring online/offline and would fail cluster validation tests
[*]Randomly (and often) the iscsi persistant reservations would start playing up and refuse to release ownership of the volume to another node
[*]only way to fix was to reboot freenas box multiple times a day
[/LIST]

Do yourself a favor and stay away from FreeNAS & windows clusters.
I found this thread while researching an alternative to freenas lol

---

### Post by rubylaser on 2012-07-04
Here's another idea.  You could use Openindiana + napp-it and use COMSTAR. I don't have any experience using Openindiana with Windows in this setup, but COMSTAR does support SCSI-3 persistent reservations.

---

### Post by joeinbend on 2012-07-04
Hey guys,
I ended up setting up a FreeNAS for iSCSI (version 8.0.4 p3), and it works perfectly. I have a two-node Hyper-V cluster, managed by System Center 2012, VMM. I am able to fail over between the nodes at will, live migrate running VMs between the hosts with no problems. My storage is 6x 1TB drives, running their "RAID-Z", and it works great.

This is an interim solution for me. In the long run, I want to move this back to Ubuntu / Debian, as soon as we can figure something out that supports SCSI-3. The big BIG drawback to FreeNAS, is you cannot expand a "RAID-Z" volume, whereas with MDADM (again, read my guide...) you can extend RAID-5 volumes with additional disks, or larger disks, with no data loss, and remaining online. Can't do that with FreeNAS.

But, until I can do SCSI-3 persistent reservations in a Debian build, I'm stuck with it. (insert "sad trumpet" sound here).

---

### Post by rubylaser on 2012-07-04
You can't expand a vdev in ZFS, but you can add another vdev to an existing array.  Especially, in the case of an enterprise environment, this is less of an issue  than a home fileserver, because you typically plan better for enterprise deployments.  So, if you have a 4 disk raidz, you could add another 4 disk raidz to the pool with no problem. Also, you can replace disks with larger disks and the array will autoexpand to take advantage of the new space once all the disks have been upgraded.  Not nearly as flexible as mdadm, but for all the benefits that come with ZFS, I've really enjoyed using it for the last year (I do still have mdadm based arrays at work and home too).

The main reason, I've avoided FreeNAS for ZFS is it's always had much slower throughput for me than Solaris/Openindiana/Nexanta/EON.  I'd be interested to hear what your network transfer speeds are to your array.  Maybe FreeNAS has finally fixed that problem.

---

### Post by joeinbend on 2012-07-04
In the Enterprise world, I completely agree. Of course at home, we have different storage and budget considerations. Thanks for mentioning that you can in fact grow a RAID-Z by swapping out for larger disks; I was not aware that was an option. I will likely do that soon. So if I go through and swap one by one and allow to rebuild, my existing 6x 1TB array, with 6x 2TB disks, it will auto-grow once that last disk is swapped in? 

If so, that's a good option. 

As for throughput, just from the web GUI, I have seen it sustain up in to the 600 Mb range, for write speeds. I am travelling this week and don't have access to my system right now; do you know if I can do something similar (or same command?) in FreeNAS such as "hdparm -Tt /dev/md0"? I'm happy to test my throughput and post results, if you can advise what testing you would like to see results from.

thanks!

---

### Post by rubylaser on 2012-07-04
> **joeinbend said:**
> In the Enterprise world, I completely agree. Of course at home, we have different storage and budget considerations. Thanks for mentioning that you can in fact grow a RAID-Z by swapping out for larger disks; I was not aware that was an option. I will likely do that soon. So if I go through and swap one by one and allow to rebuild, my existing 6x 1TB array, with 6x 2TB disks, it will auto-grow once that last disk is swapped in? 

If so, that's a good option.

Yes, this is exactly how it will work.  Or, you could extend your array with the second set of 2TB drives and end up with 6x1TB + 6x2TB.  You can combine vdevs that have different sizes without a problem as well (this would give you the equivalent of a RAID50).

> **joeinbend said:**
> As for throughput, just from the web GUI, I have seen it sustain up in to the 600 Mb range, for write speeds. I am travelling this week and don't have access to my system right now; do you know if I can do something similar (or same command?) in FreeNAS such as "hdparm -Tt /dev/md0"? I'm happy to test my throughput and post results, if you can advise what testing you would like to see results from.

thanks!

600Mbps is about 75 MB/s, so that's fairly good.  I would expect that to saturate gigabit with 6 disks, but if you don't have greater than 4GB of RAM in the box, those are fairly good numbers.  I'm not a huge fan of hdparm as a real benchmark, personally, I'd use dd to measure write then read speed.

WRITE
```
dd if=/dev/zero of=/path/to/array/testfile.out bs=1M count=10000
```

READ
```
dd if=/path/to/array/testfile.out of=/dev/null bs=1M
```

iozone is another good test to run.

---

### Post by joeinbend on 2012-07-05
Thanks for the tips, I will do some RW tests when I get back home next week. In my previous setup with Debian and MDADM (on the same physical hardware I am using FreeNAS on now), I would get about 130 MB/sec results from hdparm -Tt /dev/md0. Hopefully I will see comparable results with FreeNAS.

As far as perceived performance, I'm doing pretty well. I run about 25-30 VMs in my lab environment on the two hosts, all VMs reside on iSCSI storage, and I don't get any noticeable lag times on the VMs, and the local disk queues always stay below 1, so I don't seem to be bottlenecking there. My VMs are fairly intense I/O: SQL, Operations Manager, Configuration Manager, and Exchange.

---

### Post by Biggs427 on 2012-07-13
I'm building a storage server for a backup to disk to tape scenario with a Dell precision 490 workstation, 6GB ram, 4x 2TB WD Black drives (WDC2002FAEX) for storage.
 
I gave a try to the latest Freenas version and was dispappointed by the results.  I'm getting around 45-50MB/s using iSCSI for the 4 drives with a raidz configuration.
 
I did try Ubuntu with ZFS for Linux  with the same 4 drives raidz configuration and I'm getting 92MBps with th Gig interface steady at 91%.  All through a crappy TrendNet switch.  With overhead, I'm probably maxing the lan.  I'm gonna give a try to Jumbo frames to see if it helps.  I'm using ietd that shares a 100GB file on the zvol.
 
The only problem I have is to share  a zvol with ietd.  I could create a big file on my tank/backupvol zvol and share it but I'd like to share the zvol.
 
Anybody knows how I could do it?
 
 
 
Anybody know how I could do it?

---

