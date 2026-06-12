---
title: "Clean install fails to reboot"
date: 2010-05-17
forum: Server Platforms
---

### Post by KLStringer on 2010-05-17
I'm installing 10.4 x64 on a Dell PowerEdge R610 RAID 1 and the install goes fine until I have to reboot the finish it. On reboot after about a minute it gives the error

```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline/
     -check rootdelay= (did the system wait long enough?)
     -check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/mysql1-root does not exist. Dropping to shell!
```And then it drops to a (initramfs) at which point I have no idea what to do and my co-worker who knows a little more about Linux can't get it to let him check any of the above common problems.

We're tried letting GRUB manually configure itself at the end og the install before we reboot and we've also pointed it to /dev/sba partition which is what should be the boot partition.


EDIT: in the code tag it's ALERT! /dev/mapper/mysql(one)-root....  the L and 1 look the same

---

### Post by KLStringer on 2010-05-17
From the (initramfs) I can cd to /dev/mapper/ and mysql1-root does exist why it can't be found during boot I have no idea or any idea how to make it find it.

---

### Post by KLStringer on 2010-05-18
Still can't get this to work. Has anyone tried setting up a x64 10.04 server?

---

### Post by eltonw on 2010-05-18
> **KLStringer said:**
> Still can't get this to work. Has anyone tried setting up a x64 10.04 server?

First things first: did you check and verify the MD5SUMS of the ISO image after downloading and before burning the CD?

---

### Post by KLStringer on 2010-05-18
Yes and they matched

---

### Post by irv on 2010-06-08
Here is a link to fix a Linux system.
[http://manpages.ubuntu.com/manpages/lucid/man8/fsck.8.html]("http://manpages.ubuntu.com/manpages/lucid/man8/fsck.8.html")
You will need to get to a command line to fix the system.

---

### Post by KLStringer on 2010-06-08
That looks interesting and I'll have more time tomorrow to mess with it, but what am I doing with it? How do I tell it to fix my system so that it'll boot?

---

### Post by irv on 2010-06-09
Here is another thing you might want to try. Go to this link: [https://help.ubuntu.com/community/LiveCD]("https://help.ubuntu.com/community/LiveCD")
Just a little way down the page you will see 
> Reasons for Using a LiveCD Session
I believe there is a way to fix the system from a command prompt when you run the live CD and go to a terminal. Hopefully someone can give you more direction. I will not be at my computer for the rest of the Day, maybe later this afternoon, so I hope someone will jump in.
Before I go I just want you to post if you can get to the grub menu. If so you can boot in to a command line and run a menu which allows you to run a fix on the system. I have done it before, but can't remember exactly how to do it.

---

### Post by KLStringer on 2010-06-09
I've got a LiveCD, booted into it, and read the fsck page, not sure where to go from here other than to run fsck but I don't know what flags I should use with it.

---

### Post by KLStringer on 2010-06-09
While booted into the LiveCD I mounted /dev/sda1 which is the boot partition created during install to /mnt and went to look and see what was in /dev/mapper and there is no /dev/mapper at all. No idea if that means anything, just thought that I'd mention it in case it does mean something.

---

### Post by irv on 2010-06-09
Well, I am back online and sitting in a motel room in LaCrosse WI. I tried to boot to Recovery mode to see if I could tell you how to run the repair or at lease get to the menu to do the fix. There seem to be a problem in booting to recovery mode on my laptop. It just hangs. I had to reboot and bootup normal. So at this point I can't give you any directions. I sure hope someone will pickup on this so you can get going. Is it possible to start from scratch with a clean install? Are you duel booting with Windows. or just running Ubuntu. If you can boot with live CD and recover your data, then I would do the clean install.

---

### Post by karesmakro on 2010-06-09
It seems to me, that you have a kernel problem, as one ore more modules can't be loaded! I'm not sure, if the root system is mounted, because you got this message:
```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline/
     -check rootdelay= (did the system wait long enough?)
     -check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/mysql1-root does not exist. Dropping to shell!
```
One hint: the devices are created on booting the system and this is the reason, why your /dev folder is empty while mounting your filesystem on a live cd (same to /proc folder).

I had the same problem on my system, I got a kernel panic after fresh installation and rebooting the system!
The only solution to get a working 10.04 system for me was, to install the system and create my own kernel! But this is more complicated and very complex

I suspect a kernel bug, but I do not find the time to investigate :(

---

### Post by KLStringer on 2010-06-09
It's a clean install, we haven't put these servers into production yet since we can't get passed this problem. I've also got a thread about it in the Install and upgrade forum (linked below). I know cross posting is usually frowned upon in most forums but I figured posting here and there would get me the most exposure and hopefully a solution.

[http://ubuntuforums.org/showthread.php?t=1487227](http://ubuntuforums.org/showthread.php?t=1487227)


From the other thread I booted into the LiveCd, mounted the boot partition /dev/sda1 and went to see what was in the dev/mapper/ folder only to find that it's no longer being created when I do a fresh install (did a new one this morning).

On 1 of the other 3 servers we have that have the exact same hardware configuration we installed CentOS to test it out and didn't have any problems with it installing or booting up. Looking in that server we saw that it had 3 files in /dev/mapper control, VolGroup00-LogVol00, & VolGroup00-LogVol01 so we created /dev/mapper and the 3 files then tried editing GRUB during boot to look in dev/mapper for the boot information but it still wouldn't boot.

I'm at home now, but will be back in the office in a few hours to continue trying to get this sorted out. I will provide more details of what we tried once I get back there as I don't have all my notes with me.

---

### Post by KLStringer on 2010-06-09
> **karesmakro said:**
> It seems to me, that you have a kernel problem, as one ore more modules can't be loaded! I'm not sure, if the root system is mounted, because you got this message:
```
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline/
     -check rootdelay= (did the system wait long enough?)
     -check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/mysql1-root does not exist. Dropping to shell!
```One hint: the devices are created on booting the system and this is the reason, why your /dev folder is empty while mounting your filesystem on a live cd (same to /proc folder).

I had the same problem on my system, I got a kernel panic after fresh installation and rebooting the system!
The only solution to get a working 10.04 system for me was, to install the system and create my own kernel! But this is more complicated and very complex

I suspect a kernel bug, but I do not find the time to investigate :(


If it is a kernel bug then it's a more serious issue especially since this is the server release and a LTS one at that. I know that its hard to test every situation when coding an OS release but I'd like to believe that RAID support would be one of the things that got beat to death during testing, then kicked a few more times just to make sure it was dead..errr working.

You say that you got it working by creating your own kernel, how did you go about doing that? Any how to's or walk trough's that you could link would be most helpful. While I may be new to the Linux environment I'd love to learn more about it and how to create my own kernel is something I'd like to know how to do from both a career and personal prospective.

---

### Post by KLStringer on 2010-06-09
OK from my notes after we made the 3 above mentioned files we rebooted and edited GRUB from:

```
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9\a54
linux /boot/vmlinux-2.6.32.31-server root=UUID=77e9b156-7d83-476a-b930-4475f04a9\a54 ro     quite    
initrd /boot/initrd.img-2.6.32.21-server
```TO:
```

recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 77e9b156-7d83-476a-b930-4475f04a9\a54
linux /boot/vmlinux-2.6.32.31-server root=MAPPER=VolGroup00-LogVol00 ro     quite    
initrd /boot/initrd.img-2.6.32.21-server
```

Which gave an error that /dev/mapper didn't exist,then we tried taking out line 3 and changing line 4 to oot=MAPPER=VolGroup00-LogVol00 which gave an error as well, then we tried setting line 4 to root=PATH=pci-0000:03:00.0-scsi-0:1:0:0-part1 whcih gave an error as well.

I also ran gparted while booted into the LiveCD and had it check /dev/sba1 I attached the file that it created. One thing that I noticed is that sda1 is ext4 format. I don't know waht the 'insmod ext2' line from GRUB means (and couldn't find anything on it either) but I tried changing it to insmod ext4 on the off chance that it was looking for the wrong file system type. 

In the end nothing we tried this afternoon worked.
:sad::-?

---

### Post by ronparent on 2010-06-11
This problem is driving me crazy. Just out of curiosity, do you see the drive your 10.04 is installed to in System>Administratiom>Disk Utility. If so, by highlighting the partition, under 'Device:' you will see the raid handle of the partition you are installed to. It will show the 'Mount Point:' as '/'. We might be able to deduce the root for that array. That root is where the grub MBR has to be written.

Umde 'Disk Utility' your actual raid disks, SATA or PATA will show as unpartitioned. My raid partitions show under 'Peripheral Devices'. Hopefully the live cd will produce the desired results.

---

### Post by KLStringer on 2010-06-11
A reply from [Brachus12]("http://ubuntuforums.org/member.php?u=1093677") to my thread in the install & upgrade forum lead me to 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7744000](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7744000)

and adding the rootdelay=90 solved our problem. :guitar:=D>\\:D/

Thanks everyone for all the help getting this sorted out, there's noway I would have figured it out on my own.

---

### Post by irv on 2010-06-11
> **KLStringer said:**
> A reply from [Brachus12]("http://ubuntuforums.org/member.php?u=1093677") to my thread in the install & upgrade forum lead me to 

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7744000](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=7744000)

and adding the rootdelay=90 solved our problem. :guitar:=D>\\:D/

Thanks everyone for all the help getting this sorted out, there's noway I would have figured it out on my own.

It great to see this one solved. Maybe you should make a note in the other thread on installing and upgrading in case someone else has this same problem.

---

