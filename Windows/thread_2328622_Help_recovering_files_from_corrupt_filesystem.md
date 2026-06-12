---
title: "Help recovering files from corrupt filesystem"
date: 2016-06-22
forum: Windows
---

### Post by frustratedn00b on 2016-06-22
Brief rundown. (Windows 10 operating system)
. 
 After use of my laptop, I put it into sleep mode and times during sleep it would turn on to install small updates and such before going back to sleep. Sometimes when my laptop wouldn't turn off after 30min or longer, I'd open up the lid and manually turn it off. It always booted up fine until last time I did it. When I turned it on, I started getting the infinite repair loop. I've googled many problems and it appears my Windows filesystem is corrupt. 

I've attempted running a bootable USB version of Knoppix to try and back up my files on an external HD but it can't read my HDD. Any attempt to mount my HDD has been unsuccessful. 
I'm currently running ubuntu xenial through bootable USB. 

Opening up GParted, it shows /dev/sda4 and /dev/sda5 with warnings. /dev/sda4 is my HDD/basic data partition. This is what I get when I pull up information.
> ntfs_mst_post_read_fixup_warn: magic: 0xffffffff  size: 1024   usa_ofs: 65535  usa_count: 65534: Invalid argument
Record 0 has no FILE magic (0xffffffff)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda4': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs.

I also got this when running ntfsfix
> root@ubuntu:/home/ubuntu# sudo ntfsfix /dev/sda4
Mounting volume... ntfs_mst_post_read_fixup_warn: magic: 0xffffffff  size: 1024   usa_ofs: 65535  usa_count: 65534: Invalid argument
Record 0 has no FILE magic (0xffffffff)
Failed to load $MFT: Input/output error
FAILED
Attempting to correct errors... ntfs_mst_post_read_fixup_warn: magic: 0xffffffff  size: 1024   usa_ofs: 65535  usa_count: 65534: Invalid argument
Record 0 has no FILE magic (0xffffffff)
Failed to load $MFT: Input/output error
FAILED
Failed to startup volume: Input/output error
Checking for self-located MFT segment... ntfs_mst_post_read_fixup_warn: magic: 0xffffffff  size: 1024   usa_ofs: 65535  usa_count: 65534: Invalid argument
OK
ntfs_mst_post_read_fixup_warn: magic: 0xffffffff  size: 1024   usa_ofs: 65535  usa_count: 65534: Invalid argument
Record 0 has no FILE magic (0xffffffff)
Failed to load $MFT: Input/output error
Volume is corrupt. You should run chkdsk.

Is there anyway I'd be able to view and recover the files on my HDD?

---

### Post by yancek on 2016-06-22
The "NTFS is inconsistent" message you get is often because windows is hibernated although there could be other problems.  If it is hibernated, you won't be able to mount it from any Linux system.  Best option is to use your windows installation DVD which should have a repair option.  You might also try posting your problem at a windows forum as it is totally unrelated to Ubuntu or Linux.

---

### Post by QIII on 2016-06-22
*Moved to **Windows***

I hope you will get better support here.  There are plenty of UF users who also use Windows and would be happy to help.

---

### Post by frustratedn00b on 2016-06-23
Thanks for the clarification and help. I'll ask there.

---

### Post by yancek on 2016-06-23
I think the problem you will have trying to repair this problem from Linux is the extreme proprietary nature of the filesystem.  ntfsfix might be able to repair some minor problems but generally, you need some type of software designed specifically for windows.  If you don't have the windows DVD, you might be able to get some free software to do the job such as Hiren's boot CD or the UBCD or something similar.  As you can see from the messages you got, all you need is something with chkdsk on it, hopefully?  Goot luck.

---

### Post by gnosoz on 2016-07-22
I believe below solution might work perfectly for your issue.
Open terminal and digit the following commands in sequence
```

sudo -s 
e2fsck -f /dev/sda4
e2fsck -p /dev/sda4
ntfsfix /dev/sda4
ntfsfix -d /dev/sda4
mkdir /mnt/ntfs
mount /dev/sda4 /mnt/ntfs

```
it should dod the trick

---

