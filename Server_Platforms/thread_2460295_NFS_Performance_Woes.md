---
title: "NFS Performance Woes"
date: 2021-04-06
forum: Server Platforms
---

### Post by dwhickok on 2021-04-06
_**Environment**_
Ubuntu 18.04.5 LTS server
4.15.0-140-generic
Two disks:  30GB root (/) and 16TB /dev/sdb1 (ext4)
NFSv3
ESXi 6.7 virtualized environment.
Nimble AF-80 storage (fibre channel)

/etc/exports
    @servers1(rw,no_auth_nlm,insecure,async,no_subtree_check) 

[U][B]Symptoms
[/B][/U]This system has a single filesystem exported via NFS to a number of U16 hosts.  Starting a few weeks ago, every few days it will just stop processing I/O.  I've looked at the storage array and it's not receiving any I/O requests.  The CPU, memory, disk, etc. stats within vSphere (and within htop) appear as if the system isn't doing anything at all.  I've tried restarting the NFSd service, have looked at thread counts, etc. but a reboot is the only thing that returns performance to normal immediately.  All cues point to something within the OS or its configuration but nothing has presented as a likely cause.  

Here's one stat that's indicative of the problem:

After 3-4 days, iotop reports the following:
```
1172 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [nfsd]
  1163 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [nfsd]
  1157 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [nfsd]
  1205 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [nfsd]
  1189 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [nfsd]
  1164 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [nfsd]
  1212 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [nfsd]
  1197 be/4 root        0.00 B/s    0.00 B/s  0.00 % 99.99 % [nfsd]

```

Following a reboot (no other changes), performance returns to normal:
   [HTML]969 be/4 root        2.29 M/s    5.03 M/s  0.00 %  6.33 % [nfsd]
   972 be/4 root        2.70 M/s    9.91 M/s  0.00 %  6.00 % [nfsd]
   970 be/4 root        2.16 M/s    9.21 M/s  0.00 %  5.19 % [nfsd]
   968 be/4 root     1920.71 K/s    5.28 M/s  0.00 %  4.26 % [nfsd]
   967 be/4 root     1504.36 K/s    6.63 M/s  0.00 %  4.02 % [nfsd]
   966 be/4 root      958.39 K/s    5.53 M/s  0.00 %  2.87 % [nfsd]
   959 be/4 root      903.40 K/s    9.08 M/s  0.00 %  2.13 % [nfsd]
   965 be/4 root      785.56 K/s    4.45 M/s  0.00 %  2.13 % [nfsd][/HTML]


Any thoughts or leads are very much appreciated!!!

---

### Post by LHammonds on 2021-04-06
Started a few weeks ago?  Was there a kernel update around that time?  Are you on the same kernel?  Can you revert back to the prior kernel (1st option) or update to a newer kernel (2nd option)

**EDIT:** I remembered I still have an 18.04 server that will update itself daily.  Looking at the kernels installed, here is what I have:

```
ls -l /boot/vm*
-rw------- 1 root root 8396448 Mar 15 18:03 /boot/vmlinuz-4.15.0-139-generic
-rw------- 1 root root 8396448 Mar 19 08:26 /boot/vmlinuz-4.15.0-140-generic
```

Based on file date, looks like the 4.15.0-140 kernel released about 2.5 weeks ago and the prior kernel was only a few days before that.

Not sure if this helps but based on my apt logs, the following kernels first showed up on my system on these dates:

2021-01-21 - 4.15.0-134
2021-01-27 - 4.15.0-135
2021-02-24 - 4.15.0-136
2021-03-16 - 4.15.0-137
2021-03-20 - 4.15.0-139
2021-03-25 - 4.15.0-140

LHammonds

---

### Post by TheFu on 2021-04-06
> **dwhickok said:**
> 
Any thoughts or leads are very much appreciated!!!
If U16 is Ubuntu 16.04, it is passed time to migrate to 18.04 or 20.04.  Support for 16.04 ends this month. It isn't worth troubleshooting anything on 16.04 at this point.  [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)  On my 18.04 NFS server, I run:
```
$ ubuntu-support-status 
Support status summary of 'istar':

You have 1454 packages (62.4%) supported until April 2023 (Canonical - 5y)
You have 512 packages (22.0%) supported until April 2021 (Community - 3y)
You have 2 packages (0.1%) supported until April 2021 (Canonical - 3y)
```

Why force NFSv3 when NFSv4 has been production ready since 2005 and has a number of enhancements for both security and performance?
You've lost me on what system is actually running the NFS server. As I read the summary, seems ESXi is providing NFS.  If the NFS server is an Ubuntu VM, how does it efficiently access the block storage?  Hopefully, not using vmdk files, but raw, block storage, access or a PCIe controller passthru?

I only run NFS clients in VMs.  NFS servers are on real hardware ... er ... for performance reasons.

Ok, sorry for all the junk below. I got into this a little more than I should have. You can ignore all of it - or not.

Were I troubleshooting this, I'd start with performance of the disks and network as separate problems.  Then I'd add in nfsstat and run tests from an NFS client using something like fio or bonnie++, and locally perform the same tests with fio or bonnie++.   [https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/](https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/) has some test step, explanations and results.

The exact command:
```
$ fio --name=random-write --ioengine=posixaio --rw=randwrite --bs=4k \
    --numjobs=1 --size=4g --iodepth=1 --runtime=60 --time_based \
    --end_fsync=1
```
The test file is created in the CWD. I didn't run as root. There is overhead in using a normal userid, but for NFS, remote root gets mapped to nobody, so it only seemed fair.

From an NFS client using virtio for networking and disk controllers, inside a VM on a different physical machine that the NFS server, the first test from Ars had these 2 major lines of output:
```
write: IOPS=3544, BW=13.8MiB/s (14.5MB/s)(1191MiB/86041msec); 0 zone resets
WRITE: bw=13.8MiB/s (14.5MB/s), 13.8MiB/s-13.8MiB/s (14.5MB/s-14.5MB/s), io=1191MiB (1249MB), run=86041-86041msec
```

On the physical system (nfs server), same directory, same disk, 
```
write: IOPS=1927, BW=7710KiB/s (7895kB/s)(866MiB/115075msec)
WRITE: bw=7710KiB/s (7895kB/s), 7710KiB/s-7710KiB/s (7895kB/s-7895kB/s), io=866MiB (909MB), run=115075-115075msec
```
So, the NFS was faster.
On the VM host (I use KVM), a much faster system with better CPU, RAM, and networking, same directory, same NFS disk,
```
write: IOPS=3445, BW=13.5MiB/s (14.1MB/s)(1712MiB/127224msec)
WRITE: bw=13.5MiB/s (14.1MB/s), 13.5MiB/s-13.5MiB/s (14.1MB/s-14.1MB/s), io=1712MiB (1795MB), run=127224-127224msec
```
I didn't run 10 runs on each system, nor did I reboot or turn off other jobs running on all the installs so this is just FYI.  Basically the systems were doing what they normally do on a Tuesday afternoon already.

My exports looks like this:
```
/d/D1   regulus(rw,async,root_squash)
```
On the clients, I use autofs to mount NFS when requested. That looks like this:
```
/d/D1 -fstype=nfs,proto=tcp,intr,rw,async  istar:/d/D1
```

LVM is used on D1 with ext4 file system.
The drive is a HGST HUS726T4TALA6L4. That's an Ultrastar DC HC310 7200rpm 4TB HDD - basically a WD-Gold Series HDD.

I got curious - my NFS server is a 5 yr old dual core Pentium with over 30TB of disks connected, and a fairly crappy NIC. I've been meaning to swap in an Intel PRO/1000 or i210/i211 NIC for a few years.  It's on the TODO list. Promise. 

Re-ran the tests on my main VM host which has a cheap HDD and ok SATA SSD.   For the HDD:
```
write: IOPS=4891, BW=19.1MiB/s (20.0MB/s)(2794MiB/146229msec)
WRITE: bw=19.1MiB/s (20.0MB/s), 19.1MiB/s-19.1MiB/s (20.0MB/s-20.0MB/s), io=2794MiB (2930MB), run=146229-146229msec
```
For the m.2 SATA-SSD:
```
write: IOPS=54.8k, BW=214MiB/s (224MB/s)(13.3GiB/63784msec)
WRITE: bw=214MiB/s (224MB/s), 214MiB/s-214MiB/s (224MB/s-224MB/s), io=13.3GiB (14.3GB), run=63784-63784msec
```

Hummm.

Because I like bad results, run the same random block test on another NFS server here. It is a Core i5-750 from 2010 and has a few RAID1 arrays. 
Locally, on the real hardware:
```
write: IOPS=1372, BW=5491KiB/s (5623kB/s)(1780MiB/331874msec)
WRITE: bw=5491KiB/s (5623kB/s), 5491KiB/s-5491KiB/s (5623kB/s-5623kB/s), io=1780MiB (1866MB), run=331874-331874msec
```
RAID1 takes a hit.

NFS client:
```
write: IOPS=6530, BW=25.5MiB/s (26.7MB/s)(2114MiB/82884msec)
WRITE: bw=25.5MiB/s (26.7MB/s), 25.5MiB/s-25.5MiB/s (26.7MB/s-26.7MB/s), io=2114MiB (2217MB), run=82884-82884msec
```

One thing is certain, network disk caching is helpful!

---

### Post by TheFu on 2021-04-06
Oh and on all my 18.04 and 20.04 systems (clients and servers), the kernel version is:
```
$ uname -a
Linux regulus 5.4.0-70-generic #78-Ubuntu SMP Fri Mar 19 13:29:52 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by dwhickok on 2021-04-07
Thanks and a kernel change was the first thing that came to my mind.  Last week when we had the issue the system was at 139 but updated to 140 with the reboot.  I suppose we could go back to 137 (or prior) just to see if there's any change.

> **LHammonds said:**
> Started a few weeks ago?  Was there a kernel update around that time?  Are you on the same kernel?  Can you revert back to the prior kernel (1st option) or update to a newer kernel (2nd option)

**EDIT:** I remembered I still have an 18.04 server that will update itself daily.  Looking at the kernels installed, here is what I have:

```
ls -l /boot/vm*
-rw------- 1 root root 8396448 Mar 15 18:03 /boot/vmlinuz-4.15.0-139-generic
-rw------- 1 root root 8396448 Mar 19 08:26 /boot/vmlinuz-4.15.0-140-generic
```

Based on file date, looks like the 4.15.0-140 kernel released about 2.5 weeks ago and the prior kernel was only a few days before that.

Not sure if this helps but based on my apt logs, the following kernels first showed up on my system on these dates:

2021-01-21 - 4.15.0-134
2021-01-27 - 4.15.0-135
2021-02-24 - 4.15.0-136
2021-03-16 - 4.15.0-137
2021-03-20 - 4.15.0-139
2021-03-25 - 4.15.0-140

LHammonds

---

### Post by dwhickok on 2021-04-07
Thank you and yes, upgrading to 5.4 is a decent idea.  I've floated the idea to my team.  

Re the U16 systems, we're keeping them around because of whole bunch of dependencies but working on migrating to U20 in the next several months.  

> **TheFu said:**
> Oh and on all my 18.04 and 20.04 systems (clients and servers), the kernel version is:
```
$ uname -a
Linux regulus 5.4.0-70-generic #78-Ubuntu SMP Fri Mar 19 13:29:52 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by TheFu on 2021-04-07
> **dwhickok said:**
> Thank you and yes, upgrading to 5.4 is a decent idea.  I've floated the idea to my team.  

Re the U16 systems, we're keeping them around because of whole bunch of dependencies but working on migrating to U20 in the next several months.

I feel ya.  I have 1 system left on 16.04. I have a migration path, but it won't be fun.  Moved all the others over the last year.

Canonical sells 5 more years of extended support for security updates. [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)  Best to get that, so management feels the cost of not moving to still free supported releases in a timely way.  Plus, having unpatched systems on a network is bad.

When moving to 20.04, the python3 change broke some of our packaged software solutions, so be very aware of that change, if you need mixed server releases.

---

### Post by dwhickok on 2021-04-07
> **TheFu said:**
> 
Why force NFSv3 when NFSv4 has been production ready since 2005 and has a number of enhancements for both security and performance?
You've lost me on what system is actually running the NFS server. As I read the summary, seems ESXi is providing NFS.  If the NFS server is an Ubuntu VM, how does it efficiently access the block storage?  Hopefully, not using vmdk files, but raw, block storage, access or a PCIe controller passthru?

I only run NFS clients in VMs.  NFS servers are on real hardware ... er ... for performance reasons.


To your first question, we're not averse to NFSv4 but with a bunch of older systems (U16 and Cent6.10) didn't want to get too "out there" :).  Might be time to try it again, however, and see if it helps.

To your second question, the U18 server is a VM on an ESXi hypervisor.  Both of its drives (sda and sdb) are on a dedicated Nimble volume, presented to the host as a VMFS6 datastore (so yes, to your VMDK question).  We used to do RDM but it was a headache when expanding volumes, moving from one array to another, and likely other things I've blocked from my brain.  Granted, it's possible some of those challenges have been resolved since we last did it (5-6 years ago); I'm happy to get feedback on that.

```
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0   30G  0 disk
&#9500;&#9472;sda1   8:1    0  476M  0 part /boot
&#9500;&#9472;sda2   8:2    0  4.7G  0 part [SWAP]
&#9492;&#9472;sda3   8:3    0 24.9G  0 part /
sdb      8:16   0   16T  0 disk
&#9492;&#9472;sdb1   8:17   0   16T  0 part /disk/data
sr0     11:0    1 1024M  0 rom
```

I agree with your comment on bare-metal performance but 99.999% of our environment is virtualized for flexibility and ease of redundancy, albeit with a hopefully-acceptable performance hit.

---

