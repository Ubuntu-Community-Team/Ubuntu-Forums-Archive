---
title: "Hard Drive mapping"
date: 2009-05-14
forum: Server Platforms
---

### Post by c1rcu17 on 2009-05-14
Ok, so I have this server, that has 2, 20GB drives. I suspect that it is in a raid config, but I don't have much experience with that. What I'm trying to figure out is how these drives are configured, and how to get the 2nd 20GB working. I really don't know whats going on with these drives, and any help to figure out how they are set up would be greatly appreciated.

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/pdc_bcegcdgjdd1
                       18G  5.6G   12G  34% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  332K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  132K  1.5G   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
```

mount
```
/dev/mapper/pdc_bcegcdgjdd1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (r
```w)

fdisk -l
```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000461f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e643657

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+  83  Linux
```

ls /dev
```
block            fuse     loop5               ppp    ram2    sda       tty    tty19  tty3   tty40  tty51  tty62           usbdev2.1_ep00  vcsa    xconsole
bus              hpet     loop6               psaux  ram3    sdb       tty0   tty2   tty30  tty41  tty52  tty63           usbdev2.1_ep81  vcsa1   zero
cdrom            initctl  loop7               ptmx   ram4    sg0       tty1   tty20  tty31  tty42  tty53  tty7            usbmon0         vcsa2
char             input    mapper              pts    ram5    sg1       tty10  tty21  tty32  tty43  tty54  tty8            usbmon1         vcsa3
console          kmem     mem                 ram0   ram6    sg2       tty11  tty22  tty33  tty44  tty55  tty9            usbmon2         vcsa4
core             kmsg     net                 ram1   ram7    shm       tty12  tty23  tty34  tty45  tty56  ttyS0           vcs             vcsa5
cpu_dma_latency  log      network_latency     ram10  ram8    snapshot  tty13  tty24  tty35  tty46  tty57  ttyS1           vcs1            vcsa6
disk             loop0    network_throughput  ram11  ram9    sndstat   tty14  tty25  tty36  tty47  tty58  ttyS2           vcs2            vmci
ecryptfs         loop1    null                ram12  random  sr0       tty15  tty26  tty37  tty48  tty59  ttyS3           vcs3            vmmon
fd               loop2    oldmem              ram13  rtc     stderr    tty16  tty27  tty38  tty49  tty6   urandom         vcs4            vmnet0
fd0              loop3    pktcdvd             ram14  rtc0    stdin     tty17  tty28  tty39  tty5   tty60  usbdev1.1_ep00  vcs5            vmnet1
full             loop4    port                ram15  scd0    stdout    tty18  tty29  tty4   tty50  tty61  usbdev1.1_ep81  vcs6            vmnet8
```

---

### Post by c1rcu17 on 2009-05-14
Ok, I just deleted the old partition /dev/sdb1 and re-created it.

fdisk -l
```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000461f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e643657

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+  83  Linux
```

I tried to format it using 
```
mke2fs -j /dev/sdb1
```
but I got this error
```
mke2fs 1.41.4 (27-Jan-2009)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!
```
If it is in use, I have no idea where. sdb1 does show up under /dev. I have a sneaky suspicion that somehow my system is using LVM, but I'm not sure of that. Any ideas?

---

### Post by windependence on 2009-05-14
I don't see any RAID or LVM on that machine and unless you set it up that way, it's not gonna magically get that way. sda is your first disk and sdb is your second. You just needed to partition and format your sdb drive and you would have been fine. 

How did you "delete" sdb?

-Tim

---

### Post by cariboo on 2009-05-14
you probably have to disable the raid array in the raid bios befroe you can use the drives as two seperate units.

---

### Post by windependence on 2009-05-14
Jim, from the fdisk -l it looks like they are both listed. I'm not sure what isn't working for him.

-Tim

---

### Post by Gimpy_Rob on 2009-05-14
Whoa, careful there.
/dev/mapper/[someuuid] is a software raid.

/dev/sdb1 is in use by it.

What you want to do is change your /etc/fstab to mount from /sda1 instead of dev/mapper/ and then reboot

You'll also want to disable the RAID functions on the card, or motherboard, through some bios options.

---

### Post by capscrew on 2009-05-14
> **Gimpy_Rob said:**
> Whoa, careful there.
/dev/mapper/[someuuid] is a software raid.

/dev/sdb1 is in use by it.

What you want to do is change your /etc/fstab to mount from /sda1 instead of dev/mapper/ and then reboot

You'll also want to disable the RAID functions on the card, or motherboard, through some bios options.

@ Gimpy_Rob,

Nice catch there.  

For the OP, here is some more info: [http://ubuntuforums.org/showthread.php?t=646340]("http://ubuntuforums.org/showthread.php?t=646340").

I would add that in fstab one should use the UUID instead  of sda1

---

