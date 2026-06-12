---
title: "Complete System Backup"
date: 2010-01-26
forum: Server Platforms
---

### Post by fiveironfrnzy08 on 2010-01-26
Hey everyone,

I have a system running Ubuntu 9.10 that has a lot of specific packages and configurations on it (apache configurations, wireless card driver alterations, etc.) that I don't want to have to redo. What can I use to make and image of my entire installation, packages, files, configurations, and all?

Thanks in advance!

---

### Post by bluefrog on 2010-01-26
make an image with partimage

---

### Post by ian dobson on 2010-01-26
Hi,

Have a look at dd, it'll copy an complete drive to another drive/file.

regards
Ian Dobson

---

### Post by Bubbel on 2010-01-27
Hi,

Well, you can do your backup as a one-timer, or regularly.

If you want to do it just once, the best way is to boot from CD, using a SysRescueCD [http://www.sysresccd.org]("http://www.sysresccd.org")
mount your backup target and do the archiving.
Boot the CD with default options.
Assuming you want to backup /dev/sda1 to a USB disk /dev/sdb1:
```
mkdir /mnt/targetfs
mount /dev/sdb1 /mnt/targetfs
fsarchiver -z 6 -s 2000 savefs /mnt/targetfs/backup.fsa /dev/sda1
```
This makes 2GB file parts (hence the -s 2000 option) so that the FAT32, that  usually is the filesystem on USB mass-storage, doesn't throw you an error.

For a regular backup I'd go with another configuration. I would put your root on an LVM2 volume and make a snapshot of the root and rsync that to another computer. This though is somewhat more complex than the first option, but when done right, it's a set-it and forget-it option.
Just for the record. I make regular backups now of my server. I still need to test a disaster restore. Will do that soon.

Hope this helped.

Gretings, Bubbel:KS

---

### Post by HermanAB on 2010-01-28
Howdy,

I would just save a tar ball of /etc.  The rest shouldn't matter since programs are easy to install using 'apt get', it is the configuration settings that are the problem and they are all in /etc.

---

### Post by kamaji792 on 2010-01-28
> **HermanAB said:**
> Howdy,

I would just save a tar ball of /etc.  The rest shouldn't matter since programs are easy to install using 'apt get', it is the configuration settings that are the problem and they are all in /etc.

Thank you HermanAB.  That was a really useful piece of information.

---

### Post by Bubbel on 2010-01-29
> **kamaji792 said:**
> Thank you HermanAB.  That was a really useful piece of information.
As in Simplicity is the key.
Bare in mind though that a quick-and-easy restore is not in question.
When you recreate the base OS, you need to hand-pick the correct files and edit some where needed. For instance the /etc/fstab file is not to be overwritten. When fstab is overwritten by the backup one, you have a good chance your system does not boot or gets hung-up in error messages.
Also be aware that the /home, as well as /opt and /usr/local can all contain valuable extra packages, or data you don't want to loose.

It's all up to you. An easy backup, a complex restore. Or the other way around. Speaking for myself I'd rather be safe than sorry. But then again, that's my take on it.

Good luck in with the backup. Hope you 'll never have to restore, whatever the backup scheme is you will follow.

Bubbel :KS

---

### Post by OldGrantonian on 2010-02-02
I use fsarchiver for my system partition, and rsync for my data partion. Here's a comparison between fsarchiver and partimage:
[http://www.fsarchiver.org/Fsarchiver_vs_partimage](http://www.fsarchiver.org/Fsarchiver_vs_partimage)

Another advantage of fsarchiver is that the size of the backup file (and the time) depends on the number of files on the backed-up partition. I think some cloning software backs up the empty space in the partition :)

When you restore, you don't need to edit any files. If your system worked OK when you backed it up, then you will get an identical system when you restore it.

I use rsync for data, because it's incremental, and I can work with individual files.
.

---

### Post by vpadro on 2010-02-02
You could use remastersys as a custom install DVD...

---

