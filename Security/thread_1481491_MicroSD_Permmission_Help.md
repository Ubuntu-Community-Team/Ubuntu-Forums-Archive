---
title: "MicroSD Permmission Help"
date: 2010-05-12
forum: Security
---

### Post by Th3Blaze on 2010-05-12
Hi.
I have a microSD card I use for my NDS.
Recently(I think) when I try to put games on it, it doesn't come up with the paste button.
I could do it before and it isn't full and helP?

---

### Post by cdenley on 2010-05-12
Are you sure the write-protect tab hasn't been slid over?

---

### Post by Th3Blaze on 2010-05-13
Thanks for the help but what do you mean?

---

### Post by cdenley on 2010-05-13
> **Th3Blaze said:**
> Thanks for the help but what do you mean?

[http://en.wikipedia.org/wiki/Secure_Digital#Optional_write-protect_tab](http://en.wikipedia.org/wiki/Secure_Digital#Optional_write-protect_tab)

---

### Post by Th3Blaze on 2010-05-14
Oh right,
I haven't got one.
I have put games on before, but I had to change users and It says I don't have permmision. Any help?

---

### Post by cdenley on 2010-05-14
What filesystem is on it? How is it being mounted?
```

cat /proc/mounts

```

---

### Post by Th3Blaze on 2010-05-14
I don't know what you mean?
/media/(foldername)
USB?

---

### Post by cdenley on 2010-05-14
> **Th3Blaze said:**
> I don't know what you mean?
/media/(foldername)
USB?

Filesystem, as in FAT32, NTFS, EXT3, EXT4...

If you don't know what I mean by mount, I would assume it is mounted through nautilus? Posting the output from the command I gave you would show me what mount options were used.
```

cat /proc/mounts

```

---

### Post by Th3Blaze on 2010-05-14
Do I put it in terminal?
It is FAT32.

---

### Post by cdenley on 2010-05-14
> **Th3Blaze said:**
> Do I put it in terminal?

Yes.

Applications>Accessories>Terminal

Also, immediately after your filesystem is mounted, run this command and post that output as well.
```

dmesg|tail

```

---

### Post by Th3Blaze on 2010-05-14
Ok

[spoiler][14214.055406] sr: Sense Key : Hardware Error [current] 
[14214.055414] sr: Add. Sense: Media load or eject failed
[14220.352366] sr0: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[14220.352389] sr: Sense Key : Hardware Error [current] 
[14220.352397] sr: Add. Sense: Media load or eject failed
[14223.256522] FAT: Filesystem error (dev sdb1)
[14223.256532]     fat_get_cluster: invalid cluster chain (i_pos 0)
[14226.649122] sr0: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[14226.649145] sr: Sense Key : Hardware Error [current] 
[14226.649153] sr: Add. Sense: Media load or eject failed
 [/spoiler]

Can u not do spoilers?

---

### Post by cdenley on 2010-05-14
> **Th3Blaze said:**
> Ok

[spoiler][14214.055406] sr: Sense Key : Hardware Error [current] 
[14214.055414] sr: Add. Sense: Media load or eject failed
[14220.352366] sr0: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[14220.352389] sr: Sense Key : Hardware Error [current] 
[14220.352397] sr: Add. Sense: Media load or eject failed
[14223.256522] FAT: Filesystem error (dev sdb1)
[14223.256532]     fat_get_cluster: invalid cluster chain (i_pos 0)
[14226.649122] sr0: CDROM (ioctl) error, command: Start/Stop Unit 1b 00 00 00 03 00
[14226.649145] sr: Sense Key : Hardware Error [current] 
[14226.649153] sr: Add. Sense: Media load or eject failed
 [/spoiler]

Can u not do spoilers?

There is the output from one command, but it's not too useful since you seem to have attempted to eject a CD before you ran it.

---

### Post by Th3Blaze on 2010-05-15
I didn't its just a automatic folder.
Anyhelp yet?
I just want to know how to chnage the permmision of a folder

---

### Post by cdenley on 2010-05-15
> **Th3Blaze said:**
> I didn't its just a automatic folder.
Anyhelp yet?
I just want to know how to chnage the permmision of a folder

FAT32 doesn't have linux permissions, so they are assigned at mount time. If you let nautilus mount it, then it should be owned by the user you are logged in as. If it is read-only, then I suspect the device is detected as read-only, but you still haven't posted the output to confirm that.

---

### Post by Th3Blaze on 2010-05-15
how do I get that?
I know how to boot natilus
sudo natilus

It says Sorry, could not change the owner of "88F4-FD07_": Error setting owner: Read-only file system
I am on as root and it says that I am owner but it won't let me copy or extarct stuff on it

---

### Post by cdenley on 2010-05-15
Get what? Why are you using sudo to launch nautilus?

---

### Post by Th3Blaze on 2010-05-15
post the output.
And what do I have to do to change the permmision?

---

### Post by cdenley on 2010-05-15
You post output from commands with copy/paste, like you did before.

---

### Post by Th3Blaze on 2010-05-15
Ok.
What do I put in the terminal?

My cat/proc/mounts output:
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
none /proc proc rw,nosuid,nodev,noexec,relatime 0 0
none /dev devtmpfs rw,relatime,size=250052k,nr_inodes=62513,mode=755 0 0
none /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
/dev/disk/by-uuid/91cafa31-65b2-42bf-b88d-847025ad90b7 / ext4 rw,relatime,errors=remount-ro,barrier=1,data=ordered 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /var/run tmpfs rw,nosuid,relatime,mode=755 0 0
none /var/lock tmpfs rw,nosuid,nodev,noexec,relatime 0 0
none /lib/init/rw tmpfs rw,nosuid,relatime,mode=755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0
gvfs-fuse-daemon /home/joel/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1009,group_id=1009 0 0
gvfs-fuse-daemon /home/th3blaze/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,relatime,user_id=1011,group_id=1012 0 0
/dev/sdb1 /media/88F4-FD07_ vfat ro,nosuid,nodev,relatime,uid=1011,gid=1012,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro 0 0

---

### Post by cdenley on 2010-05-15
Nautilus is mounting readonly, so it must see the device as write-protected. Run this command again, but immediately after the drive is mounted.
```

dmesg¦tail

```

---

### Post by Th3Blaze on 2010-05-15
It says no such command

---

### Post by cdenley on 2010-05-15
> **Th3Blaze said:**
> It says no such command

The same command you ran before. I can't type the pipe character on my phone.

---

### Post by Th3Blaze on 2010-05-16
Sorry.
[59332.817717] FAT: Filesystem error (dev sdb1)
[59332.817721]     fat_get_cluster: invalid cluster chain (i_pos 0)
[59332.820626] FAT: Filesystem error (dev sdb1)
[59332.820630]     fat_get_cluster: invalid cluster chain (i_pos 0)
[59332.831318] FAT: Filesystem error (dev sdb1)
[59332.831328]     fat_get_cluster: invalid cluster chain (i_pos 0)
[59332.832915] FAT: Filesystem error (dev sdb1)
[59332.832920]     fat_get_cluster: invalid cluster chain (i_pos 0)
[59341.669891] FAT: Filesystem error (dev sdb1)
[59341.669902]     fat_get_cluster: invalid cluster chain (i_pos 0)

This is unrelated but Imgburn won't pick up my disc.
I am using it on Wine on Ubuntu 10.04L

---

### Post by Th3Blaze on 2010-05-16
Done!
Come on I really want some new games.

---

### Post by OpSecShellshock on 2010-05-16
> **Th3Blaze said:**
> Sorry.
[59332.817717] FAT: Filesystem error (dev sdb1)
[59332.817721]     fat_get_cluster: invalid cluster chain (i_pos 0)
[59332.820626] FAT: Filesystem error (dev sdb1)
[59332.820630]     fat_get_cluster: invalid cluster chain (i_pos 0)
[59332.831318] FAT: Filesystem error (dev sdb1)
[59332.831328]     fat_get_cluster: invalid cluster chain (i_pos 0)
[59332.832915] FAT: Filesystem error (dev sdb1)
[59332.832920]     fat_get_cluster: invalid cluster chain (i_pos 0)
[59341.669891] FAT: Filesystem error (dev sdb1)
[59341.669902]     fat_get_cluster: invalid cluster chain (i_pos 0)

This is unrelated but Imgburn won't pick up my disc.
I am using it on Wine on Ubuntu 10.04L

Did a quick check on the error and it appears that it's a sign of corruption on the disk or of it not having been un-mounted properly. Unfortunately all of the solutions I've seen have involved reformatting.

---

### Post by Th3Blaze on 2010-05-16
How do I do that?
I've backed it up.
What am i formatting it to?

---

### Post by OpSecShellshock on 2010-05-16
Easy way? Select the Applications menu in the panel, then go to Ubuntu Software Center. In the search box, start typing Gnome Partition Editor until it comes up. If it has a green check on it, then it's installed. If not, then install it.

When it's installed, it will appear under System-->Administration-->GParted. This requires escalation of privileges to run. OK, so then you'll need to proceed carefully. Make sure you select the correct disk from the menu. Hopefully it's the only one of that size that's connected so there's no confusion. If it's mounted, you'll need to right click on it and select Unmount. Once that's done, right click again and select Format To-->FAT32. If you want to give it a name, right click and select Label, then give it a name. After that, click on the Apply icon at the top. It will do its thing, and when it's done it still won't be mounted. The new-user-friendly way to mount it is to just remove it and then put it back in. It should open on its own in Nautilus, at which point I think you can just copy your files back over.

Can't guarantee that it will be readable by the DS at that point, so hopefully you've read this far prior to doing anything. It's possible that the firmware of the DS is what's causing the problem if the lock-slider isn't what's causing it.

---

### Post by Th3Blaze on 2010-05-17
FIXED!
Can anyone help with the IMgburn thingy?
Is there any ubuntu program that I can use that will burn iso's/ images?

---

### Post by cdenley on 2010-05-17
> **Th3Blaze said:**
> FIXED!
Can anyone help with the IMgburn thingy?
Is there any ubuntu program that I can use that will burn iso's/ images?

Brasero burns .iso images. It should be installed by default. You should also be able to right-click the file, then select "write to disc". In the future, you should first try to find a solution by searching the forum, google, etc. If there isn't already a thread for your question and you were unable to find a solution, then you should start a new thread (not in an unrelated thread).
[https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu](https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu)

---

### Post by Th3Blaze on 2010-05-17
sorry thanks everyone bye!

---

