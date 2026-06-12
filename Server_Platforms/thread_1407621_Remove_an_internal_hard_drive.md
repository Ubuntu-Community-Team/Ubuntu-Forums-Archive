---
title: "Remove an internal hard drive"
date: 2010-02-15
forum: Server Platforms
---

### Post by sonicnudge on 2010-02-15
I'd like to physically remove a hard drive from my Ubuntu 9.10 Server. (And not replace it.)

This is a fresh install of 9.10. (I am using Grub2.)

(Please note -- I have moved this question from the "Hardware & Laptops" category, because I think this category ("Server Platforms") may be better suited to answer the issue. Here is the original (closed) thread: [http://ubuntuforums.org/showthread.php?t=1403287](http://ubuntuforums.org/showthread.php?t=1403287) )

Here is my current disk configuration (via df -hT):
```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/fullback-root
              ext4     54G  1.7G   50G   4% /
udev         tmpfs    375M  200K  375M   1% /dev
none         tmpfs    375M     0  375M   0% /dev/shm
none         tmpfs    375M  260K  375M   1% /var/run
none         tmpfs    375M     0  375M   0% /var/lock
none         tmpfs    375M     0  375M   0% /lib/init/rw
/dev/sda5     ext2    228M   41M  176M  19% /boot
/dev/sdb1      xfs    280G  271G  8.7G  97% /media/media-01
/dev/sdc1      xfs    298G  288G   11G  97% /media/media-02
/dev/sdd1      xfs    298G  290G  8.5G  98% /media/media-03
/dev/sde1      xfs    298G  288G   11G  97% /media/media-04
/dev/sdf1      xfs    153G  135G   18G  89% /media/vault-01

```My system is installed on /dev/sda (hd0). sdb - f contain data only. I'd like to remove sdf (hd5).

I thought I could modify /etc/fstab, shutdown the server, remove the drive, and restart. Instead, reboot hangs at "Loading GRUB".

Are there a set of commands and/or configuration files that need to be modified to make this happen?

All ideas welcome!

Thank you,
-Sonic

---

### Post by sonicnudge on 2010-02-25
Anyone?

-Sonic

---

### Post by dmizer on 2010-02-26
Please post your /etc/fstab

---

### Post by Jive Turkey on 2010-02-26
You should edit your fstab file to remove the directives that point to that drive before powering down your server.  You could do it after but the os fill freak out and start checking your partiions on the next boot.  If you have any critical os related partition on there it would be fatal unless you put the drive back in and worked it out some other way.  If you have os related partitions on the drive in question you could possibly try imaging the partition(s) in question.  I cant help you with that but I'll bet its possible.

---

### Post by sonicnudge on 2010-03-03
Thanks for the feedback.

@dmizer: Here is my current / working fstab (with sdf1 installed):
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/fullback-root /               ext4    errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0   0       1
# /boot was on /dev/sda5 during installation
UUID=2849129c-baf2-4281-a379-0614fdf62ba1 /boot           ext2    defaults        0       2
/dev/mapper/fullback-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0               udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0                            auto   rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/media-01                           xfs    defaults        0       0
/dev/sdc1       /media/media-02                           xfs    defaults        0       0
/dev/sdd1       /media/media-03                           xfs    defaults        0       0
/dev/sde1       /media/media-04                           xfs    defaults        0       0
/dev/sdf1       /media/vault-01                           xfs    defaults        0       0

```

@Jive Turkey: I thought this was the case (or rather, all I needed to do). The first thing I tried was to comment out the /dev/sdf1 line in fstab:

```

. . .
/dev/sde1       /media/media-04                           xfs     defaults        0       0
# /dev/sdf1       /media/vault-01                           xfs     defaults        0       0

```

I even removed the /media/vault-01 directory. However, whenever I reboot without the sdf1 drive, the system hangs at the loading GRUB message.

*** Might be relevant: All of the drives are installed across 2 inexpensive (Rosewill RC-209-EX) 4-port SATA cards. No problem in getting them to work -- their drivers for Linux seem to be good. (Hmmm . . . I might try splitting the drives evenly across the 2 controller cards . . . sdf1 was on its own card.)


Any other ideas?

Thanks,
-Sonic

---

### Post by dmizer on 2010-03-03
I highly suggest that you change all of your drive mounts in /etc/fstab to UUID rather than /dev/xxx. Here's a decent howto: [http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/](http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/)

Once this is done, see if you can reboot with your drive removed.

---

### Post by KiLaHuRtZ on 2010-03-04
> **dmizer said:**
> I highly suggest that you change all of your drive mounts in /etc/fstab to UUID rather than /dev/xxx.

Ditto...

---

### Post by sonicnudge on 2010-03-05
@dmizer and @KiLaHuRtZ: Thanks for the suggestion. I had not really considered using UUIDs.

So I gave it a try, converting to UUIDs (@dmizer -- I used your recommended guide -- thanks -- I found it well written.)

However, after I remove the drive and restart, the system still hangs at "Loading GRUB". (I still like the philosophy behind the the use of the UUIDs in /etc/ftab -- I'll be using this approach in the future regardless.)

I also have a theory that balancing the drives between the two controller cards might help. (Maybe GRUB is getting confused with a now empty SATA controller where there had previously been (at least) a drive?) I'll give it a try today and reply.

Thank you!
-Sonic

---

### Post by psusi on 2010-03-05
This is a GRUB problem so it has nothing to do with fstab.  It sounds like the drive you are trying to remove is actually the one that had grub installed on it.  Which drive is your system drive?  Which one does the bios consider the boot drive?  You will need to boot from the livecd and reinstall grub on the correct hard drive after removing the old one.

---

### Post by sonicnudge on 2010-03-05
@psusi: Nah -- The boot is on a separate IDE 60 GB drive, plugged directly into the mobo.

PROBLEM SOLVED!

My theory about a lonely (freshly empty) controller on boot up throwing GRUB for a loop seems to be true!

Here's what I did:
I left 2 drives on one 4-port controller, and moved the other 2 to the second 4-port. And the system rebooted!

I then tried adding the vault drive on the third port of the second controller. Reboot OK; tweaking /etc/fstab allowed access vault drive OK.

Then, I commented out vault in /etc/fstab, and re-removed the vault drive. Reboot OK!


So, is this a GRUB bug, or a driver bug? (Or a GRUB bug when it accesses the driver?)

Should I submit a bug to the GRUB folks?

(I started wrestling with this problem in early September 2009. Killed maybe 25 hours figuring this out.)

Thanks again to All!
-Sonic

---

### Post by psusi on 2010-03-05
It's a hardware configuration problem, not really a bug at all.  It's a question of which drive the bios was trying to boot from.  When you changed the configuration by moving drives around, the bios tried to boot from the wrong drive.  Most likely the drive that the bios decided to boot from after removing the vault drive had the GRUB MBR installed, but when the MBR went out to load the rest of grub from the disk, it wasn't there, hence the error.

---

### Post by sonicnudge on 2010-03-09
psusi,

While I am no hardware or Ubuntu server guru (although I did come up with the fix to my issue!), I don't believe this is a BIOS or boot issue:
1) The Ubuntu install/boot drive is an IDE drive connected directly to the mobo.
2) I added the vault drive after I initially got the system up and  running.
3) The vault drive was on an add-in SATA controller card. (I understand that Ubuntu does not like to boot off drives connected to SATA controller cards.)
4) The vault drive is not marked as a boot device in fdisk.
5) My workaround (and repeatable proof of concept) indicates a problem (bug) in GRUB: during "GRUB loading" and before (GRUB's) "error: no such disk" (see below).

So, I just performed a proof of concept, which I believe supports my understanding. Here's what I did:
0) Started with working setup: 2 permanent drives on each controller, no vault drive installed.
1) I changed /etc/fstab to include my vault drive
2) Moved all permanent drives back to controller 1
3) Added vault (solo) to controller 2
4) Rebooted. All worked OK.
5) Removed vault from /etc/fstab.
6) Rebooted. Hangs at "GRUB loading." <------ This is where I was stymied for months.
7) Split the 4 permanent drives between controller 1 and 2
8) Rebooted. All OK. (Note: After seeing "GRUB loading", I also saw "error: no such disk". I believe this is GRUB giving up on the existence of vault -- as it should do at #6, above. This indicates the heart of the problem, what I believe is a GRUB2 bug.)
9) Added vault to /etc/fstab.
10) Added vault as 3rd drive on controller 2.
11) Rebooted. All OK. (Maybe some additional output during boot -- machine is adding vault drive (?).)
12) Removed vault from /etc/fstab.
13) Rebooted. All OK. (Again, the "GRUB loading", followed briefly by "error: no such disk" message.)

Again, let me know if I should submit a bug to the GRUB folks. (Now that I know the workaround, I'm personally good -- I'd just like to see GRUB2 help others avoid the pain.)

Regards,
-Sonic

---

### Post by psusi on 2010-03-09
> **sonicnudge said:**
> psusi,
5) Removed vault from /etc/fstab.
6) Rebooted. Hangs at "GRUB loading." <------ This is where I was stymied for months.


You MUST have missed a step here.  Just removing the entry from fstab can't cause any changes grub can see or care about.  Did you ALSO (re)move the physical drive after removing it from fstab?

---

### Post by sonicnudge on 2010-03-09
psusi,

Right! For additional clarity I also added shutdown points.

Here's the corrected POC:
0) Started with working setup: 2 permanent drives on each controller, no  vault drive installed. Booted OK.
1) I changed /etc/fstab to include my vault drive.
2) Shutdown.
3) Moved all permanent drives back to controller 1.
4) Added vault (solo) to controller 2.
5) Rebooted. All worked OK.
6) Removed vault from /etc/fstab
7) Shutdown.
 8) Removed vault from controller 2. (controller 2 now empty.)
9) Rebooted. Hangs at "GRUB loading." <------ This is where I was  stymied for months.
10) Shutdown.
11) Split the 4 permanent drives between controller 1 and 2 (2 on each)
12) Rebooted. All OK. (Note: After seeing "GRUB loading", I also saw  "error: no such disk". I believe this is GRUB giving up on the existence  of vault -- as it should do at #7, above. This indicates the heart of  the problem, what I believe is a GRUB2 bug.)
13) Added vault to /etc/fstab.
14) Shutdown.
15) Added vault as 3rd drive on controller 2.
16) Rebooted. All OK. (Maybe some additional output during boot --  machine is adding vault drive (?).)
17) Removed vault from /etc/fstab.
18) Shutdown.
19) Removed vault drive.
20) Rebooted. All OK. (Again, the "GRUB loading", followed briefly by  "error: no such disk" message.)

So, is GRUB the culprit? If not, is there a good command to tell GRUB what it needs to know to avoid hanging at "GRUB loading"?

(I'm still thinking this is primarily a problem with GRUB2. I suppose it could also be a driver issue -- maybe in the way the driver provides interaction with the controller -- or possibly a hardware issue, but I am speaking a little out of my league here.)

Regards,
-Sonic

---

### Post by sonicnudge on 2010-03-13
I submitted a bug to the GRUB2 folks. See:
[https://savannah.gnu.org/bugs/index.php?29213](https://savannah.gnu.org/bugs/index.php?29213)

Regards,
-Sonic

---

### Post by psusi on 2010-03-13
It sounds like what happened is when you moved the other two drives and plugged in the vault, you changed the boot order your bios went through.  It sounds like it was booting from the vault which also had grub installed on it at that point.  Then when you removed it, your bios tried to boot from the third drive that apparently did not have grub on it.

By the way, are you sure you are using grub2 and not grub legacy?  With grub legacy it is much more likely to hang at loading grub because that is what the MBR says when it tries to load the grub stage2 file in /boot/grub, which fails if it can't find them, probably because that drive has been reformatted or repartitioned.  With grub2 the MBR loads the grub core which is hidden between the MBR and the first partition.  If at least the core loads ok, you will at least get a grub rescue prompt if it can't locate /boot/grub.

---

### Post by DuronForever on 2010-03-13
What happens, as I understand it, when GRUB boots, is it typically has a Stage 1 presence in the MBR of the boot drive, which then chainloads the real thing from /boot (if Stage 2) or the first few sectors of a particular drive (if stage 1.5) with a very direct type of link, that gets confused easily. Your /boot is on the sda drive, and by messing with the drive order of the s-disks, the MBR on the IDE disk (which should be an h-disk rather than an s-disk, and going through LVM for that matter -- I can't tell from what you've posted which physical /dev/xdyz drive(s) are functioning as PVs -- sudo pvdisplay please?) still loads but the drive with /boot on is no longer at exactly the same point of the sequence in the BIOS. 

Given the results, I would think that the controller that had your vault drive is first in sequence, and with your sda drive being identified in bios/grub as the second sata drive, that would change to the first drive, breaking the chainlink in the MBR. You could maybe fix that also by only changing the order of the first two drives on your secondary controller even when leaving the primary that had vault empty.

sudo pvdisplay ; cat /boot/grub/device.map ; cat /boot/grub/menu.lst | grep \(hd

ought to provide more useful information.

---

### Post by sonicnudge on 2010-03-16
Thanks for the feedback.

@psusi:
Here is grub-install -v:
grub-install (GNU GRUB 1.97~beta4)

@DuronForever:
Here is: pvdisplay ; cat /boot/grub/device.map ; cat /boot/grub/menu.lst | grep \(hd:
```

  --- Physical volume ---
  PV Name               /dev/sda1
  VG Name               fullback
  PV Size               57.03 GB / not usable 331.00 KB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              14600
  Free PE               10
  Allocated PE          14590
  PV UUID               fP5af0-NCpF-aIFx-cko0-o2Nz-R1cl-WMXG0x

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
(hd4)   /dev/sde
cat: /boot/grub/menu.lst: No such file or directory

```

Sincerely,
-Sonic

---

### Post by psusi on 2010-03-17
> **sonicnudge said:**
> 
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd
(hd4)   /dev/sde


And what are each of those drives currently, and which one is the bios set to boot from?  To work correctly, whichever one grub is installed to ( hd0 by default ) must be the drive your bios tries to boot.  This class of problem is caused by the fact that grub has no way of knowing how your bios sees the disks.  It guesses that the bios sees them in the same order the linux kernel does.  In other words, that hd0 is /dev/sda and so on.  If that guess is incorrect, then things break down.  You can edit device.map to correct the guess if it is wrong, and reinstall grub.

With grub2 it normally installs its core image to the hidden space between the MBR and the first partition.  Unless you manually install with additional options, both the MBR and core should always be installed to (hd0) AFAIK.  You hang loading grub when the MBR can't find the core, and the only way I can see that happening is if you somehow got the MBR on the drive the bios boots, but the core on another drive, and the bios's idea on which drive that is and the device.map listing of it do not agree, so the MBR is looking on the wrong drive.  I'm not sure how you can get this to happen though.

---

### Post by sonicnudge on 2010-03-23
psusi,

Here is the current output of df -hT:
```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/fullback-root
              ext4     54G  2.3G   50G   5% /
udev         tmpfs    375M  200K  375M   1% /dev
none         tmpfs    375M     0  375M   0% /dev/shm
none         tmpfs    375M  340K  375M   1% /var/run
none         tmpfs    375M     0  375M   0% /var/lock
none         tmpfs    375M     0  375M   0% /lib/init/rw
/dev/sda5     ext2    228M   54M  163M  25% /boot
/dev/sdb1      xfs    280G  271G  8.7G  97% /media/media-01
/dev/sdc1      xfs    298G  288G   11G  97% /media/media-02
/dev/sde1      xfs    298G  290G  8.5G  98% /media/media-03
/dev/sdd1      xfs    298G  290G  8.0G  98% /media/media-04

```

Per the above, /boot is set to hd0 (/dev/sda5). (My boot drive is an IDE HD plugged directly into the Mobo -- as it has been from the start, and I have not tweaked this device.)

Please let me know if you'd like me to run any additional commands.

(Maybe I missed something in your comments, however I still believe GRUB2 has a bug related to the issue I encountered.)

Thank you,
-Sonic

---

### Post by psusi on 2010-03-24
So your bios is set to boot from sda.  Was this also the case before you removed the vault?  Specifically did linux still see that drive as sda?  If the bios was still booting from it but linux detected another drive first and called that sda, that would explain the problem.

---

### Post by sonicnudge on 2010-03-24
psusi,

Linux has always booted from sda (the IDE drive).

Vault has always been on sdf. (The other "permanent" drives are sdb..e.)

I do not believe Linux is getting confused here -- I installed the full Ubuntu 9.10 (w/GRUB2) on a clean system to the IDE drive (sda) originally. I've never seen Linux report anything other than the current drive configuration for boot (sda via df -hT) -- just the absence or presence of vault on sdf.

Regards,
-Sonic

P.S.: I suppose I'm about done with this one. Whether or not GRUB2 has a bug or not, I've spent as much time as I care to on this issue. I know how to work around the situation/bug in the future, and hopefully someone else running into this situation/bug will be able to save some time through these posts. (And maybe the GRUB folks will look into my bug report, and either fix the bug or document the workaround.) Thanks again for all your feedback and best of luck!

---

### Post by justnice980 on 2010-03-30
there is a quick easy fix for this problem, one that doesnt require editing your fstab at all. i came ascossed this myself and was quite annoyed with it till i figured out how easy it was. first things first............remove all drives you want out of the system and power down. you may need to cycle the power a few times to get the load screen that looks like this one........[IMG]https://help.ubuntu.com/community/BootOptions?action=AttachFile&do=get&target=grubmenu.png[/IMG]

what you're going to want to do is press "E" to edit boot options. 

you will be presented with a screen that has the boot information. sorry but i do not have a screenshot for this. but it will contain info similar to this......

[SIZE=3]sh:grub> linux /boot/vmlinuz-[/SIZE][SIZE=3]2.6.31-[/SIZE][SIZE=3]14-generic root=/dev/sda2 loop=/ubuntu/[/SIZE][SIZE=3]disks/root.[/SIZE][SIZE=3]disk ro
sh:grub> initrd /boot/initrd.[/SIZE][SIZE=3]img-2.6.[/SIZE][SIZE=3]31-14-generic
sh:grub> boot[/SIZE]

(this is not my boot screen info, just some randomly typed stuff.) the entire problem is stemming from the fact  that ubuntu is looking for a device that wasn't there. all i had to do was change the values of the boot hdd[SIZE=4] [SIZE=1]from /dev/sda2 to /dev/sda1 or whatever number your physical boot volume is.[/SIZE]

[/SIZE][SIZE=4]2.6.31-[/SIZE][SIZE=4]14-generic root=/dev/[COLOR=Red]sda2[/COLOR] loop=/ubuntu/[/SIZE][SIZE=4]disks/root.[/SIZE][SIZE=4]disk ro[/SIZE]


[SIZE=4][COLOR=Red]changed to......[/COLOR][/SIZE]
[SIZE=4]
[/SIZE]
[SIZE=3]2.6.31-[/SIZE]
[SIZE=3]14-generic root=/dev/[COLOR=Red]sda1[/COLOR] loop=/ubuntu/[/SIZE][SIZE=3]disks/root.[/SIZE][SIZE=3]disk ro[/SIZE]


[SIZE=3][SIZE=1]once the change has been made, press  ctrl+x to boot. should boot into ubuntu fine when proper drive is edited in.[/SIZE][/SIZE]
[SIZE=3][SIZE=1]once you are in to the desktop open terminal and log in as root,  to do so type " su " and when prompted enter your password.[/SIZE][/SIZE]
[SIZE=3][SIZE=1]next, type the following command, " update-grub " without quotations of course[/SIZE][/SIZE]
[SIZE=1]
[/SIZE]
[SIZE=3][SIZE=1]all in all the entire process should look like this.....[/SIZE][/SIZE]


empire@empire-desktop:~$ su
Password: 
root@empire-desktop:/home/empire# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
File descriptor 4 left open
done
root@empire-desktop:/home/empire# 

that's it, grub will be back to normal and should boot successfully every time. sorry for lack of actual screenshots, but i'm kinda pressed for time and maybe i'll post a more in depth tutorial when i can find the time.

---

### Post by psusi on 2010-03-30
He wasn't even getting to the grub menu.  In any case unless you manually made it so, grub will not have root=/dev/sdanything.  It will be using the UUID by default which will work no matter what device the drive is on.

---

