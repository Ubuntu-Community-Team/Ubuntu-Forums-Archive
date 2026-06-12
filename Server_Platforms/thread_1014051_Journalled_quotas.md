---
title: "Journalled quotas?"
date: 2008-12-17
forum: Server Platforms
---

### Post by leon.hh on 2008-12-17
Hello there! I'm trying to setup a file server and, of course, I want to activate users and groups quotas.

I followed the regular procedure but when I'm running quotacheck I get a message that says that my kernel supports journalled quotas but they're not active.

I research about it and the advanages of using journalled quotas are very attractive...

The thing is that nobody seems to know how to implement it, even the one who created the kernel patch says that it's very easy but he doesn't tell how to do it.

Hope somebody can help me

---

### Post by capscrew on 2008-12-17
See:[http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch11.pdf]("http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch11.pdf")
Page 34 - Quota.

> Quota support
If you say yes here, you will be able to set per-user limits for disk
usage (also called disk quotas). Currently, it works for the ext2,
ext3, and ReiserFS filesystem. ext3 also supports journaled quotas,
for which you don’t need to run quotacheck after an unclean shutdown.
For further details, read the “Quota” mini-HOWTO,
available from [COLOR="Red"]**[http://www.tldp.org/docs.html#howto](http://www.tldp.org/docs.html#howto)**[/COLOR] or the documentation
provided with the quota tools. Quota support is
probably useful only for multiuser systems

---

### Post by leon.hh on 2008-12-18
As I said before, many documents like the one you mentioned, talk about quotas and the traditional method to aply them, but it doesn't say how to set journalled quotas! I'm about to give up, it really seems that nobody actually know how to do that...

---

### Post by capscrew on 2008-12-18
Maybe you did not understand what I sent you.  The chapter was on the:
> Kernel Configuration Options Reference
The journaled quota is a setting in the OS kernel.  If you have a journaling FS (like ext3) you set the switch for journaled quotas to 'true'.

Are you using a journaling FS?  

Are you configuring a Linux Kernel?

---

### Post by leon.hh on 2008-12-21
I see, I believe I'm starting to understand. However I'm still a little new in the Linux world and I have absolutely no idea of how to set those switches on. What file do I have to modify, I mean, what exactly do I have to do?

---

### Post by capscrew on 2008-12-22
> What file do I have to modify, I mean, what exactly do I have to do?There is no file that you can modify.  The switches are really options that you select when compiling the OS kernel.  

This is not something you normally need to do.  I would say in your case; if you have to ask what it is, then you should not attempt it. I would just use the quotas as they are.  

But, if you must persist, See:
 [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")
and
 [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu")

---

### Post by leon.hh on 2008-12-23
Well, thanks anyway

---

### Post by Awx56twY667qZ on 2009-04-07
I see there has not been a reply to this thread in several months. I, however, am in the same boat as the original poster. 

quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotachiec after an unclean shutdown.

I gather from this message that it is not a kernel issue, as my kernel probably supports journaled quota, but that is is a quota issue, as I need to switch to journaled quota.

I looked at the supplied link, and I cannot find where it says how to turn on journaled quota.

---

### Post by capscrew on 2009-04-08
> **pcsmasher@gmail.com said:**
> I see there has not been a reply to this thread in several months. I, however, am in the same boat as the original poster. 

quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotachiec after an unclean shutdown.

I gather from this message that it is not a kernel issue, as my kernel probably supports journaled quota, but that is is a quota issue, as I need to switch to journaled quota.

I looked at the supplied link, and I cannot find where it says how to turn on journaled quota.

What file system format (ext 3??) are you using?  Did you have user/group quota's enabled when you ran quotacheck?

---

### Post by palo_m on 2009-04-15
> **capscrew said:**
> What file system format (ext 3??) are you using?  Did you have user/group quota's enabled when you ran quotacheck?
I think you are missing the point. pcmasher has the normal (non-journaled) quota already on, but when running usual quota tool quotacheck, he receives notification, that his filesystem already supports journaled quota, but he is using non-journaled quota. Thus, _compilation of kernel is not needed_, as ubuntu distributers already did it for us :p. If the kernel wouldn't support journaled quota, he would not receive that notification...


The advantage of journaled quota against non-journaled is the same as advantage of journaled filesystem against non-journaled: If the filesystem is not unmounted correctly (typically unclean shutdown, but now possibly unclean disconnect of external disc drive), the check of non-journaled filesystem needs to be done (takes quite long time on large filesystems. Journaled filesystem just replays journal which is much faster than whole filesystem check. The same goes on quota - on incorrect shutdown the non-journaled quota needs to check for quota for whole filesystem (i.e. calculate total size and file numbers for each users), which can take a lot of time if the filesystemis big and there are many various users owning the files. Journaled quotas... you know, just replays journal.


> **pcsmasher@gmail.com said:**
> I see there has not been a reply to this thread in several months. I, however, am in the same boat as the original poster. 

quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotachiec after an unclean shutdown.

I gather from this message that it is not a kernel issue, as my kernel probably supports journaled quota, but that is is a quota issue, as I need to switch to journaled quota.

I looked at the supplied link, and I cannot find where it says how to turn on journaled quota.
I'm going to try this myself, but haven't started it yet. One problem is, that journaled quotas are still undocumented AFAIK. Fortunately we have Google.
So far I've found:
> To use journalled quota you need
to mount a filesystem with following options:
  usrjquota=<user quota file>
  grpjquota=<group quota file)
(quota files must be placed in filesystem's root directory)
  jqfmt=vfsv0
(quota format 'vfsold' should also work but it's not tested)
So I guess that where you previously mounted fs as:
```
$ mount -o rw,usrquota /dev/sda6 /mnt
```
you should mount it instead as:
```
$ mount -o rw,usrjquota=aquota.user,jqfmt=vfsv0 /dev/sda6 /mnt
```

Maybe re-creation of quota-file aquota.user will be needed to make it work properly... I'm not sure about this point.
Good idea is to test it first on some unused fs (or even better, instead of using real partition /dev/sda6 create just small image file and mount it via loop) and once it's working, you can go live on real fs.

As I said, I will also try to enable the journaled quota for myself, but it may take me some time (have other important things to do 8)). When I'm successful, I will post here the short howto (if nobody will do it earlier). If somebody has enough time and experience to play with it, Google "mount usrjquota" (and please skip those "mount usrquota" results which Google offers on top - thank you Mr.Google, but we put that "j" there on purpose :p).

---

### Post by capscrew on 2009-04-15
@ palo_m,

Yes, I subsequently saw the usrjquota reference.  I did a my own [**[COLOR="Green"]_Google search_[/COLOR]**]("http://www.google.com/search?hl=en&q=journaled+quota++usrjquota+ubuntu&btnG=Search").  One references was [[COLOR="Red"]**_here_**[/COLOR]]("http://forum.qnap.com/viewtopic.php?f=11&t=8759").  

As [COLOR="Blue"]**pcmasher** [/COLOR] did not reply, I dropped the issue.  It seems that there is not much interest in this at this time.

A howto to would be great if and/or when you have the time.

---

### Post by palo_m on 2009-04-15
OK, I couldn't wait. As soon as I came home, I had to try it.
Short summary: it's as I already described.

Long story follows. 
**[COLOR="Red"]Warning:[/COLOR] For simplicity I ran those commands under root account, so if you try to repeat the same steps, be careful during typing and think about consequences of your actions. Or use normal user for most of actions and sudo for, only mount/umount and quota-related commands need root access. It's your machine and your responsibility...**
[LIST=1]
[*]Create image file for testing
```
linux:~#
linux:~# cd /tmp
linux:/tmp# dd if=/dev/zero of=/tmp/disk.img bs=1024 count=20000
```
[*]Make ext3 filesystem in image file
```
linux:/tmp# mkfs.ext3 -m 0 -L test /tmp/disk.img
mke2fs 1.41.3 (12-Oct-2008)
/tmp/disk.img is not a block special device.
Proceed anyway? (y,n) y
...blah-blah-blah... (usual stuff displayed)
```
[*]Mount disk with non-journaled quota option and create some file there... just to have situation like normally used filesystem
```
linux:/tmp# mount -o loop,rw,usrquota /tmp/disk.img /mnt
linux:/tmp# mount | grep mnt
/tmp/disk.img on /mnt type ext3 (rw,loop=/dev/loop0,usrquota)
linux:/tmp# mkdir /mnt/test1
linux:/tmp# dd if=/dev/zero of=/mnt/test1/test2 bs=1024 count=100
100+0 records in
100+0 records out
102400 bytes (102 kB) copied, 0.000684922 s, 150 MB/s
linux:/tmp#
linux:/tmp#
linux:/tmp# ls -al /mnt/test1/
total 103
drwxr-xr-x 2 root root   1024 2009-04-15 21:30 .
drwxr-xr-x 4 root root   1024 2009-04-15 21:29 ..
-rw-r--r-- 1 root root 102400 2009-04-15 21:30 test2
linux:/tmp# df /mnt
Filesystem           1K-blocks      Used Available Use% Mounted on
/tmp/disk.img            19362      1301     18061   7% /mnt
```
[*]Initiate non-journaled quota. It's in vfsv0 format by default, that's what we like:
```
linux:/tmp# quotacheck -c -v /mnt
quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotacheck after an unclean shutdown.
quotacheck: Scanning /dev/loop0 [/mnt] done
quotacheck: Cannot stat old user quota file: No such file or directory
quotacheck: Old group file not found. Usage will not be substracted.
quotacheck: Checked 4 directories and 3 files
quotacheck: Old file not found.
linux:/tmp# setquota -u root 10000 15000 1000 1500 /mnt
linux:/tmp# repquota /mnt
*** Report for user quotas on device /dev/loop0
Block grace time: 7days; Inode grace time: 7days
                        Block limits                File limits
User            used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
root      --    1301   10000   15000              6  1000  1500


linux:/tmp# ls -al /mnt
total 24
drwxr-xr-x  4 root root  1024 2009-04-15 21:57 .
drwxr-xr-x 23 root root  4096 2009-04-11 18:02 ..
-rw-------  1 root root  6144 2009-04-15 21:57 aquota.user
drwx------  2 root root 12288 2009-04-15 21:28 lost+found
drwxr-xr-x  2 root root  1024 2009-04-15 21:30 test1
linux:/tmp# quotacheck -v /mnt
quotacheck: Your kernel probably supports journaled quota but you are not using it. Consider switching to journaled quota to avoid running quotacheck after an unclean shutdown.
quotacheck: Scanning /dev/loop0 [/mnt] done
quotacheck: Old group file not found. Usage will not be substracted.
quotacheck: Checked 4 directories and 4 files

```Now we are in pretty much same situation on /mnt, as our real FS is - we have some files, we have quota set, all seems fine, but quotacheck -v annoys us, that we should consider journaled quota. So, we considered it already and we want it, so let's go for it.
-
[*]Remount filesystem with journaled quota options. *(See above, that file aquota.user already exists. The old quota format - vfsold - uses file quota.user instead. I guess we have no reason to use the old format anymore - and there is convertquota command for case of "historical" disks anyway.)* 
```
linux:/tmp# mount -o remount,loop,rw,usrjquota=aquota.user,jqfmt=vfsv0 /mnt
linux:/tmp# mount | grep mnt
/tmp/disk.img on /mnt type ext3 (rw,loop=/dev/loop0,usrquota,usrjquota=aquota.user,jqfmt=vfsv0)

```
We can see, that previous usrquota option stayed there... Alternatively to remount, we could use umount and then mount - but the filesystem cannot be used to be able to do that, which is not always the case. So I prefer remount.
-
[*]Let's see where we are now
```
linux:/tmp# quotacheck -v /mnt
quotacheck: Scanning /dev/loop0 [/mnt] done
quotacheck: Old group file not found. Usage will not be substracted.
quotacheck: Checked 4 directories and 4 files
linux:/tmp# repquota /mnt
*** Report for user quotas on device /dev/loop0
Block grace time: 7days; Inode grace time: 7days
                        Block limits                File limits
User            used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
root      --    1301   10000   15000              6  1000  1500
```
Yeah, the message has gone. We are using journaled quota now!
:guitar:

[*]So as we tested it works with image file, we can try with real partitions. Turn quota off first, then remount it with additional "usrjquota=aquota.user,jqfmt=vfsv0" options, verify with quotacheck that it works and then turn quota back on. If all seems to work fine, one last step is to update /etc/fstab to have the mount options permanent (and if we want to be really-really sure, we can also reboot afterwards... although another remount using /etc/fstab is sufficient).
[/LIST]
I did not try it with grpquota (I don't use group quotas anyway), but I believe it works the same, just needs to use "grpjquota=aquota.group"... Here we go, using journaled quota now \\:D/

---

### Post by capscrew on 2009-04-15
@ palo_m,

That's great work!  I believe you are the only one who has documented this feature.

---

### Post by cupinzim on 2009-08-14
Brilliant! Thanx a lot!

---

### Post by bfdhud on 2009-11-28
Tried this on 9.10 / ext4 both user and group quota's work with his tutorial.


hi5

---

### Post by PieterN on 2010-04-06
Thanks a lot for your howto!

For me to get it to work I needed to add "grpjquota=aquota.group" to the mount options, otherwise I got the message:

```
mount: / not mounted already, or bad option
```

I got this error when "grpjquota" was left out on both 9.04 and 9.10.

---

### Post by Alan-A on 2010-09-15
There is a further example of a way to start journaled quotas here: [http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p4](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p4)
Look for point 12 "Journaled Quota".
Hope this may help.
A.

---

