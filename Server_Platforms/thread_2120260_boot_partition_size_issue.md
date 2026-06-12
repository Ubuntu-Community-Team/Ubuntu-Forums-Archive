---
title: "/boot/ partition size issue"
date: 2013-02-26
forum: Server Platforms
---

### Post by medikoo on 2013-02-26
Why do default Ubuntu Server installation make /boot/ partition so small, when it's easy to predict that it wil get full within few months? Why there's no possibility to provide custom size at install process?

Few months ago I lost my system due this issue. My /boot/ was constantly being at 100%. I was trying to release the space by removing old versions of kernel, but at one point I removed one file too many and was not able to get it back.

I reinstalled the system with new version and now I'm faced with exactly same issue, my /boot/ is again 100%. I'm not able to install new packages due to errors.

It's hard to believe for me that such issue just lives with a system for years. It's extremely annoying.

What is the remedy?
Is there any easy method to increase /boot/ partition size? Is this possible through remote ssh access (my server is collocated in far place)?

How can I remove older kernel versions (and why they're just not removed by default)?
Currently ls -la of /boot/ shows:

-rw-r--r--  1 root root   791281 Jul 27  2012 abi-3.2.0-29-generic
-rw-r--r--  1 root root   791446 Aug 24  2012 abi-3.2.0-30-generic
-rw-r--r--  1 root root   791446 Sep  7 18:57 abi-3.2.0-31-generic
-rw-r--r--  1 root root   792532 Sep 27 00:14 abi-3.2.0-32-generic
-rw-r--r--  1 root root   792532 Oct 18 19:10 abi-3.2.0-33-generic
-rw-r--r--  1 root root   792587 Nov 15 12:29 abi-3.2.0-34-generic
-rw-r--r--  1 root root   792715 Dec  5 19:22 abi-3.2.0-35-generic
-rw-r--r--  1 root root   792767 Jan  8 23:25 abi-3.2.0-36-generic
-rw-r--r--  1 root root   792767 Jan 24 17:08 abi-3.2.0-37-generic
-rw-r--r--  1 root root   792830 Feb 19 13:58 abi-3.2.0-38-generic
-rw-r--r--  1 root root   140432 Jul 27  2012 config-3.2.0-29-generic
-rw-r--r--  1 root root   140432 Aug 24  2012 config-3.2.0-30-generic
-rw-r--r--  1 root root   140459 Sep  7 18:57 config-3.2.0-31-generic
-rw-r--r--  1 root root   140488 Sep 27 00:14 config-3.2.0-32-generic
-rw-r--r--  1 root root   140488 Oct 18 19:10 config-3.2.0-33-generic
-rw-r--r--  1 root root   140505 Nov 15 12:29 config-3.2.0-34-generic
-rw-r--r--  1 root root   140505 Dec  5 19:22 config-3.2.0-35-generic
-rw-r--r--  1 root root   140505 Jan  8 23:25 config-3.2.0-36-generic
-rw-r--r--  1 root root   140505 Jan 24 17:08 config-3.2.0-37-generic
-rw-r--r--  1 root root   140488 Feb 19 13:58 config-3.2.0-38-generic
drwxr-xr-x  3 root root     5120 Feb 14 11:26 grub
-rw-r--r--  1 root root 14764647 Sep  9 23:25 initrd.img-3.2.0-29-generic
-rw-r--r--  1 root root 14764153 Sep 11 09:21 initrd.img-3.2.0-30-generic
-rw-r--r--  1 root root 14770139 Oct  8 09:08 initrd.img-3.2.0-31-generic
-rw-r--r--  1 root root 14771831 Oct 13 06:50 initrd.img-3.2.0-32-generic
-rw-r--r--  1 root root 14772389 Nov 17 06:27 initrd.img-3.2.0-33-generic
-rw-r--r--  1 root root 14771754 Dec  3 14:42 initrd.img-3.2.0-34-generic
-rw-r--r--  1 root root 14770741 Dec 18 06:29 initrd.img-3.2.0-35-generic
-rw-r--r--  1 root root 14770610 Jan 18 06:44 initrd.img-3.2.0-36-generic
-rw-r--r--  1 root root 14775080 Feb 14 11:26 initrd.img-3.2.0-37-generic
drwxr-xr-x  2 root root    12288 Sep  9 23:20 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2882108 Jul 27  2012 System.map-3.2.0-29-generic
-rw-------  1 root root  2883362 Aug 24  2012 System.map-3.2.0-30-generic
-rw-------  1 root root  2883401 Sep  7 18:57 System.map-3.2.0-31-generic
-rw-------  1 root root  2884076 Sep 27 00:14 System.map-3.2.0-32-generic
-rw-------  1 root root  2884306 Oct 18 19:10 System.map-3.2.0-33-generic
-rw-------  1 root root  2885127 Nov 15 12:29 System.map-3.2.0-34-generic
-rw-------  1 root root  2885822 Dec  5 19:22 System.map-3.2.0-35-generic
-rw-------  1 root root  2886319 Jan  8 23:25 System.map-3.2.0-36-generic
-rw-------  1 root root  2886103 Jan 24 17:08 System.map-3.2.0-37-generic
-rw-------  1 root root  2887333 Feb 19 13:58 System.map-3.2.0-38-generic
-rw-------  1 root root  4960752 Jul 27  2012 vmlinuz-3.2.0-29-generic
-rw-------  1 root root  4963280 Aug 24  2012 vmlinuz-3.2.0-30-generic
-rw-------  1 root root  4963792 Sep  7 18:57 vmlinuz-3.2.0-31-generic
-rw-------  1 root root  4966768 Sep 27 00:14 vmlinuz-3.2.0-32-generic
-rw-------  1 root root  4966896 Oct 18 19:10 vmlinuz-3.2.0-33-generic
-rw-------  1 root root  4967632 Nov 15 12:29 vmlinuz-3.2.0-34-generic
-rw-------  1 root root  4968400 Dec  5 19:22 vmlinuz-3.2.0-35-generic
-rw-------  1 root root  4969392 Jan  8 23:25 vmlinuz-3.2.0-36-generic
-rw-------  1 root root  4969072 Jan 24 17:08 vmlinuz-3.2.0-37-generic
-rw-------  1 root root  4968592 Feb 19 13:58 vmlinuz-3.2.0-38-generic

I don't see anything that I can safely remove.

I'll be gratefull for any help on that

---

### Post by The Cog on 2013-02-26
You can safely remove the old versions of the kernel once you know the latest version is working OK. In your case, that's versions 29-37.

It is best to remove these by uninstalling the packages that they belong to. On a desktop system I would use synaptic for this task, but as you have a GUI-less server you need a textual way to do it. Use aptitude or apt-get. You are probably looking for packages that start with "linux-image".

I wish I knew an easy way to remove the outdated images easily, but I haven't found one yet.

---

### Post by schragge on 2013-02-26
I'd automate it with a shell script like this
```

#!/bin/sh
prev=`readlink /vmlinuz.old` && prev=linux-image-${prev#*-}+
exec [COLOR=red]sudo[/COLOR] apt-get -y purge '^linux-image-[0-9]' linux-image-`uname -r`+ $prev

```

You can run it as a cron job periodically, say once a month. If run as root, you don't need the [COLOR=red]sudo[/COLOR] part.

---

### Post by sudodus on 2013-02-26
Welcome to the Ubuntu Forums :-)

> **medikoo said:**
> Why do default Ubuntu Server installation make /boot/ partition so small, when it's easy to predict that it wil get full within few months? Why there's no possibility to provide custom size at install process?

Old kernels are left, because the updated kernel might not work will all your installed software, so you can boot with an old kernel if necessary.
> 
What is the remedy?
Is there any easy method to increase /boot/ partition size? Is this possible through remote ssh access (my server is collocated in far place)?
You can create partitions manually with ***gparted*** booted from an Ubuntu desktop install drive (if you have one) or another live linux drive. Then when installing you can select to use that manual partitioning. It is possible but more complicated and risky to edit the partition size afterwards. Backup everything before doing that!
> 
How can I remove older kernel versions (and why they're just not removed by default)?
...
I don't see anything that I can safely remove.

I'll be gratefull for any help on thatYes, when you know that 'everything' works with the new kernel, you can remove the old ones. I usually leave only the two newest kernels (the current one plus one more), and I hardly ever boot into the older one.

There are several convenient methods, for example with the GUI tool ***Ubuntu Tweak***
but I guess you have no graphics desktop in your server, so the following method might work better for you (I have not used it myself, but the commands seem OK for me).

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by schragge on 2013-02-26
The problem with the method described in the linked page is that it removes all kernels, but the current one. My script above, however, should retain the previous kernel, too, provided that you have the /vmlinuz.old link (which is maintained automatically on Debian-based systems).

---

### Post by sudodus on 2013-02-26
> **schragge said:**
> The problem with the method described in the linked page is that it removes all kernels, but the current one. My script above, however, should retain the previous kernel, too, provided that you have the /vmlinuz.old link (which is maintained automatically on Debian-based systems).

... and this is a big advantage :KS

---

### Post by LHammonds on 2013-02-26
I use Nagios to monitor the size of my partitions for all my servers as well as when they are wanting to reboot after a kernel update.

When I manually reboot a server, I usually do a "df -k" to check if the /boot partition is larger than normal (usual size is about 20 to 30% usage).  If it grew, I check what images are there by typing "ls -l /boot/vm*"

If there are more than 2 kernel images, I remove the older ones using a command similar to this one:

```
apt-get remove linux-image-3.2.0-36-generic
```

I thought about writing a script and automating it but I just don't want something like this or automated reboots that can potentially keep the server from booting up.  If there is a bug in the script or the processing of the script, the potential is there to delete all images.  Or if security updates changes grub and the config gets messed up causing it to not boot.

If something goes wrong, I want to be there and watch it as it happens and ONLY to one server at a time of my choosing.

LHammonds

---

### Post by medikoo on 2013-02-27
Guys, great thanks for helpful answers.

Indeed removing old kernels with apt-get remove/purge is straightforward and does what I expect. Thanks! :)

---

### Post by lcadman on 2013-11-19
To add onto this question, if I have an out of the box (took default options) Ubuntu setup, how can I resize the boot partition?

For example, I see this with GParted:   /dev/sda (60.00 GiB)

**Partition..............File System.......Mount Point.......Size.............Used............Unused........Flags**
/dev/sda1__________ext4________________________243.00 MiB___68.38 MiB___174.62 MiB___boot
/dev/sda2__________extended____________________59.76 GiB_____---________---
___/dev/sda5_______lvm2 pv_______servername_____59.76 GiB____59.76 GiB____0.00 B______lvm
unallocated_________unallocated__________________1.00 MiB______---________---

The machine is a VM. Is it possible to perform any of the scenarios such as: (a) shrink beginning of LVM to grow sda1 or (b) expand /dev/sda from 60 GiB to 70 GiB, shrink sda2 somehow and give space to sda1?

Thanks ):P

---

### Post by houstonbofh on 2013-11-20
You can grow the entre disk image.  Then boot from a LiveCD and run gparted to move everything to the end of the disk to open up space for boot.  Then resize boot.

As a totally different thing...  A boot partition is only written to during system upgrades.  as this is not common, you may decide that journaling is not really all that important.  If so, format it ext2 and noatime for a nice performance boost when booting.

---

### Post by SeijiSensei on 2013-11-21
I always partition manually during installation and set the size of /boot to 512MB.  That's usually sufficient.  Like houstonbofh, I use ext2 formatting for boot since journalling is unnecessary on a filesystem that small.

---

