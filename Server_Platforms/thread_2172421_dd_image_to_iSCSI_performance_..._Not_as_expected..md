---
title: "dd image to iSCSI performance ... Not as expected."
date: 2013-09-04
forum: Server Platforms
---

### Post by paraviz on 2013-09-04
Hello all!

I've got an iSCSI server (Ubuntu 13) that seems to be performing great.  I am having one little "issue" ... I do not believe it is affecting the day-to-day performance, but it is very worrying to me, and it's been wasting quite a bit of my time when I've been trying to work on the VM hosts.

Here's the deal.  If I image an iSCSI partition from the initiator, performance is as expected.  If I re-apply that same image to the same iSCSI partition, the process runs at about 4-8MB/s, which is ridiculous, considering the read speed is over 100MB/s.  And I go crazy on 256GB+ partitions.  The iSCSI array is a SATA3-based SSD array, with 8 drives in a RAID0+1 setup.  (FWIW, the RAID is powered by an Intel RAID with 1GB cache, all partitions are LVM, and all but one of the iSCSI targets is in blockio mode.)

When writing "normally" to the partition, from its respective VM for example, the write performance is great.  Only administrative duties, such as applying images, etc., goes at dog-slow speeds.  Read performance seems great at all times.  Write performance though, very puzzling to me ... I need to be able to apply these images faster.

In addition to the poor write performance, if I run an "iotop" while the dd is writing, I often see the read value as twice the speed as the write.  How is that possible?

Am I doing something wrong here?

Any suggestions, thoughts, ideas, etc. are greatly appreciated.  Thank you!
~Laz

---

### Post by M!K3_$ on 2013-09-05
Hello Paraviz,

You mentioned the issue comes up when you are trying to read/write from the same array? It is possible that the disks are wasting lots of time moving the heads here, there and everywhere which is causing your performance to drop.

Are you familiar with the sysstat tools, namely iostat? Sysstat can be configured to keep historical performance statistics (very useful!) but we are concerned with iostat in this case.

Go ahead an install it like this:
```

sudo apt-get install sysstat

```

Once you have it installed, monitor your disk usage with the following command:
```

iostat -d -x 5

```

While monitoring, start up the task which you are experiencing issues with in a different shell and look at at the output of iostat. The last column in the output is disk I/O utilization percentage  - very important! How high does it get?

---

### Post by paraviz on 2014-04-26
Hey there Mike!

Sorry for my very late reply.  I actually thought I had notifications set to email me.  Doh ... (While I stupidly felt like the forums were abandoning me ... Oh man.)

The main thing is that the array is built using eight 480GB Intel DC3500 solid state drives.  I went this way specifically to avoid the physical movement of the heads.

I am going to check out the tools that you recommend and see what type of data comes out of it.

Thank you so much for your response.  Again, my apologies for letting it slip through!  Take care.
~Laz

---

