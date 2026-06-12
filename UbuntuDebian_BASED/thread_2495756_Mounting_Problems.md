---
title: "Mounting Problems"
date: 2024-02-29
forum: Ubuntu/Debian BASED
---

### Post by Hasimir on 2024-02-29
I'm running PopOS and, after a recent clean install, I'm having some problems with a secondary HDD I use for data storage.


***My Partitions***

One disk /dev/***sda1** "data" is a 1Tb hdd NTFS logical partition for Basic Data. It is mounted as /mnt/data

One disk /dev/**sdb1** is a 500Gb ssd with multiple partitions:

- 1Gb FAT32 /boot/efi /dev/sdb1

- 17Mb Microsoft reserved thing /dev/sdb2

- 150Gb NTFS win10 system

- 4Gb swap /dev/sdb4

- 105Gb ext4 /home  /dev/sdb5

- 251Gb ext4 / (my popOS root)  /dev/sdb7

- 523Mb Microsoft recovery thing /dev/sdb6

This way my system and apps are in /.
My /home is separate and independent.
And I dump pretty much all my files and downloads in the external drive "data".

Data is mounted like so:

UUID=70D48E04D48DCD32
/mnt/data
ntfs
rw,auto,user,exec,noatime,errors=remount-ro,nofail,x-gvfs-show
0
0

It seems to work ok, except...

***Problems***
First, I can't trash files. I only have the option to **permanently delete** them (which on my Nautilus is set to NOT be available, btw).

Second, my browser saves downloads wrong.
Edge/Opera/Chrome always ask me where to download files even though I set a default directory and toggled off the option to always prompt me for action.
Looking into it, I noticed that while I set the download directory as **/mnt/data/myName/Downloads** the browsers interpret it instead as this weird thing **/run/user/1000/doc/a0207089/Downloads**

Interestingly, **Firefox** doesn't show this behavior and does everything as expected.
I assume the two problems might be related.
How can I fix them?

This is my fstab:
```

PARTUUID=c262783b-5cf0-47cc-aaa2-c1ca59b38cd6  /boot/efi  vfat  umask=0077  0  0

/dev/mapper/cryptswap  none  swap  defaults  0  0

UUID=492f3857-56c4-44a7-ba34-2145fc8c8048  /home  ext4  noatime,errors=remount-ro  0 0

UUID=ba17cb87-0f71-41e2-97a2-4ccc889ead63  /  ext4  noatime,errors=remount-ro  0  1

UUID=70D48E04D48DCD32 /mnt/data ntfs rw,auto,user,exec,noatime,errors=remount-ro,nofail,x-gvfs-show 0 0

```

---

### Post by oldfred on 2024-02-29
Generally better to use Linux formats for most Linux data. I typically used a NTFS partition only for some data that I wanted to share.
Windows now has made used of NTFS more difficult. It uses fast start up which sets hibernation flag. And it turns it back on with updates.
If hibernation flag seen, Linux NTFS driver will not write into NTFS to prevent loss of data. When Windows restores hibernation, it will not see anything written from Linux.

Windows turns fast startup back on with updates. And you may not always see Windows update in background.
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

Several users have posted suggest parameters for mounting NTFS. no space in async
> nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000

[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
[https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822](https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822)
Supposedly big-writes always on, now
[https://unix.stackexchange.com/questions/536971/disadvantages-of-ntfs-3g-big-writes-mount-option](https://unix.stackexchange.com/questions/536971/disadvantages-of-ntfs-3g-big-writes-mount-option)

Mount parameter examples, ext4, NTFS, exFAT:
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)
[https://ubuntuforums.org/showthread.php?t=2493845](https://ubuntuforums.org/showthread.php?t=2493845)

---

### Post by TheFu on 2024-02-29
Rather than use words, please run commands and post the command + the output here, wrapping the output in code tags as you did for the fstab.  This avoids all sorts of issues with words and attempted transcriptions. For mounted storage, this command is best:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

For all storage, 
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```

Nobody should type those, ever. Create aliases for both.

First, NTFS should be avoided, unless that specific partition will be physically connected to a MS-Windows computer.  For networked access or access to 100% Linux computers, use a native Linux file system like ext4.

Trash is implemented by the DE and those implementations are far from perfect. I disable them and use daily, versioned, backups, to get any files back, if needed. There is a gap when the files are created until the first backup runs, when if something is corrupted or deleted, then it has to be recreated.  Since I seldom use any DE and basically never use a GUI file manager, it really doesn't matter. If you don't use a DE and certain GUI file manager, the Trash location won't be created and may not be possible on foreign disks anyway.

Assuming this fstab is correct, 
```
UUID=70D48E04D48DCD32 /mnt/data ntfs rw,auto,user,exec,noatime,errors=remount-ro,nofail,x-gvfs-show 0 0
```
You are missing the owner, group, and permission masks which are mandatory for foreign file systems like NTFS, exFAT, FAT32 and others.

Making lots of assumptions, I would suggest this line instead:
```
UUID=70D48E04D48DCD32    /mnt/data    ntfs    [COLOR="#FF0000"]nodev,windows_names,nosuid,noatime,async,big_writes,uid=1000,gid=1000,fmask=0002,dmask=0002[/COLOR]    0    0
```
Comment out your current line and copy/paste the one provided. Next run
```
sudo umount  /mnt/data
sudo mkdir /mnt/data
sudo mount -a
```

Like I said, I made lots of assumptions, mainly about the userid and group. I also added some security protections and performance stuff. If you like, you could add noatime, but I don't bother.  NTFS handles mtime, ctime, atime differently.

I can't help with snap packages. I don't use them. On Ubuntu Firefox and Chromium are snaps unless you go out of your way. I know nothing about PopOS.

BTW, if you label a partition in the partitioning tool, then you can mount using **LABEL=** rather than those offensive UUIDs. Best not to have spaces or mixed case in a LABEL to avoid some issues.  Additionally, the LABEL will be used if you allow the GUI tools to mount storage. You shouldn't do that for many reasons, but whatever. People do it all the time because convenience overrules security 99% of the time.

---

### Post by Hasimir on 2024-02-29
Fixing the fstab file as you explained has (allegedly) solved whatever problem my Data drive had. It not mounts nicely and the trash bin works :D

The browser download location problem still persists ](*,)

I'm thinking it's something to do with how the (latest?) chromium browsers work, as it affects Chrome, Edge and Opera... but not Firefox :-k

Any ideas?
Things I could do to gather more info?

> [COLOR=#000000]I can't help with snap packages. I don't use them. On Ubuntu Firefox and Chromium are snaps unless you go out of your way. I know nothing about PopOS.[/COLOR]
PopOS uses mainly DEBs, as far as I can tell.

---

### Post by &amp;KyT$0P# on 2024-02-29
> **Hasimir said:**
> The browser download location problem still persists ](*,)

Do you have the affected browsers installed as flatpaks?  If so, you could try installing [flatseal]("https://flathub.org/apps/com.github.tchx84.Flatseal") and explicitly adding Filesystem access to your download folder for each of the browsers.

---

### Post by Hasimir on 2024-03-01
Solved!
What I found is: my browsers were all installed through the PopOS Shop software manager.
It supposedly installed them as DEBs (some offer an option to be flatpacks, but I always opt for deb).
Still, THAT seemed to be the problem, as multiple re-installs fixed nothing.

So I tried to instead install from an actual DEB file downloaded from the official website... and it fixed the problem. Go figure o_O

---

### Post by TheFu on 2024-03-01
Ubuntu Software Center seems to prefer snap packages rather than debians. I don't use a GUI for package management, so I don't really know how or if they denote snap vs deb packages.  I do know that the firefox and Chromium .deb packages in Ubuntu are just wrappers around the snap package for each.  Feels like a bait and switch scam to me.

---

