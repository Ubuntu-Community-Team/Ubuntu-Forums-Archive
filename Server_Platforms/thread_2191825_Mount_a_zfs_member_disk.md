---
title: "Mount a zfs_member disk"
date: 2013-12-04
forum: Server Platforms
---

### Post by rossguil on 2013-12-04
Hello everyone!

I would like to get some support about importing a zfs filesystem on Ubuntu Server (v14.04, Trusty). How do I import a zfs_member disk?

The story behind this question is the following: I am unfortunately the IT guy of my family. I say unfortunately because we're 6 in my family and that makes a lot of sensible data. I built a nice server on top of a LSI Megaraid SAS 8888elp card, on which I hooked 6x2TB hdd's. I configured them in Raid 6, did some testing on raid expansion and then thought about which OS to install. Since at the time I was not willing to use another hdd for the operating system, I went for freenas 8 (it is a freebsd-based server, working from a usb key). That is where the story went ugly. FreeNas's preferred filesystem is ZFS, so I formatted the raid disk as ZFS. It was pretty straightforward because the raid card showed the raid array as a big, 7.8 tb disk. _-> I did not know at the time that ZFS on top of hardware raid is a bad thing to do. Now I do._

I went away for the summer to go work in another province. Unfortunately while I was away, 3 of the disks (Yes, 3!!) went bad, or missing, or otherwise not detected by the raid card. When I came back, I proceeded to carefully ddrescue every "bad" disk onto a new one, juggling with the rma procedures and finally got the array back together. The hardware raid array is now working "fine", at least for the raid card. It is on the software side that it is not working at all. Freenas 8 doesn't see the drives as a valid Zfs filesystem, nor does Ubuntu (I finally plugged in an extra disk just for Ubuntu, directly on the motherboard and not connected to the raid card).

I can see the big raid disk in ubuntu. I can use the megacli tool to manage it (the command line tool provided by msi to manage a hardware raid). I just cannot mount it to check if the data is still there, or if anything is retrievable.

I ran a nice and new-to-me command to get the info I needed, so here is the output if it can help:
```
famille@CXTO:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                   FSTYPE        SIZE MOUNTPOINT LABEL
sda                    zfs_member    7.3T            Data
sdb                                931.5G
ââsdb1                 ext2          243M /boot
ââsdb2                                 1K
ââsdb5                 LVM2_member 931.3G
  ââCXTO-root (dm-0)   ext4        928.1G /
  ââCXTO-swap_1 (dm-1) swap          3.1G [SWAP]
sr0                                 1024M

```
Of course, importing the zpool doesn't work with the traditional zfs or zpool commands.

Thanks for your time, and any help would be much appreciated!

P.S.: The important data such as photos or documents were saved on my backup server. I was able to remotely get the backup online this summer, so the unrecoverable stuff is not so lost if I have to completely wipe the disks and start back form scratch.

---

### Post by rossguil on 2013-12-11
Don't know if it's legal or not but... *bump*

---

### Post by cariboo on 2013-12-11
Have a look at the zpool, the manpage is [here]("http://manpages.ubuntu.com/manpages/lucid/man1/zpool.1M.html"). Zpool is a part of the zfs-fuse package.

BTW, it's OK to bump your thread after 24 hours, if there hasn't been any activity.

---

### Post by rossguil on 2013-12-12
Thanks for the input on the *bump* policy of this forum, I was not sure.

As for the zpool command from the zfs-fuse package, I have tried unsuccessfully to mount the device (/dev/sda) using
```
famille@CXTO:~$ sudo zpool import -d /dev/sda Data
cannot open '/dev/sda/': Not a directory
cannot import 'Data': no such pool available
```

Opening my eyes a little bit more (RTFM), I tried using only the import option for destroyed pools, and so (to my astonishment) I got:
```
famille@CXTO:~$ sudo zpool import -D -f
  pool: Data
    id: 15256612932731819672
 state: UNAVAIL (DESTROYED)
status: The pool is formatted using an incompatible version.
action: The pool cannot be imported.  Access the pool on a system running newer
        software, or recreate the pool from backup.
   see: http://www.sun.com/msg/ZFS-8000-A5
config:

        Data                                                 UNAVAIL  newer version
          disk/by-id/scsi-3600605b0005f1760185a2d7b1e9029d8  ONLINE
```

Ooook. Now I think I am getting somewhere... I plugged my FreeNAS's USB key on my laptop just to access the shell, and asked it what zpool version it was running. It seems that FreeNAS is running on ZFS pool version 28.

I double-checked on my Ubuntu box to see what version of ZFS it was running, and it seems that "only" version 23 is installed.

I'll google how to install the 28th version of ZFS on the Ubuntu box and keep updating this thread. If you have any insight, comments or jokes relevant to the topic feel free to comment and provide some input.

---

### Post by rossguil on 2013-12-12
Well

I bumped on the fact that my server's version was too high for the zfs packages. I had to re-install an earlier version (13.10). Also, to get the last ZFS version possible, I installed ubuntu-zfs instead of fuse. After about 2 hours of installing, re-configuring and tweaking, I managed to finally mount the pool with the "-D" option specified. It showed as empty.

I give up, letting go on the possibility of recovering data.

Let's get back to ripping my CD collection!

That's all folks!

---

