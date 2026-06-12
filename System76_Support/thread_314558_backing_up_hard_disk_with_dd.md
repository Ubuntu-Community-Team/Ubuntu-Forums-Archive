---
title: "backing up hard disk with dd"
date: 2006-12-07
forum: System76 Support
---

### Post by eleach on 2006-12-07
I have a Gazelle laptop. So far it looks and behaves great.

In my desktop machine I have two internal hard disks. To backup I boot from a live cd and do dd from one hard disk to the other. I realize this isn't the most efficient way of doing a backup, but it is very effective.

What would be the best way to do this from a laptop? I've heard that this works best if you are copying to/from disks of same make and size.

I have an 80 gig hard disk in the laptop. I assume I'd have to attach an 80+ gig disk through a USB port.

Thanks for any advice.

---

### Post by crichell on 2006-12-08
I really like Mondo for backups.  Not only do you backup your file system but also the entire machine to a bootable iso.  If you have to restore you can restore the entire machine.

The downside comes when you want to restore a single file or group of files.

I just installed "simplebackup" which looks like it may be a good tool.  Once I ran simplebackup i got this though:

carl@lincoln:~$ simplebackup 
stat: cannot stat `/home/carl/.simplebackup.conf': No such file or directory
/usr/bin/simplebackup: line 42: /home/carl/.simplebackup.conf: No such file or directory

Looks like some config may be necessary.

---

### Post by crichell on 2006-12-08
scratch that earlier post - sbackup looks better

```
sudo apt-get install sbackup
```

Go to System > Administration > Simple Backup Config to give it a shot

---

### Post by newlinux on 2006-12-11
rsync or grsync (gui to rsync) works good for basic file backup as well. You could write a decent script for rsync or just periodically run grysnc.

---

### Post by rafttrip on 2008-03-20
Hello there I am a very new user and I just got my system running with everything working.
I want to make a backup that I can restore my computer to a working state if I make some mistake later on. I am not looking to back up my files (they get backed up separately), I just don't want to go through the whole setup/configuring if I have to reload my OS.I tried QuickStart and it makes a backup of files fine but it seams to me there must be a simple way to back up my system.

In the past I have used Ghost to do this. I would definatly prefer to make something that will be bootable.

Thanks in advance for any help.

---

### Post by thomasaaron on 2008-03-20
You might want to experiment with dd.

dd if=/dev/<hard drive> of=<path to external hard drive> bs=1M

---

