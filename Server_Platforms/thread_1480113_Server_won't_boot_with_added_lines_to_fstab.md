---
title: "Server won't boot with added lines to fstab"
date: 2010-05-11
forum: Server Platforms
---

### Post by kextyn on 2010-05-11
I recently formatted my HDD and installed Ubuntu Server 10.04 x64.  This is actually the 4th install in the past week because I was testing some things.  But I had this problem on at least the previous install which made me want to start fresh again.

The problem I'm having is Ubuntu will not boot if I add any of my drives to fstab.  If I leave it with the standard proc, /, and swap lines it works fine.  As soon as I add a line for one of my RAID arrays or an NTFS formatted partition the system hangs on bootup.  It doesn't matter if I have the extra drives operating or not.

The last thing I see before it hangs is:
```
/dev/sda1: clean, 69351/4358144 files, 583945/17401600 blocks
```

Here is what the fstab currently looks like:
```
proc    /proc   proc    nodev,noexec,nosuid     0       0
UUID=c62ac627-46a6-4fd5-87e8-4ae0d9185d53       /       ext4    errors=remount-ro       0       1
UUID=c1cee1e4-f8ac-4555-a88b-f237afdedd27       none    swap    sw      0       0
/dev/md0        /mnt/raid5      ext4    defaults        0       0

```

The other two lines which also made it hang included one which was almost exactly the same as the /dev/md0 line except it was md1 with a different mount point and another which used a UUID and was ntfs-3g.  I know they work because all 3 of them were mounted by "mount -a" after putting them into fstab and they're pretty much the same as what I was using with 9.04 server.

---

### Post by ERikDerWikinger on 2010-06-25
Same here

boot hangs with 
```

init: ureadahead-other main process (1515) terminated with status 4

```i added following line to fstab
  
```
//192.168.1.100/share  /mnt/winshare   cifs    user=winuser,password=pwd 0 0
/dev/md_d1             /vms            ext4    defaults                  0 0
```System
AMD Opteron 2382
Software-raid: Level 1 2x2.0 TB 
ubuntu server 10.04 LTS x86_64

---

### Post by clrg on 2010-06-25
Maybe your network based file systems fail to mount when the network is not yet available. Why don't you add the CIFS part to /etc/rc.local as a normal command? Should work just as good, except that this script gets called last.

About the md-devices: I don't know much about those things in Linux, since I use Solaris for servers, but most likely you made an error/typo when adding those lines to fstab. Boot into single user mode and triple-check them.

---

### Post by CharlesA on 2010-06-25
I had the same problem (or a very similar one), but wasn't sure it was due to fstab. You can take a look at the bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576001](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576001)

Did you recently upgrade the kernel or has anything changed since it last worked?

---

