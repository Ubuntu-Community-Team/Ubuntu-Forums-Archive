---
title: "Server crashes on boot (possibly HDD capacity problems)"
date: 2012-08-10
forum: Server Platforms
---

### Post by shoot2kill on 2012-08-10
Hi. I currently have an Ubuntu server box at home which I use as a home file server.

The server has various services running including sabnzbd, which currently has quite a large queue of pending downloads, however I noticed recently that my HDD on there was running at 99% capacity when running a 'df'.

Now, when the server starts, it doesn't stay up for very long before crashing with an extremely long error message (100s of pages of similar repeated errors) The last few lines of the error are:

```

ata3 00: status: { DRDY DF ERR }
ata3 00: error: { ABRT }
ata3 00: failed to enable AA(error_mask=0x1)
ata3 00: failed to enable AA(error_mask=0x1)
end_request: I/O error, dev sda, sector 80084025
Buffer I/O error on device sda4, logical block 0
EXT4-fs error (device sda4): ext4_find_entry:934: [node #9437210: comm python: reading directory Iblock 0

```

as far as I'm aware, sabnzbd is a python service, and I think that maybe the server is crashing because it's trying to read/write to a disk that's too full.

I have tried booting to recovery mode root shell, and doing a df to see the disk is full, but this is giving false data. It says that every partition on my system is 32GB and 11% full. I'm assuming this is something to do with the recovery mode, and not all of my HDDs

The server doesn't stay up for long enough for me to stop any services to debug if this stops the problem.

Any help would be much appreciated.

Thanks

---

### Post by shoot2kill on 2012-08-11
OK. So I booted into the recovery console and deleted a good bunch of files off each hard disk (even though df was showing 32gb avail) and it seems to be booting OK.

Not sure if this is an ubuntu problem, or sabnzbd running out of HDD space and throwing a fatal error, causing ubuntu to crash. 

Seems stable for now. will keep monitoring it.

---

### Post by Vegan on 2012-08-11
giant hard disks are now inexpensive, I use several of them

bigger is better in my opinion, this way logs can be huge etc for debugging nasty problems

---

### Post by CharlesA on 2012-08-11
Have you run a fsck already?

Also run this:

```
df -i
```

---

### Post by ian dobson on 2012-08-11
Hi,

The errors your seeing are disk errors. It looks as if sda has media errors and could well be dieing.

Maybe run a fschk to see if there are any sector errors in the ext file system.

Regards
Ian Dobson

---

### Post by CharlesA on 2012-08-11
> **ian dobson said:**
> Hi,

The errors your seeing are disk errors. It looks as if sda has media errors and could well be dieing.

Maybe run a fschk to see if there are any sector errors in the ext file system.

Regards
Ian Dobson
Agreed. The buffer errors aren't a good thing. The OP might want to do a SMART test as well.

---

### Post by shoot2kill on 2012-09-02
OK. The result of a ```
df -i
``` is:

```
Filesystem        Inodes    IUsed     IFree IUse% Mounted on
/dev/sda1        2444624    74666   2369958    4% /
udev              318549      528    318021    1% /dev
tmpfs             320749      447    320302    1% /run
none              320749        2    320747    1% /run/lock
none              320749        1    320748    1% /run/shm
/dev/sda2          61312      237     61075    1% /boot
/dev/sda4       12517376    10562  12506814    1% /home
/dev/sdc1       45793280    32827  45760453    1% /media/hdd/storage
/dev/sdb1      122101760    11422 122090338    1% /media/hdd/videos
/dev/sdd1       30531584     8491  30523093    1% /media/hdd/music
unionfs-fuse   167895040 45804702 122090338   28% /media/movies

```

I went to do a fsck too, but aborted when I got a message saying:
```

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue<n>? no

```
Is it safe to unmount the drives and run this?

---

### Post by CharlesA on 2012-09-02
Run fsck from a livecd, but it is likely the drive is going out.

---

