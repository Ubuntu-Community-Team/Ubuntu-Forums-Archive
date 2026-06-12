---
title: "RAID Array Not Recognized After Reboot"
date: 2008-11-24
forum: Server Platforms
---

### Post by thadrolling on 2008-11-24
I am having a problem with my RAID1 array and I am hoping I could find some help here. I have two 250 GB disks (and I am NOT using the array for root or home partitions). I have gone through all the steps that (I believe) are needed, however, the array doesn't automatically start work when I reboot. After reboot, if I type the two following commands, everything works like a charm. So, my question is...what am I missing?

Here are the two commands that, once typed after reboot, everything is splendid:

```
sudo mdadm --assemble /dev/md0
sudo mount -t ext3 /dev/md0 /media/raid1/
```

The two disks that make up the array are SATA, 250 GB and /dev/sdb and /dev/sdc.

Because the two commands above, I am fairly convinced that the RAID array is ok...it just doesn't start on reboot.

Any help is greatly appreciated!

Thanks, Thad

---

### Post by fjgaude on 2008-11-25
Did it ever start on re-boot?

Do you have a line in /etc/fstab to mount the array?

---

### Post by thadrolling on 2008-11-25
No, it never restarted after a reboot.  Here is the line in my /etc/fstab file:

```
/dev/md0    /media/RAID1    ext3    defaults    0    0
```

Any thoughts?  What else can I verify.  This seemingly simple problem is driving me crazy.

---

### Post by fjgaude on 2008-11-25
You did make the mountpoint at /media/RAID1 using **mkdir**?

If so here's what I'd do in this order: delete **/etc/mdadm/mdadm.conf**, remove **mdadm** using **apt-get**, re-boot. Re-install mdadm using apt-get and then run this:

```
sudo mdadm --assemble --scan
```

That will auto-create a new mdadm.conf file and all should be mountable now. See what happens!

---

### Post by thadrolling on 2008-11-25
Thanks Frank.  Yes, the directory is there for the mount point.  I will try the instructions you provided when I get home tonight...thanks so much for the help.

---

### Post by thadrolling on 2008-11-25
Ok, I did what you suggested, but still no luck.  After I reboot, I type the following command:

```
sudo mdadm --detail /dev/md0
```

and I get the following message:

mdadm: md device /dev/md0 does not appear to be active.

So, I go ahead and type the following and then everything works fine.  

```
sudo mdadm --assemble /dev/md0

sudo mount -t ext3 /dev/md0 /media/raid1/
```

Any additional thoughts?  In my prior message I had /etc/fstab pointing to /media/RAID1.  I have since changed fstab to point to /media/raid1.

Thanks in advance for any help.  This is driving me crazy.

---

### Post by fjgaude on 2008-11-26
Okay, what does the **mdadm.conf** file show?

And also:

```
sudo mdadm -D /dev/md0
```

after you have assembled and mounted it manually?

Also:

```
df -m
```

---

### Post by thadrolling on 2008-11-30
Thanks for sticking with me on this one.  Here is the info you asked for:

1) mdadm.conf says the following:

```
#
# Please refer to mdadm.conf(5) for information about this file
#
# by default, scan all partitions (/proc/partitions) for MD superblocks
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions
# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes
# automatically tag new arrays as belonging to the local system
HOMEHOST <system>
# instruct the monitoring daemon where to send mail alerts
MAILADDR root
# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=a8cb78ec:cef973a4:a95107c4:8449513d
#This file was auto-generated on Tue, 25 Nov 2008 19:47:31 -0600
# by mkconf 
```

2) sudo mdadm -D /dev/md0 says:
```
/dev/md0:
/dev/md0: Version : 00.90.03
Creation Time : Tue Nov 25 17:59:58 2008
Raid Level : raid1
Array Size : 244195904 (232.88 GiB 250.06 GB)
Used Dev Size : 244195904 (232.88 GiB 250.06 GB)
Raid Devices : 2
Total Devices : 2
Preferred Minor : 0
Persistence : Superblock is persistent
Update Time : Sun Nov 30 17:23:24 2008
State : clean
Active Devices : 2
Working Devices : 2
Failed Devices : 0
Spare Devices : 0
UUID : a8cb78ec:cef973a4:a95107c4:8449513d (local to host gollum)
Events : 0.6
Number   Major   Minor   RaidDevice State
0       8       17        0      active sync   /dev/sdb1
1       8       33        1      active sync   /dev/sdc1
```

3) df -m says:
```
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda2                12297      4207      7471  37% /var
run                     886         1       	886   1% /var/run

varlock                    886         0       886   0% /var/lock
udev                       886         1       886   1% /dev
devshm                     886         1       886   1% /dev/shm
lrm                        886        39       848   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3                67179     41344     22449  65% /home
/dev/sdd1               151423    108930     40967  73% /media/160GB
gvfs-fuse-daemon         12297      4207      7471  37% /home/thad/.gvfs
/dev/md0                236594    125133    109076  54% /media/raid1
```

4) And, finally, I noticed on boot I get the following message:
```
Mounting local Filesystems
EXT3-fs: unable to read superblock
mount: wrong fs type, bad option, bad superblock on /dev/md0
missing codepage or helper program, or other error
```

Thanks again for your help.  Looking forward to hearing back.

Regards, Thad

---

### Post by fjgaude on 2008-11-30
I don't know what it could be but your df file is sure different from mind, no tmpfs item:

```
frank@sunshine:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sdb1                98552     17995     75551  20% /
tmpfs                     1980         0      1980   0% /lib/init/rw
varrun                    1980         1      1980   1% /var/run
varlock                   1980         1      1980   1% /var/lock
udev                      1980         3      1977   1% /dev
tmpfs                     1980         1      1980   1% /dev/shm
lrm                       1980         3      1978   1% /lib/modules/2.6.27-9-generic/volatile
/dev/md32               908514     29494    833233   4% /home/raid
/dev/sdb2                98619     58871     34778  63% /media/backup
/dev/scd1                 4299      4299         0 100% /media/cdrom0
/dev/sda1                33542     18961     12891  60% /media/disk
```

You have this mounted, which I've not seen before:

```
gvfs-fuse-daemon         12297      4207      7471  37% /home/thad/.gvfs
```

You have a "normal" install of 8.04 or 8.10? Maybe 7.10?

All else seems okay. We know the array is good, it is just not auto mounting. It could be a "race" issue... you might wish to add a line in the initramfs-tools/init file:

**/usr/share/initramfs-tools/init**   # to stop a race condition with md

```

   157 maybe_break mount
   158 sleep 5
   159 log_begin_msg "Mounting root file system..."
```

```
sudo /usr/sbin/update-initramfs -uk all    # run to rebuild the image
```

Make sure if you add it it is to the "mount" line. The line numbers are likely different with your system. You might start with 10 instead of 5, seconds delay.

Let us know how you are doing.

---

### Post by thadrolling on 2008-12-01
**That's it!**  I can't thank you enough...do you know how long I have been trying to fix that problem?  Whew.

Couple of thoughts:
1) I did a normal install of v8.04, but my root partition seems strange.  Instead of a 12 GB root, I ended up with a 12 GB "gvfs-fuse-daemon".  Not sure how that happened or if it created the problem in this thread.

2) The entire boot process is a mystery to me.  I have never worked with /usr/share/initramfs-tools/init or **/usr/sbin/update-initramfs** before.  Any thoughts on some good reading materials to get me up to speed?  

Thanks again for your help!  

Thad

---

### Post by fjgaude on 2008-12-01
Great, now tell just what was it that did it?

The man pages for tools are helpful:

[http://man.he.net/man8/initramfs-tools](http://man.he.net/man8/initramfs-tools)

[http://www.annodex.net/cgi-bin/man/man2html?initramfs-tools+8](http://www.annodex.net/cgi-bin/man/man2html?initramfs-tools+8)

Usually we find info on any subject using google search. <smile>

---

### Post by thadrolling on 2008-12-01
Sorry...adding the code "sleep 10" right before my drives are mounted in the startup script is what did it.

Thanks again for all your help!

~Thad

---

### Post by deepsiks on 2008-12-29
I too have the same problem, that is my raid does not mount at boot.  I have entered in sleep 10 into the init file and then updated it.  On the first reboot the system did not mount the raid, however on the second reboot it did...  Maybe because I'm using two 1TB hdd raided together I should increase the sleep to 15?
I should also note that the OS resides on its own 10GB hdd.

---

### Post by fjgaude on 2008-12-29
> **thadrolling said:**
> Sorry...adding the code "sleep 10" right before my drives are mounted in the startup script is what did it.

Thanks again for all your help!

~Thad

Great... we learn something new everyday, eh?

---

### Post by Cracauer on 2008-12-29
The conditions for autodetection of the array are:
[list]
[*] partitions must be marked "Linux raid autodetect" in fdisk
[*] drivers for appropriate RAID level must be compiled into the kernel or available via other-than-filesystem means
[/list]

Mounting the array that was started up is an entirely separate matter and is done normally via fstab.

Be warned that I lately encountered an obscure bug around this in that if you do a diskless book on a machine that has drives with raid autodetect partitions on it, and the kernel has the raid driver available, then the whole thing blew up by the diskless book not finding it's (NFS) root filesystem anymore. Obviously the RAID autodetection code prepared itself for being the root filesystem and wiped out the original root parameter to the kernel.

I never had to put in sleep(1) statements, but I have the drivers compiled into the kernel, so I won't have race conditions with loading the modules from initramfs.

---

### Post by fjgaude on 2008-12-30
Driver modules are needed for hardware raid... with modern kernels md is alrady there and works well with **mdadm**.

I'm not sure why the warning.

---

### Post by Cracauer on 2008-12-30
> **fjgaude said:**
> Driver modules are needed for hardware raid... with modern kernels md is alrady there and works well with **mdadm**.


Not when using autodetect. Autodetect happens before the filesystem containing /lib/modules is mounted. Hence you must make the modules for the appropriate RAID level available to the kernel before filesystems are mounted. You can do that either by compiling them in or by using initramfs.

---

### Post by fjgaude on 2008-12-31
I can't say of sure but when did this stop being necessay... I remember something like 7.10 not requiring driver modules for various raid levels, as they all were built-into the kernel. I could be wrong.

---

