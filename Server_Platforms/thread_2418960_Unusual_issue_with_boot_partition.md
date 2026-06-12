---
title: "Unusual issue with /boot partition"
date: 2019-05-14
forum: Server Platforms
---

### Post by wjhildreth on 2019-05-14
Hello all,

I have been running Ubuntu 14.04 hosting out Zimbra email server.  While doing a kernel update, the system reported to me that there was insufficient room on the /boot partition.  I set out and removed some old kernels to free the space.  Now, even though it looks like I have the space, I cannot install the kernel update and it seems to be affecting the initramfs-tools software update as well.  Essentially, any software that needs to write to the boot partition.

The server is set up with LVM and a separate 258MB boot partition.  The df command gives me the following information about the partition.

```

root@mail:/# df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             16G   12K   16G   1% /dev
tmpfs           3.2G  804K  3.2G   1% /run
/dev/dm-0       3.2T  238G  2.8T   8% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
none            5.0M     0  5.0M   0% /run/lock
none             16G     0   16G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda2       237M   48M  177M  22% /boot
root@mail:/# 

```

and

```

root@mail:/# df -i
Filesystem        Inodes  IUsed     IFree IUse% Mounted on
udev             4110326    524   4109802    1% /dev
tmpfs            4113425    526   4112899    1% /run
/dev/dm-0      217636864 461365 217175499    1% /
none             4113425      2   4113423    1% /sys/fs/cgroup
none             4113425      2   4113423    1% /run/lock
none             4113425      1   4113424    1% /run/shm
none             4113425      4   4113421    1% /run/user
/dev/sda2          62496    303     62193    1% /boot
root@mail:/# 

```

All software is up to date, but when doing apt update / upgrade I am informed that I have a package not fully installed.

```

Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
root@mail:/# 

```

When I run the dpkg --audit command I get the following output

```

root@mail:/# dpkg --audit
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      tools for generating an initramfs

The following packages are missing the list control file in the
database, they need to be reinstalled:
 linux-image-3.13.0-169-generic Signed kernel image generic

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 linux-image-3.13.0-169-generic Signed kernel image generic

root@mail:/# 

```

From the text above I see that initramfs-tools looks to be half configured, and then the failed kernel install.  Running dpkg --configure initramfs-tool I get the following output

```

root@mail:/# dpkg --configure initramfs-tools
Setting up initramfs-tools (0.103ubuntu4.11) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.11) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-161-generic
grep: /boot/config-3.13.0-161-generic: No such file or directory

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.13.0-161-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
root@mail:/# 

```

From this, I get the message that there is no space left on the drive.  I should also note the kernel 3.13.0-161-generic failed and has been removed as best I can tell.  Here is a listing of the files in the /boot directort

```

root@mail:/# ls -l /boot
total 33134
-rw-r--r-- 1 root root  1169204 Aug 20  2018 abi-3.13.0-157-generic
-rw-r--r-- 1 root root   166094 Aug 20  2018 config-3.13.0-157-generic
drwxr-xr-x 5 root root     1024 May 13 17:45 grub
-rw-r--r-- 1 root root 22594985 Aug 27  2018 initrd.img-3.13.0-157-generic
drwx------ 2 root root    12288 Sep 10  2014 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-r--r-- 1 root root      254 Aug 20  2018 retpoline-3.13.0-157-generic
-rw------- 1 root root  3416014 Aug 20  2018 System.map-3.13.0-157-generic
-rw------- 1 root root  5892240 Aug 20  2018 vmlinuz-3.13.0-157-generic
root@mail:/# 

```

Currently there is only one working kernel and I am unable to update the system because of what appears from the error messages to be no space left on the drive or not enough space.  But the system seems to report that there is space.

Can someone please offer some assistance?

Regards,
Joe Hildreth

---

### Post by LHammonds on 2019-05-14
> **wjhildreth said:**
> I set out and removed some old kernels to free the space.
Can you be more specific on exactly how you freed more space?

Check your command history (if enabled) to see exactly what you typed to make more space.

LHammonds

---

### Post by wjhildreth on 2019-05-14
I have run a bunch of commands the last couple weeks, but what I done was:

```

dpkg --get-selections | grep linux-image
apt-get purge <oldest Kernel>

```

But I have been trying all sorts of things.  One of which I should mention is that kernel update 3.13.0-161-generic failed and only partially installed.  I removed it from dpkg via brute force if I remember.  Then it tried the 2.13.0-169-generic update.  The previous error with configuring initramfs-tools was it was trying to generate initrd.img-3.13.0-161-generic.  I need to find a way to remove all traces of this kernel I think.

I am sure I made some mistakes somewhere.  Perhaps with the removal of old kernels.  If I run dpkg -l | grep linux-image I get the following now.

```

root@mail:~# dpkg -l | grep linux-image
rc  linux-image-3.13.0-156-generic            3.13.0-156.206                                                      amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-157-generic            3.13.0-157.207                                                      amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ri  linux-image-3.13.0-169-generic            3.13.0-169.219                                                      amd64        Signed kernel image generic
rc  linux-image-extra-3.13.0-156-generic      3.13.0-156.206                                                      amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-157-generic      3.13.0-157.207                                                      amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.13.0.169.180                                                      amd64        Generic Linux kernel image
root@mail:~# 

```

Thank you for any assistance you can provide.

Joe

---

### Post by oldfred on 2019-05-14
You may not be getting updates as repository should be closed. It expired April 2019.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
I believe corporations can purchase extended support. But better to just upgrade to 18.04 or even 16.04.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

---

### Post by TheFu on 2019-05-14
I moved my zimbra system last month from 14.04 to 16.04.  I was running a v8.0.6 Zimbra release (internal access only), but now have v8.9.11.  The migration method failed and I had less than 50 users to migrate, so I just used the Zimbra export/import process for each userid (from the web GUI) after I setup the fresh new VM, loaded the new Zimbra, then got busy on the command prompt.

Newer versions of Zimbra use a sparse DB file for LDAP, so be certain when you move it around or back it up to use tools that handle sparse files correctly.  The real size of the file was just 2.7MB, but after a copy/backup it was 80GB.  That had repercussions throughout my storage planning.  For backups, I ended up excluding the sparse file and create tgz file (sparse option) that is included.

Anyway, it is passed time to get off 14.04. Support for 14.04 ended last month and there isn't any approved 18.04.x based zimbra today. 

I have some overview notes for zimbra stuff, if you like.  I've been running it since 2008.  Part of my security is not allowing it to be accessed from internet. I've setup an email gateway for all inbound and outbound SMTP and the IMAP and webGUI are only available from the VPN or using an SSH tunnel to get onto a known LAN.  A few years ago, we did allow IMAPS access, but there were so many SASL authentication failures, it wasn't worth the risks and management agreed that VPN was the best trade-off for access. We were using fail2ban to block sasl failures, but that just became too much hassle with thousands of blocks a day.

As for the /boot/ partition size. It really needs to be 500MB or larger. Here's the /boot/ on my fresh zimbra server.
```
# df -h
Filesystem                  Size  Used Avail Use% Mounted on
/dev/vda1                   720M  107M  577M  16% /boot
```

It has 2 kernels:
```
# dpkg -l |grep linux-image-4
ii  linux-image-4.4.0-142-generic 4.4.0-142.168 amd64 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-146-generic 4.4.0-146.172 amd64 Signed kernel image generic
```

I patch weekly.

---

### Post by TheFu on 2019-05-14
And ... this might be helpful.  Perhaps there is some waste in your grub or the initrd is huge?
```
/boot# du -sh *
1.2M    abi-4.4.0-142-generic
192K    config-4.4.0-142-generic
192K    config-4.4.0-146-generic
7.3M    grub
39M     initrd.img-4.4.0-142-generic
39M     initrd.img-4.4.0-146-generic
16K     lost+found
4.0K    retpoline-4.4.0-142-generic
3.8M    System.map-4.4.0-142-generic
3.8M    System.map-4.4.0-146-generic
6.9M    vmlinuz-4.4.0-142-generic
6.9M    vmlinuz-4.4.0-146-generic

```

---

### Post by wjhildreth on 2019-05-14
You are correct, I probably need to upgrade the server to v16 or v18, but would like to resolve the issue first.

Joe

---

### Post by wjhildreth on 2019-05-14
I don't have any issues with upgrading to Ubuntu 16.04 and migrating the mailboxes.  I only have 50, but there is a LOT of data associated with a half dozen or so of them.  But before doing that, I would like to fix the issue I am seeing.  I suppose I can use an intermediate machine for a migration.  Problem is the tiny hospital I work for has limited resources.  :-(


On the topic of file sizes for grub, kernel, etc.  The file sizes seem to be normal enough.

```

root@mail:/boot# du -sh *
1.2M	abi-3.13.0-157-generic
164K	config-3.13.0-157-generic
12M	grub
22M	initrd.img-3.13.0-157-generic
12K	lost+found
174K	memtest86+.bin
175K	memtest86+.elf
176K	memtest86+_multiboot.bin
1.0K	retpoline-3.13.0-157-generic
3.3M	System.map-3.13.0-157-generic
5.7M	vmlinuz-3.13.0-157-generic
root@mail:/boot# 

```

Joe

---

### Post by TheFu on 2019-05-14
I don't see anything in the df/du or inodes.  It is something else, something strange.

Which version of Zimbra is running?

Might that sparse LDAP DB file have been expanded?  /opt/zimbra/data/ldap/mdb/db/data.mdb
Need to use **du** to see the real size and ignore the size that **ls** reports.

By any chance is btrfs being used?  df and du don't work with btrfs. It lies to them.

---

### Post by wjhildreth on 2019-05-15
TheFu,

I am currently running Release 8.7.1.GA.1670.UBUNTU14.64 Network edition of Zimbra.

The /boot partition is ext2 and the root file system is ext4

---

### Post by TheFu on 2019-05-15
I'm lost. No more ideas.

Did you check that LDAP DB file didn't explode in size?

---

