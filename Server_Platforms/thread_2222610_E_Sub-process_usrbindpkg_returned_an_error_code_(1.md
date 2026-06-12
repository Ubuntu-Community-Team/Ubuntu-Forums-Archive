---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-05-07
forum: Server Platforms
---

### Post by astarmathsandphysics on 2014-05-07
I was trying to install some packages for my video website. During this process I got these errors.

Errors were encountered while processing:
 linux-image-3.2.0-61-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

I have tried to purge, uninstall, clean, autremove - all the usual things but nothing works.
When I try to reconfigure I get this message

root@server11362:~# dpkg --configure linux-image-3.2.0-61-generic
Setting up linux-image-3.2.0-61-generic (3.2.0-61.93) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-61-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-61-generic /boot/vmlinuz-3.2.0-61-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-61-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-61-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-61-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-61-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-3.2.0-61-generic
root@server11362:~# 

The video website is theeducationchannel.info 
I WORK REAL HARD ON IT!

How do I fix this problem?

---

### Post by Bashing-om on 2014-05-07
astarmathsandphysics; Humm,

I see 2 immediate problems;
1) > 
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-61-generic
 Which at some point we will have to follow and correct to point to the current initrd.img
2) Of the more pressing is:
> 
gzip: stdout: No space left on device
 With no operating head room the system can do nothing. Let's get that head room as the 1st priority.
Looking to see where the space is consumed:
```

df -h
df -i
dpkg -l | grep linux-image-
cd /
sudo du -sx * | sort -n

```
If you need to drill down further, use cd to move to a directory of interest then repeat the 'du' command.
The results are in megabytes.

Once known what the situation is we can go to work on cleaning it up.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2014-05-07
I will do that tomorrow. Tonight is slop night. I dont trust myself to do this with all the beer slopping about inside me.

---

### Post by Bashing-om on 2014-05-07
astarmathsandphysics; Hey,

Yeah I can understand and relate.

[INDENT]so we can see clearly
[INDENT][INDENT][INDENT]now
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2014-05-08
root@server11362:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/md2        444G  155G  267G  37% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           789M  1.4M  788M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G     0  3.9G   0% /run/shm
/dev/md0         92M   86M  1.1M  99% /boot

root@server11362:~# df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/md2       29548544 542620 29005924    2% /
udev            1007351    511  1006840    1% /dev
tmpfs           1009603    465  1009138    1% /run
none            1009603      4  1009599    1% /run/lock
none            1009603      1  1009602    1% /run/shm
/dev/md0          24096    245    23851    2% /boot

root@server11362:~# 
root@server11362:~# dpkg -l | grep linux-image-
ii  linux-image-3.2.0-23-generic     3.2.0-23.36                        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-59-generic     3.2.0-59.90                        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-60-generic     3.2.0-60.91                        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-61-generic     3.2.0-61.93                        Linux kernel image for version 3.2.0 on 64 bit x86 SMP

root@server11362:~# sudo du -sx * | sort -n
0	aux
0	ps
0	Setup
4	cacert.pem
4	eicar_com.zip
4	killport
4	mdadm.conf.new
4	postponed
4	sent
4	server.crt
4	server.csr
4	server.key
4	server.key.secure
56	dpkg-l
200	bfd-1.5
440	apf-9.7-2
616	last_x264.tar.bz2
2036	libvpx-v1.3.0.tar.bz2
2220	fdk-aac.zip
4256	x264-snapshot-20140505-2245
7068	ffmpeg-snapshot.tar.bz2
7092	Maildir
10480	mstorsjo-fdk-aac-2f29dd4
10560	ffmpeg_build
17660	libvpx-v1.3.0
51376	ffmpeg
root@server11362:~#

I am really surprised that the boot sector is only 100MB. 
Can this be increased?

---

### Post by mörgæs on 2014-05-08
Please use CODE tags for terminal output.

---

### Post by astarmathsandphysics on 2014-05-08
will do

---

### Post by Bashing-om on 2014-05-08
astarmathsandphysics; Yuk;


Welp, yeah, that small /boot partition is a problem
> 
/dev/md0 92M 86M 1.1M 99% /boot

The '/md0' says we are dealing with "raid" arrays, I see no provision for Logical Volume Management.
All I can say is when we get the 2 older kernels removed form the system 
a) live with the sloppyation as is and pay real close attention when new kernels are installed to remove the older kernels ( keep 2 kernels, never can tell what might happen, a backup kernel is a good thing to have on hand !) ;
b) Yikes ! Back up all data, turn the system down, and RE-partition with a larger /boot partition.

But to address the immediate issue, get us some operating room by removing 2 kernels and see if that latest kernel will install.
Hold your breath and try :
```

sudo dpkg --purge linux-image-3.2.0-23-generic
sudo dpkg --purge linux-headers-3.2.0-23-generic

```
May not be able too, no operating head room to work in, or broken dependencies.
If there is a problem, well, we just do "something" else to get to the root of things.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by astarmathsandphysics on 2014-05-09
Everything seems ok now

---

### Post by Bashing-om on 2014-05-09
astarmathsandphysics; Great !

Did you also remove 3.2.0-59.90  image and header ; leaving you with the current  3.2.0-61.93 kernel and the .91 as a backup ?

And to verify that all is indeed fine good and dandy:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade # apt's smart mode to install - if any - the latest kernel.

```

[INDENT][INDENT]house work is
[INDENT][INDENT][INDENT]never all done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

