---
title: "Disk &quot;full&quot; when writing to disk in 8.04 LTS"
date: 2013-03-24
forum: Server Platforms
---

### Post by archonon on 2013-03-24
Hello!

I needed to reboot my old 8.04 LTS server after 1,5 year uptime to swap PSU, but after boot it has problems when writing to disks and can't really find out whats the problem.

I can create folders and new files but can't write anything to new files. Size always displays as zero bytes. Problem only concers /dev/sdb1 and /dev/sdc1, writing to /dev/sda1 (root) / works normally. 

When copying something to disk, cp only throws: "cp: writing `test.png': No space left on device".

For some reason free space shows as 0 bytes, but before booting there was about ~300 GB left on both disks. 

SMART tests looks good and fsck doesn't find any problems. 

Any help appreciated :)

df -h:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  9.7G   25G  29% /
varrun                489M  3.0M  486M   1% /var/run
udev                  489M   56K  489M   1% /dev
/dev/sdc1             463G  463G     0 100% /media/archive_sdb
/dev/sdb1             463G  463G     0 100% /media/archive_sdc

```


fstab:
```

#/dev/sdc1
UUID=893b37da-f562-41ef-b27c-5d8962fc1d3a /media/archive_sdb ext3 defaults 0 0

#/dev/sdb1
UUID=162d9796-c1fb-4b0c-9e0c-3e18f43defe1 /media/archive_sdc ext3 defaults 0 0

```blkid:
```

/dev/sda1: UUID="b6e45a15-1bd0-44ac-94ae-b15d2dd909c5" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="21352774-75af-49e4-98b0-4ba9836348bc"
/dev/sdb1: UUID="162d9796-c1fb-4b0c-9e0c-3e18f43defe1" TYPE="ext3" SEC_TYPE="ext2"
/dev/sdc1: UUID="893b37da-f562-41ef-b27c-5d8962fc1d3a" TYPE="ext3" SEC_TYPE="ext2"

```kern.log:
```

Mar 21 20:45:08 kone kernel: [3475723.722089] kjournald starting.  Commit interval 5 seconds
Mar 21 20:45:08 kone kernel: [3475723.723001] EXT3 FS on sdc1, internal journal
Mar 21 20:45:08 kone kernel: [3475723.723012] EXT3-fs: mounted filesystem with ordered data mode.

```fdisk -l
```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf89ae9ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4cf5c18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ed4eb9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux


``````

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
udev on /dev type tmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/srv/chroot/hardy_i386 on /var/lib/schroot/mount/hardy_i386-bb6b29bf-8ecb-4408-86d7-e3ddb30f98b1 type none (rw,bind)
proc on /var/lib/schroot/mount/hardy_i386-bb6b29bf-8ecb-4408-86d7-e3ddb30f98b1/proc type proc (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/archive_sdb type ext3 (rw)
/dev/sdb1 on /media/archive_sdc type ext3 (rw)

```


df -i:
```

Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1            2342912  143871 2199041    7% /
varrun                125019      62  124957    1% /var/run
udev                  125019    2919  122100    3% /dev
/dev/sdc1            30531584  300443 30231141    1% /media/archive_sdb
/dev/sdb1            30531584  410745 30120839    2% /media/archive_sdc

```dupe2fs:
```

dumpe2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          893b37da-f562-41ef-b27c-5d8962fc1d3a
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              30531584
Block count:              122096000
Reserved block count:     1220960
Free blocks:              115
Free inodes:              30231141
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      994
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   256
Filesystem created:       Mon Jul 14 21:19:14 2008
Last mount time:          Thu Mar 21 21:19:35 2013
Last write time:          Thu Mar 21 21:19:35 2013
Mount count:              1
Maximum mount count:      25
Last checked:             Thu Mar 21 20:55:44 2013
Check interval:           15552000 (6 months)
Next check after:         Tue Sep 17 21:55:44 2013
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      1b45be74-242f-4ea0-ac4d-e9d49c4babd1
Journal backup:           inode blocks
Journal size:             128M

...
loads of Group xxxx -info

```

---

### Post by Bashing-om on 2013-03-24
I'll take a stab at it.
this:[PHP]
/dev/sdc1             463G  463G     0 100% /media/archive_sdb 
/dev/sdb1             463G  463G     0 100% /media/archive_sdc
[/PHP] indicates to me that at some point the devices were not available and what was directed at the devices was written to the /media folder.
Look and see that the "/media" directory is not at capacity.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by tgalati4 on 2013-03-24
Another possibility is that there are hidden directories or trash directories that need to be emptied to free up space.  How full were the drives before you had these problems?  It's possible that when the PSU failed, it damaged the drives in a subtle way.

The fact that fsck came back clean, indicates that the disks are indeed full, but where is the data?  Perhaps "Lost&Found"?

---

### Post by schragge on 2013-03-24
Try to find out where the files eating all the space are located:
```
sudo du -hd1 /media/archive_sd{b,c}|sort -hr
```

---

### Post by archonon on 2013-03-25
Thanks for help, but it looks like this was just my cockup.

I have rdiff-backup running on every night. During PSU swap i also cleaned server case, and I accidentaly switched sata cables on sdb <-> sdc. So, next night my backup script went full retarded and promptly filled both drives :D

---

### Post by Bashing-om on 2013-03-25
archonon;

Worse things could and have happened, Glad for your sake it is all sorted out !

Please mark this thread as solved, it aides others seeking solutions and the helpers time:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
Problem still ? -> graphical instruction:==>[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)[INDENT=2]
in the end all is well

[/INDENT]

---

