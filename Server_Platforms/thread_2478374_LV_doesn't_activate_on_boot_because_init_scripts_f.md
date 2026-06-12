---
title: "LV doesn't activate on boot because init scripts finish before /dev entries created"
date: 2022-08-24
forum: Server Platforms
---

### Post by janipewter on 2022-08-24
I believe I am experiencing this race condition which seems to have existed in Debian since at least 11 years ago: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568838](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568838)

Dell T20 server
New install of Ubuntu Server 22.04
Root fs - 2x 256GB SSD in RAID1 with LVM on top
Data fs - 2x 2TB SSD in RAID1 with LVM on top

```
$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/data-vg/data
  LV Name                data
  VG Name                data-vg
  LV UUID                i0MTbd-cBMs-tQvg-RQq9-eTgo-ISn9-pDcilc
  LV Write Access        read/write
  LV Creation host, time smilebox, 2022-08-16 20:03:47 +0000
  LV Status              available
  # open                 0
  LV Size                1.86 TiB
  Current LE             488377
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:1

  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/ubuntu-lv
  LV Name                ubuntu-lv
  VG Name                ubuntu-vg
  LV UUID                bKYTcO-6ifZ-sF5x-MZSh-J8NK-3NAP-Fr90Ii
  LV Write Access        read/write
  LV Creation host, time ubuntu-server, 2022-08-16 19:08:10 +0000
  LV Status              available
  # open                 1
  LV Size                <220.52 GiB
  Current LE             56452
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0

$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
tmpfs                              786M  1.6M  785M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv  217G   13G  195G   6% /
tmpfs                              3.9G     0  3.9G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
/dev/md124p2                       2.0G  128M  1.7G   7% /boot
/dev/md124p1                       1.1G  5.3M  1.1G   1% /boot/efi
tmpfs                              786M  4.0K  786M   1% /run/user/1000
/dev/mapper/data--vg-data          1.9T  290G  1.5T  17% /data

```

The majority of times when the server boots, init scripts finish before /dev entries are created, so LVM does not activate the data LV. Logging in and running ```
vgchange -ay
``` is successful at activating the data VG. It can then be mounted as normal.

I have seen many reports of this issue through Google searches but none have yielded a solution that actually works. There are patches suggested [here]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=568838") but these do not work on current version of LVM. Is there anything I can do here, other than just bodging it with a crontab entry to run ```
vgchange
``` and ```
mount
``` after boot?

---

### Post by TheFu on 2022-08-24
You can screw around with systemd dependencies i.e. unit files.
While you are at it, I'd resize the root LV to be 40G, max.  Unix isn't Windows.  We can create and mount specific LVs where they are needed, like under /var/ and /opt/ and /home/.  Having a huge root LV will make things harder than necessary in the future.  Also, where's the swap LV?

BTW, almost always, these are preferred for LVM information:
```
sudo pvs
sudo vgs
sudo lvs
```
Concise, to the point, LVM information.

I assume you have a HW-RAID card, otherwise, just use the SW-RAID that it built-into LVM. No need for mdadm anymore.

---

