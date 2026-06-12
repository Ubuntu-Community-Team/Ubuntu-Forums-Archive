---
title: "Moving to new hard drive question"
date: 2009-03-27
forum: Server Platforms
---

### Post by WhosRodney on 2009-03-27
Hi all,

I'm going to need to need to move some of my partitions to new, larger disk and wanted to run it by you guys to see if you can point out any gotchas or flaws in my plan.

Here's what my current setup looks like:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              16G  1.8G   14G  12% /
tmpfs                 942M     0  942M   0% /lib/init/rw
varrun                942M  284K  942M   1% /var/run
varlock               942M     0  942M   0% /var/lock
udev                  942M  2.7M  939M   1% /dev
tmpfs                 942M     0  942M   0% /dev/shm
lrm                   942M  2.4M  940M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda9              20G   15G  4.0G  79% /mnt/oldhome
/dev/sda8              20G  5.6G   13G  31% /srv
/dev/sda7              18G   12G  4.6G  73% /var
/dev/sdb1             925G   29G  887G   4% /home

```

As you can see, we're running out of space on /dev/sda (it's only 80G).  /dev/sdb is a 1TB drive and currently only houses /home, so I'd like to move all of the partitions on /dev/sda (except for /dev/sda9) to /dev/sdb.

All non-swap filesystems are ext3.  I'm thinking the easiest way to do this is:
[LIST=1]
[*]make a disk image of /dev/sda
[*]copy /home on /dev/sdb to another computer
[*]reformat /dev/sdb
[*]install the disk image of /dev/sda on /dev/sdb
[*]remove /mnt/oldhome from /dev/sdb
[*]add /home to /dev/sdb and then copy the backup of the old /home to the new /home partition on /dev/sdb
[/LIST]

Thoughts?  Comments?  Suggestions?

---

### Post by khelben1979 on 2009-03-27
Your plan is probably good, however, I would never partition a harddisk like you have done.

This is how my harddisk (40GB) is partitoned over here:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             894M  139M  708M  17% /
tmpfs                 156M     0  156M   0% /lib/init/rw
udev                   10M   76K   10M   1% /dev
tmpfs                 156M     0  156M   0% /dev/shm
/dev/hda8              14G   13G  155M  99% /home
/dev/hda7              90M  4.3M   81M   6% /tmp
/dev/hda4             4.6G  4.6G     0 100% /usr
/dev/hda9              15G   13G  1.1G  93% /usr/local
/dev/hda5             2.8G  426M  2.2G  16% /var
```

---

### Post by redmk2 on 2009-03-27
I don't believe you need most of those partitions at all.  When hard drives were  smaller and less reliable the use of separate partitions was a good thing.

If you have only 1 drive at the end, what are you really gaining.  This does not mean that you should not have multiple partitions on the drive.  But rather; only the partitions that make sense. What you are trying to achieve?

I have the following on my machine (approx):```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              10G    5G    5G  50% /
...
/dev/sda3              20G    5G   15G  25% /home
/dev/hda4              90G   50G   40G  55% /smb

```

Here is why I configured the partitions.  I have the /home so that if I reinstall I don't touch the data.  I have the /smb for the same reason.  Administrative controls (ACL's or disk quota's) can be used.  These  are partition wide. This allows me to control the data differently for /home vs. /smb.  The /srv partition is where I have my Samba shares.  I believe WhosRodney is using /srv for this purpose.

There is no functional reason to separate out /tmp, /var, /usr as these are all on the same spindle (hard drive) and therefore provide no advantage.

@WhosRodney,

Unfortunately,  you have boxed your self into a corner with all these partitions.  But, you only have to move the data to a larger disk.  The /, /var, /usr don't really expand much overtime.  I would start by creating only 2 partitions for holding only the data.  These would be for mounting to /home and /srv.  I would think about not using the whole disk (save some for later expansion).

Move the data out of those directories on the original disk. Use these as the mount points of the new partitions on the new disk.

Do you know how to mount partitions?  I would temporarily mount one of the partitions to transfer the data.

---

