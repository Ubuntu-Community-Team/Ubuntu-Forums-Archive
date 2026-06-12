---
title: "[SOLVED] Putting /tmp on its own partition"
date: 2008-08-19
forum: Security
---

### Post by Blancmange on 2008-08-19
G'day! I'm rather new to Unbuntu 8.04 (or indeed any Linux outside of RIPLinux). I've spent weeks configuring it for my Wacom serial tablet, an Apache web server and various preferences. The system's been backed up (and restored several times) with GPartimage. I'm now ready to make this single partition install of Ubuntu into a configuration Linux security experts seem to recommend.

I have an 80GB hard disc paritioned as follows:
[list]
[*]sdb1 3.5GB swap (yeah, I know that's a silly place to put it now)
[*]sdb5 10GB  Ubuntu (a single-partition install, now being modified)
[*]sdb6 5GB   /tmp (***not working with my /etc/fstab yet***)
[*]sdb7 5GB   /var (working perfectly)
[*]sdb8 56GB  /home (also working perfectly)
[/list]

I'd like my Ubuntu system to use sbd6 for /tmp so I can give it restrictive mount options, exclude it from my partition backups and perhaps help with defragmentation. I gather this should be achieved by using the cp -ax command to copy /tmp into the partition that is to become /tmp and editing the /etc/fstab file.

I've performed the trick on /var and /home and all seems well. However, whenever I try to use sdb6 for /tmp, Gnome fails to start. The login-failure message says something about /etc/X11/xinit/xinput.d/all_ALL and includes the message:
```
mkdtemp: private socket dir: Permission denied
```

Here's my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>         <dump>  <pass>
proc            /proc           proc            defaults          0       0
# /dev/sdb5
UUID=c72373dc-366c-5191-bf5f-6a1des0fbaa1  /        ext3  rw,relatime,errors=remount-ro  1  1
# /dev/sdb6
UUID=efbf661b-46a7-3b17-a7cf-c63e7badf00d  /tmp     ext3  defaults,relatime  1  2
# /dev/sdb7
UUID=19e85c43-2870-461b-830c-3ff9deadbeef  /var     ext3  rw,nodev,nosuid,noexec,relatime  1  3
# /dev/sdb8
UUID=52c5aff7-231e-338a-89dc-01c7c3feeb1e  /home    ext3  rw,nodev,relatime,errors=remount-ro  1  4

# /dev/sdb1
UUID=bc52ce74-d522-49e0-b5a1-62cf17b0d1ce  none     swap  sw    0  0

/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8       0  0
/dev/scd1       /media/cdrom1   udf,iso9660     user,noauto,exec,utf8       0  0
/dev/fd0        /media/floppy0  auto            rw,user,noauto,exec,utf8    0  0

```

I address the partitions by UUID because half the time, my two hard disc drives appear as sda & sdb and at other times, as sde & sdf. (in RIPLinux, they appear as hda & hdb) I've munged the UUIDs for the sake of posting them on a public forum, but otherwise they appear to be accurate - I can see the copied /tmp files when I point the [UUID for sdb6] in fstab to /xtmp (a directory I just made up). Changing "/tmp" in /etc/fstab to "/xtmp" allows my system to boot and start a Gnome session properly, using the original /tmp that resides on the 10GB partition in which Unbuntu was installed (sdb5). The slutty mount options (beginning with "defaults") are chosen in a vain attempt to get /tmp to work on sdb6. Obviously it should have options like those of /var (which does indeed work).

Just in case the following details are important:
[list]
[*] 1.5GHz Athlon processor
[*] 1GB DDR RAM (on one module)
[*] A 40GB IDE hard disc drive (for Windows 2000) and an 80 GB one for Ubuntu 8.04 Hardy Heron (2.6.24-19-generic)
[*] Two DVD/DVD-RAM writers
[*] A decrepit old Wacom 12"x12" ArtZII tablet and stylus (just bought a replacement stylus today)
[*] Some sort of mouse thing (USB)
[*] An Adaptec SCSI host card into which the film scanner is plugged
[/list]

Any idea why my use of sdb6 for /tmp is failing?

---

### Post by sisco311 on 2008-08-19
Try to mount the partition and set the correct permissions:
```
sudo chown root:root /tmp
sudo chmod 1777 /tmp
```

---

### Post by Blancmange on 2008-08-19
> **sisco311 said:**
> Try to mount the partition and set the correct permissions:
Since the /tmp-partition-to-be is at this moment mounted by /etc/fstab as /xtmp, the appropriate commands would be:
```
sudo chown root:root /xtmp
sudo chmod 1777 /xtmp
```
(followed by changing "/xtmp" in /etc/fstab to "/tmp" and using the less slutty mount options, then rebooting).

It works perfectly!

The reason I didn't think such commands could work is because I didn't imagine that the partition itself had owner, group and permissions data the way directories and files did. Silly me!

Many thanks!

---

### Post by dcstar on 2011-01-01
> **Blancmange said:**
> 
..........
Here's my /etc/fstab:

```

..........
# /dev/sdb6
UUID=efbf661b-46a7-3b17-a7cf-c63e7badf00d /tmp ext3 defaults,relatime  1  2
..........

```


You don't really want something as ephemeral at /tmp using a journaled file system, updating timestamps or being checked on bootup, much better to have:

```
UUID=efbf661b-46a7-3b17-a7cf-c63e7badf00d /tmp **ext2 defaults,noatime  0  0**
```

---

### Post by Blancmange on 2011-01-01
Cheers, dcstar!

---

