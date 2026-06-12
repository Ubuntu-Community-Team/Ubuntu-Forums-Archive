---
title: "pining for any RAID 1 grub setup assistance!"
date: 2009-05-04
forum: Server Platforms
---

### Post by maclenin on 2009-05-04
I am trying to install grub into the my RAID 1 array (sda1, sdb1) - and the following unfolds: 

```
sudo grub

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
```

I have run for miles (from one end of google to the other) and can't seem to find solace!

Here are links to background, if needed:

_[http://ubuntuforums.org/showthread.php?t=1138512](http://ubuntuforums.org/showthread.php?t=1138512)_
_[http://ubuntuforums.org/showthread.php?t=1144299](http://ubuntuforums.org/showthread.php?t=1144299)_

Thanks for any help - looking to break free of this issue!

---

### Post by caljohnsmith on 2009-05-04
I think maybe what you are missing is using the "device" command in Grub's shell to map your RAID drive to (hd0), similar to what they give in this tutorial:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

In other words, they use this command in that tutorial:
```
device (hd0) /dev/mapper/isw_beeaakeeaa_five 
```
I'm guessing that's what you probably need to do to, and of course your RAID drive will have a different name than "isw_beeaakeeaa_five", so you'll need to replace that with your RAID drive name. How about giving it a shot though and let me know if it works or not. 

John

---

### Post by maclenin on 2009-05-04
Thanks, **caljohnsmith**, for the reply!

Just a few points of clarification (as I attempt to put all of these pieces together):

sda1 (hd0,0) and sdb1 (hd1,0) make up the /dev/md0 RAID 1 array from which I'd eventually like to boot. /dev/md0 does NOT currently appear in fstab.

sdc1 (hd2,0) is the non-RAID partition which was mounted at /boot during install and is my current boot partition.  

Here's my current device.map file (which seems in order to me)...
```
(hd0)  /dev/sda
(hd1)  /dev/sdb
(hd2)  /dev/sdc
```

Generally:

1. grub>find /grub/stage1 reveals...
```
(hd2,0)
```
2. This attempt to install grub on (hd0) seemed to run successfully...
```
grub> root (hd2,0)
grub> setup (hd0)
```
3. However, I was not able to verify the success of the (hd0) setup...
```
grub> find /grub/stage1
(hd2,0)
```

Experimentally:

4. I tried a "sudo cp" of the stage1 grub file from my "sdc1" /boot/grub directory to the /grub directory of my ~Desktop/raidtest mounted /dev/md0 array.

5. After copying stage1 to "/dev/md0" grub> find revealed the following...
```
grub> find /grub/stage1
(hd0,0)
(hd1,0)
(hd2,0)
```
6. I then added stage2 and e2fs_stage1_5 and tried to boot via /dev/md0 from the stage2_eltorito CD - and got an "Error 15"...

Might there be a way to "install" all the relevant grub files to the /dev/md0 RAID array (with the same effect as "grub> set") using this experimental "sudo cp" method?

Your Suggestion:

My sense of the grub>device method was that it was used to set up grub on the "number 2" device in the RAID array...
```
grub> device (hd0) /dev/sdb
grub> root (hd0,0)
grub> setup (hd0)
```
...as discussed [_here_]("http://lists.us.dell.com/pipermail/linux-poweredge/2003-July/008898.html").

Is your suggestion, essentially...
```
grub> device (hd0) /dev/md0
grub> root (hd2,0)
grub> setup (hd0)

grub> device (hd1) /dev/md0
grub> root (hd2,0)
grub> setup (hd1)

```

So, my newly-drawn device.map file would read...
```
(hd0)  /dev/md0
(hd1)  /dev/md0
(hd2)  /dev/sdc
```
...just want to be certain I understand!

Thanks for your help with this!

---

### Post by caljohnsmith on 2009-05-05
OK, I just want to confirm, but do you have Grub's stage1, stage2, e2fs_stage1_5, and menu.lst files in the /grub directory of /dev/md0? If so, try doing the following, but make sure first that /dev/md0 is not mounted anywhere:
```
sudo umount /dev/md0
sudo grub
grub> device (hd0) /dev/md0
grub> find /grub/stage1
[that should return (hd0,0) I believe, but let me know if it doesn't]
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Let me know if that works or not, and please post the output of all the commands before typing "quit". 

John

---

### Post by maclenin on 2009-05-05
Here's an initial report:

1 /dev/md0 has all the files  you suggested should be in it's /grub directory...
```
stage1
stage2
e2fs_stage1_5
menu.lst

```

2. /dev/md0 is unmounted...

3. I ran grub> find /grub/stage1 PRIOR to running the device command just to get a "before" sample...
```
grub> find /grub/stage1
 (hd0,0)
 (hd1,0)
 (hd2,0)

grub> 
```
4. I then ran the device command as you suggested...
```
grub> device (hd0) /dev/md0

grub> 
```
5. I then ran grub> find, again - AFTER running the device command - this is the way it unfolded...
```
grub> find /grub/stage1Unknown partition table signature
 (hd1,0)
 (hd2,0)

grub> 
```

6. I  then ran the grub> find, a second time - AFTER having run the device command...
```
grub> find /grub/stage1
 (hd1,0)
 (hd2,0)

grub> 
```

This is where things stand - I have NOT proceeded past the grub> find command....

Thanks for the assistance!

---

### Post by caljohnsmith on 2009-05-05
Do you have a /dev/mapper directory at all, or is your only RAID device /dev/md0? How about posting the output of:
```

ls -l /dev/m*
sudo mount /dev/md0 /mnt
ls -lR /mnt
```

John

---

### Post by maclenin on 2009-05-05
Per request...

1. I ran ls -l /dev/m* ...
```
server@server:~$ ls -l /dev/m*
brw-rw----  1 root disk   9, 0 2009-05-04 17:53 /dev/md0
brw-rw----  1 root disk   9, 1 2009-05-04 17:53 /dev/md1
brw-rw----  1 root disk   9, 2 2009-05-04 17:53 /dev/md2
crw-r-----  1 root kmem   1, 1 2009-05-04 17:53 /dev/mem
crw-rw----+ 1 root audio 14, 0 2009-05-04 17:53 /dev/mixer

/dev/mapper:
total 0
crw-rw---- 1 root root  10, 60 2009-05-04 17:53 control
brw-rw---- 1 root disk 254,  1 2009-05-04 17:53 vgserver-lvhome
brw-rw---- 1 root disk 254,  6 2009-05-04 17:53 vgserver-lvopt
brw-rw---- 1 root disk 254,  0 2009-05-04 17:53 vgserver-lvroot
brw-rw---- 1 root disk 254,  7 2009-05-04 17:53 vgserver-lvshared
brw-rw---- 1 root disk 254,  2 2009-05-04 17:53 vgserver-lvtmp
brw-rw---- 1 root disk 254,  3 2009-05-04 17:53 vgserver-lvusr
brw-rw---- 1 root disk 254,  5 2009-05-04 17:53 vgserver-lvusrlocal
brw-rw---- 1 root disk 254,  4 2009-05-04 17:53 vgserver-lvvar
server@server:~$ 
```
2. I mounted /dev/md0 ...
```
server@server:~$ sudo mount /dev/md0 /mnt
[sudo] password for server: 
server@server:~$
```
3. Then ls -lR /mnt ...
```
server@server:~$ ls -lR /mnt
/mnt:
total 13
drwxr-xr-x 2 root root  1024 2009-05-05 10:33 grub
drwx------ 2 root root 12288 2009-04-24 20:49 lost+found

/mnt/grub:
total 134
-rw-r--r-- 1 root root   8108 2009-04-24 21:39 e2fs_stage1_5
-rw-r--r-- 1 root root   4904 2009-05-04 14:27 menu.lst
-rw-r--r-- 1 root root    512 2009-04-24 21:39 stage1
-rw-r--r-- 1 root root 121460 2009-04-24 21:39 stage2
ls: cannot open directory /mnt/lost+found: Permission denied
server@server:~$ 
```

...any clues?

---

### Post by caljohnsmith on 2009-05-05
OK, I'm curious, but what do you get if you do:
```
sudo umount /mnt
sudo mount /dev/mapper/vgserver-lvroot /mnt && ls -lR /mnt
```

John

---

### Post by maclenin on 2009-05-05
Quick note - it's a HUGE list - doesn't fit onto one terminal page - how can I copy and paste multiple pages of terminal output?

/dev/mapper/vgserver-lvroot is already mounted at "/" it's ok to mount it two places at once? I guess to analyze it?

---

### Post by caljohnsmith on 2009-05-05
> **maclenin said:**
> Quick note - it's a HUGE list - doesn't fit onto one terminal page - how can I copy and paste multiple pages of terminal output?
OK, the "-R" option is too much, so how about instead posting:
```
ls -l /mnt
```

---

### Post by maclenin on 2009-05-05
...without the -R...
```
server@server:~$ ls -l /mnt
total 104
drwxr-xr-x   2 root root  4096 2009-04-24 22:35 bin
drwxr-xr-x   2 root root  4096 2009-04-24 21:18 boot
lrwxrwxrwx   1 root root    11 2009-04-24 21:19 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2009-04-24 21:40 dev
drwxr-xr-x 123 root root 12288 2009-05-05 11:22 etc
drwxr-xr-x   2 root root  4096 2009-04-24 21:18 home
lrwxrwxrwx   1 root root    33 2009-04-24 22:37 initrd.img -> boot/initrd.img-2.6.27-11-generic
lrwxrwxrwx   1 root root    32 2009-04-24 21:21 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  15 root root 12288 2009-04-24 22:35 lib
drwx------   2 root root 16384 2009-04-24 21:14 lost+found
drwxr-xr-x   3 root root  4096 2009-04-24 21:19 media
drwxr-xr-x   2 root root  4096 2008-10-20 08:27 mnt
drwxr-xr-x   2 root root  4096 2009-04-24 21:18 opt
drwxr-xr-x   2 root root  4096 2008-10-20 08:27 proc
drwxr-xr-x   8 root root  4096 2009-05-04 14:27 root
drwxr-xr-x   2 root root  4096 2009-04-25 12:07 sbin
drwxr-xr-x   2 root root  4096 2009-04-24 21:19 shared
drwxr-xr-x   2 root root  4096 2009-04-24 21:19 srv
drwxr-xr-x   2 root root  4096 2008-10-14 09:02 sys
drwxr-xr-x   2 root root  4096 2009-05-04 17:53 tmp
drwxr-xr-x   2 root root  4096 2009-04-24 21:19 usr
drwxr-xr-x   4 root root  4096 2009-04-24 21:18 var
lrwxrwxrwx   1 root root    30 2009-04-24 22:37 vmlinuz -> boot/vmlinuz-2.6.27-11-generic
lrwxrwxrwx   1 root root    29 2009-04-24 21:21 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic
server@server:~$
```

---

### Post by caljohnsmith on 2009-05-05
OK, thanks, that helps clear things up a little more. How about next just posting:
```

mount
```

---

### Post by maclenin on 2009-05-05
mount...
```
server@server:~$ mount
/dev/mapper/vgserver-lvroot on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sdc1 on /boot type ext3 (rw,relatime)
/dev/mapper/vgserver-lvhome on /home type ext3 (rw,relatime)
/dev/mapper/vgserver-lvopt on /opt type ext3 (rw,relatime)
/dev/mapper/vgserver-lvshared on /shared type ext3 (rw,relatime)
/dev/mapper/vgserver-lvtmp on /tmp type ext3 (rw,relatime)
/dev/mapper/vgserver-lvusr on /usr type ext3 (rw,relatime)
/dev/mapper/vgserver-lvusrlocal on /usr/local type ext3 (rw,relatime)
/dev/mapper/vgserver-lvvar on /var type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/mapper/vgserver-lvroot on /mnt type ext3 (rw)
server@server:~$ 
```

---

### Post by caljohnsmith on 2009-05-05
OK, great, I think I'm getting a better handle on your setup. How about trying:
```
sudo umount /mnt
sudo grub
grub> device (hd0) /dev/md0
grub> geometry (hd0)
grub> root (hd0,0)
grub> null /
[don't press enter after typing the above "null /" command, press TAB instead to get TAB-completion]
```

---

### Post by maclenin on 2009-05-05
1. unmount...
```
server@server:~$ sudo umount /mnt
[sudo] password for server: 
server@server:~$ 
```
2. grub> device... 
```
grub> device (hd0) /dev/md0

grub> 
```
3. grub> geometry...
```
grub> geometry (hd0)Unknown partition table signature
drive 0x80: C/H/S = 56928/2/4, The number of sectors = 979712, /dev/md0

grub> 
```
4. grub> root...
```
grub> root (hd0,0)

Error 5: Partition table invalid or corrupt

grub> 

```
5. grub> null...TAB... 
```
grub> grub null /
Error 12: Invalid device requested

grub> grub null /

```

...here we are!

---

### Post by caljohnsmith on 2009-05-05
OK, after you do the "device (hd0) /dev/md0" command in Grub, try:
```
grub> root (hd0)
grub> null /
[Again use TAB-completion instead of hitting enter]
```

---

### Post by maclenin on 2009-05-05
device...
```
grub> device (hd0) /dev/md0

grub>
```

root...
```
grub> root (hd0)Unknown partition table signature

grub> 
```

null...
```
grub> null /
Error 17: Cannot mount selected partition

grub> null /
```

...THANKS A BUNCH, by the way - for your perseverance!

---

### Post by caljohnsmith on 2009-05-05
I really wish I could help you, maclenin, but my experience with RAID is  limited enough that I'm running out of ideas to try. I'm still confused about the output Grub is giving you when you search for the stage1 file with /dev/md0 set as (hd0) in Grub via the device command. I'll let you know if I can think of anything else, but in the meantime I hope that you'll figure it all out. Good luck and keep me posted. :)

Best Wishes,
John

---

### Post by maclenin on 2009-05-05
I'll keep hunting and should I bag the answer - I'll post it back here in spades! Thanks, again, for going so many rounds!

---

### Post by maclenin on 2009-05-05
A couple of additional questions before I continue my quest:

Can two bootable partitions share a /boot mount point in fstab?
Does a partition need to be mounted in order for grub to be able to boot from it? Will the "root" or "uuid" reference alone in menu.lst be sufficient?

In my example, the partitions in question are:

/dev/sdc1 - non-RAID and non-LVM
/dev/md0 - RAID 1 - but this could be any other "bootable" partition for the sake of my question....

Thanks, again, for the assist, **caljohnsmith**!

---

### Post by caljohnsmith on 2009-05-05
> **maclenin said:**
> A couple of additional questions before I continue my quest:

Can two bootable partitions share a /boot mount point in fstab?
I don't believe that's possible, and I'm wondering why you would want to do that?
> **maclenin said:**
> 
Does a partition need to be mounted in order for grub to be able to boot from it? Will the "root" or "uuid" reference alone in menu.lst be sufficient?

It depends on whether you are referring to the partition that contains Grub's boot files, or if you are referring to a partition with an OS that you want to boot with Grub; on start up, when the BIOS boots the MBR of a drive that has Grub, Grub tries to mount some particular partition to access its boot files (this assumes you installed Grub to the MBR along with the stage1.5 file, which is usually what happens). So on start up, Grub automatically mounts the partition which has its boot files, there is no need to do anything manually.

But if you are talking about an OS in your Grub menu (which I assume is probably what you meant), then if you are booting a linux partition where you use the "kernel" and "initrd" notation, Grub has to try to mount that partition in order to boot those files. Using either the "root" or "uuid" notation in the menu.lst is enough to tell Grub which partition to try to mount. But if you are trying to boot an OS like Windows, Grub does not actually mount the partition, because Grub can't read NTFS partitions; instead Grub boots the boot sector of the Windows partition (which is again specified with either "root" or "uuid" in the menu.lst), so Grub effectively hands-off the booting process to the boot code in the boot sector of that partition, which is called "chainloading". Does that help, or did I miss the point of your question?

John

---

### Post by maclenin on 2009-05-06
1. re: fstab...

When I first considered my RAID/LVM partition scheme, I mapped out the [_following general arrangement_]("http://ubuntuforums.org/showpost.php?p=7134682&postcount=4") - across 3 drives.

As you can see from the [_link_]("http://ubuntuforums.org/showpost.php?p=7134682&postcount=4"), I chose to make each of the sd*1 partitions "bootable" - preserving a "symmetrical" layout - boot on 1, swap on 2, root on 3, shared on 4...

```
sda1 - bootable 
sdb1 - bootable
sdc1 - bootable

sda2 - swap
sdb2 - swap
sdc2 - swap

sda3 - root
sdb3 - root
sdc3 - root

sdb4 - shared
sdc4 - shared
```
And though this might have looked pretty at the time, when I finally installed the OS the result wasn't quite as pretty: the installer gave priority, for some reason, to the sdc1 bootable partition and not to the bootable sda1 + sdb1 md0 RAID array - mounting sdc1 at /boot and leaving the RAID array - md0 - unmounted (and ungrubbed?)....

What I'd like, is to be able to boot from one or the other - RAID or sdc1 - via a grub "fallback" arrangement or regular menu.lst selection at boot. Should I have problems with the RAID array (which I'd set as the "default 0" option in menu.lst), I'd always be able to access or boot from sdc1!

So, that's the "root" of the fstab issue - to create an arrangement whereby I might boot from either sdc1 or the RAID array - on demand...with sdc1 being, essentially, my "emergency floppy"...

2. re: grub...

So, as I read your (responsive) reply...I tried to outline my understanding of the (grub) start-up process...

A. POWER-ON
```
1. Power-on
2. Motherboard fires up CPU and BIOS
```
B. BIOS
```
3. BIOS posts
4. BIOS locates "first" MBR - e.g. (hd0) /dev/sda
```
C. MBR - (hd0) /dev/sda
```
5. BIOS executes the bootloader code (grub stage1) found with the MBR
6. Stage1 passes to stage1.5 (located a few sectors past the MBR)
7. Stage1.5 (knowing which partitions are active) passes to stage2 - e.g. (hd0,0) /dev/sda1
```
D. ACTIVE PARTITION - (hd0,0) /dev/sda1
```
8. Stage2 reads the grub configuration file (menu.lst)
9. An OS is selected from menu.lst (via grub menu or automatically)
10. A device "uuid" tells grub where the OS kernel is located
11. Grub attempts to mount the "uuid" device.
```
C. KERNEL
```
12. The "initrd" kernel image is then loaded into ram
13. In ram, the "kernel" is associated with its filesystem "root=" 
14. The "kernel" reads its "root=" filesystem
15. The init scripts are run
```
D. LOG-IN
```
16. We log into our system.
```  
Additional reference: _[http://www.pixelbeat.org/docs/disk/](http://www.pixelbeat.org/docs/disk/)_

Questions:

1. It seems that any MBR with a bootloader - e.g. (hd0) or /dev/sda - does not have to be "mounted" in order for the BIOS to locate the MBR and stage1? The existence of stage1 with the MBR is the key. It seems the "boot" process is separate from the "mount" process. Mounting - i.e. via fstab - occurs while the filesystem is being loaded (in step 11 through 14)? So, when the BIOS goes in search of a bootloader, it executes the code with the first "live" MBR it finds....

1.a. The question for me is how do I breathe life into my (MBR or) /dev/sda1 and /dev/sdb1 "active" partitions?

2. Once grub passes the stage1 handshake, it runs off an "a priori" partition map hardwired into grub stage1.5. This is how grub is able to locate the active partition - e.g. (hd0,0) or /dev/sda1. UUIDs in menu.lst are for stage2 - i.e. when it comes time to finding and loading the kernel and "root"/filesystem and so forth....

2.a. In other words - the location of an active partition and it's contents are significant BEFORE menu.lst becomes involved in the boot process....

2.b. The location of /boot - and which partition is actually mounted there does not become important until after the OS is selected and the filesystem loaded?

3. One could have multiple active partitions - why would any one of them have to be mounted at /boot? Grub can be installed and utilized without the need for this separate /boot partition? No?

4. With regard to our RAID experiment - I am wondering whether I don't need to somehow mount /dev/md0 in fstab at /boot before I can effectively configure grub on the array...if stage1.5 already has the partition map - I will need to make certain that the partition map contained in stage1.5 sees /dev/md0 mounted at /boot?

4.a. Or, does the fact that sda1 and sda2 (devices within the RAID array) were already set up as active partitions during OS install have them as "bootable" or active in the stage1.5 file - and there is something else that needs to be configured or setup on sda1 and sdb1 - with regard to grub - and being able to boot from the RAID array....

Does any of this make sense?

Thanks, again, **caljohnsmith**, for your help with this process!

---

### Post by caljohnsmith on 2009-05-07
> **maclenin said:**
> 
Questions:

1. It seems that any MBR with a bootloader - e.g. (hd0) or /dev/sda - does not have to be "mounted" in order for the BIOS to locate the MBR and stage1? The existence of stage1 with the MBR is the key. It seems the "boot" process is separate from the "mount" process. Mounting - i.e. via fstab - occurs while the filesystem is being loaded (in step 11 through 14)? So, when the BIOS goes in search of a bootloader, it executes the code with the first "live" MBR it finds....

Grub's stage1 file lives in the MBR (just want to make clear that it is not separate from the MBR), and the MBR is always the first sector of the HDD; thus the BIOS merely tries to boot the first sector of whichever drive is first in the BIOS boot order. And you're right, at this point "mounting" is not a relevant term, because mounting involves mounting a file system--at this point the BIOS is merely executing boot code in a particular sector (the 1st sector) of the HDD.
> **maclenin said:**
> 
1.a. The question for me is how do I breathe life into my (MBR or) /dev/sda1 and /dev/sdb1 "active" partitions?

As you go on to explain below, the bottom line is getting Grub's installed stage1.5 file to point to the partition you want it to for its stage2 file, which then points to the menu.lst. 
> **maclenin said:**
> 
2. Once grub passes the stage1 handshake, it runs off an "a priori" partition map hardwired into grub stage1.5. This is how grub is able to locate the active partition - e.g. (hd0,0) or /dev/sda1. UUIDs in menu.lst are for stage2 - i.e. when it comes time to finding and loading the kernel and "root"/filesystem and so forth....

That's exactly right, but keep in mind that (hd0,0) is not necessarily sda1 on start up--(hd0,0) is the first partition of the **first drive in your BIOS boot order**. In other words, Grub sees the order of drives on start up as the same as your BIOS boot order, so on start up the following is true:
```
(hd0) = 1st boot drive
(hd1) = 2nd boot drive
(hd2) = 3rd boot drive
...etc.
```
It's only when you are running Grub commands in linux is (hd0) the same as sda, (hd1) is sdb, (hd2) is sdc, etc. 
> **maclenin said:**
> 
2.a. In other words - the location of an active partition and it's contents are significant BEFORE menu.lst becomes involved in the boot process....

You got it. :)
> **maclenin said:**
> 
2.b. The location of /boot - and which partition is actually mounted there does not become important until after the OS is selected and the filesystem loaded?

Assuming that Grub has found and loaded its stage2 file successfully, then you're right, the linux boot files in /boot are only relevant when you select the linux OS to boot. 
> **maclenin said:**
> 
3. One could have multiple active partitions - why would any one of them have to be mounted at /boot? Grub can be installed and utilized without the need for this separate /boot partition? No?

Yes, Grub is independent of the /boot partitions; all that matters to Grub on start up is where you located Grub's stage2 and menu.lst files, which doesn't necessarily have to be in a /boot partition. You could for example have your own dedicated Grub partition which only has Grub's boot files, while linux's boot files in /boot are on a completely separate partition. 
> **maclenin said:**
> 
4. With regard to our RAID experiment - I am wondering whether I don't need to somehow mount /dev/md0 in fstab at /boot before I can effectively configure grub on the array...if stage1.5 already has the partition map - I will need to make certain that the partition map contained in stage1.5 sees /dev/md0 mounted at /boot?

Grub's stage1.5 file does not have its own partition map, it just uses the one in the MBR. Also, on start up when Grub tries to locate and load its stage2 file, and that is done without regard to whether any of the linux OSes on the drive mount /dev/md0 on /boot in their fstab files. 
> **maclenin said:**
> 
4.a. Or, does the fact that sda1 and sda2 (devices within the RAID array) were already set up as active partitions during OS install have them as "bootable" or active in the stage1.5 file - and there is something else that needs to be configured or setup on sda1 and sdb1 - with regard to grub - and being able to boot from the RAID array....

Grub's stage1.5 file can point to only one partition for Grub's stage2 file, not multiple partitions. I think the crux of the problem right now is that specifying /dev/md0 as (hd0) in Grub's CLI did not allow Grub to see /dev/md0 as having any valid partitions, unlike the results they got in that Fake Raid tutorial. That's my best guess at this point, but I'm no RAID expert. :)

John

---

### Post by maclenin on 2009-05-07
Thanks, again and again, for the continuing education...I hope at least a wee bit of it will stick!

With regard to resolving the grub/RAID question, my sense...

...from: _[http://lists.us.dell.com/pipermail/linux-poweredge/2003-July/008898.html](http://lists.us.dell.com/pipermail/linux-poweredge/2003-July/008898.html)_
...and: _[http://www.howtoforge.com/software-raid1-grub-boot-debian-etch-p2](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch-p2)_
...as well as: _[http://www.linuxforums.org/forum/linux-newbie/60680-linux-linux-dual-boot.html](http://www.linuxforums.org/forum/linux-newbie/60680-linux-linux-dual-boot.html)_
...and many others...

...is that where grub is concerned, the RAID 1 array can be managed through its component devices...
```
/dev/sda1
/dev/sdb1
```

...whereas, the OS will handle the array, cumulatively, as /dev/md0.

So, here's the latest plan (given my (stubborn) desire to have both sdc1 and md0 as bootable options)....

1. Append this to fstab (sdc1 and md0 will share the mount point /boot)...
```
#/dev/md0
UUID=(blkid /dev/md0) /boot ext3 relatime 0 2
```
2. Append this to mtab (sdc1 and md0 will share the mount point /boot) [NOT CERTAIN THIS STEP IS NECESSARY?]...
```
/dev/md0 /boot ext3 rw,relatime 0 0
```
3. Update the ram disk [NOT CERTAIN THIS STEP IS NECESSARY?]...
```
update-initramfs -u
```
4. Mount /dev/md0 and copy files and folders from /boot to /dev/md0...
```
sudo mount /dev/md0 /mnt
cd /boot
cp -dpRx . /mnt
sudo umount /mnt
```
5. Configure grub...
```
sudo grub

grub> find /grub/stage1
grub> find /vmlinuz-2.6.27-11-generic
grub> find /initrd.img-2.6.27-11-generic

grub> root (hd0,0)
grub> setup (hd0)

grub> root (hd1,0)
grub> setup (hd1)

grub> quit
```

...with the output of the "find" commands being...
```
(hd0,0)
(hd1,0)
(hd2,0)
```

6. I'll give it a whirl....

Any thoughts?

---

### Post by maclenin on 2009-05-08
Success!!!

Thank you for your guidance!!!

I can now boot from BOTH/EITHER sdc1 or (one half of) the RAID array....

However, there are things that still need doing...

a. test the viability of the RAID array - I still need to set up grub on the second half of the RAID array - and mulling whether to "link" the second device of the array (sdb) with (hd0) - so, if sda (the current (hd0)) dies, sdb takes it's place - as the "substitute" (hd0)...ref: _[http://lists.us.dell.com/pipermail/linux-poweredge/2003-July/008898.html](http://lists.us.dell.com/pipermail/linux-poweredge/2003-July/008898.html)_

b. fine-tune menu.lst options and set up "fallback" - though I am currently able to use the grub menu to swap between sdc1 and md0 at boot....

c. I'll also need to see how updates (i.e. kernel and so forth) effect the current "shared-boot" arrangement....

d. I have read that I should modify groot in menu.lst to have it match where the kernel resides (i.e. match the menu.lst UUID from which the system is booting)...however - in my setup - sdc1 and md0 will be sharing the same /boot "pool" of kernel files - perhaps I should just leave groot as it is (hd2,0)....

e. I would be remiss if I didn't add this link as a major contributor, as well, to the success of this process: _[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)_

So, essentially - to get this far:

1. cp all files and folders from the sdc1 (vanilla) /boot directory to the RAID array

2. configure grub

3. make certain you have an entry in menu.lst that refers to your md0 array (by blkid /dev/md0)

4. restart, and away you go (ESC to toggle between boot options)!

I'll add additional comments and findings as relevant....

Thanks, again, **caljohnsmith**, for the soldiering!

---

### Post by caljohnsmith on 2009-05-08
That's really great news you have it all working now, maclenin. Getting Grub/booting issues resolved when RAID arrays are involved is no small feat, so congratulations on getting it working. Cheers and enjoy your Ubuntu-RAID setup. :)

John

---

### Post by maclenin on 2009-05-08
Thanks, again, **caljohnsmith**....

I think one key thing I've learned is that the RAID array can be broken down (and configured) - where grub is concerned - into its component devices.... So, any grub-related setup issues that involve RAID can be handled similarly to those that a "non-RAIDER" might encounter - certain surmountable nuances (see above) notwithstanding....

Again, thanks for the help!

---

