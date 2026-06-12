---
title: "Seeing Ubuntu from XP"
date: 2007-09-14
forum: Windows
---

### Post by burningman on 2007-09-14
Hi, I've recently installed a copy of Ubuntu on one hard disk, and a copy of XP on another, and I was wondering if there's a way if I can see files on my linux drive from XP. I know this isn't the best place in the world to talk about microsoft products, and it's probably been asked before a million times, but I'm really stumped.

I have found one program that allows me to see the linux installation on my linux-installed drive, called the Ext2 Installable File System For Windows. But it won't let me see the remainding information I need. This is where it gets confusing - initially I had tried partitioning that drive, so that XP and Ubuntu sat on the same disc, just divided into partitions. But the original files there can't be detected by my current XP or Ubuntu... confusing yeah, which is why I got a new hard drive and whacked XP on it.

To put it simply, is there a program that will let me copy the information I need from my old drive? 7 gig has gone missing! Thanks anyone who can help.

---

### Post by ajgreeny on 2007-09-14
There are various programs available for windows XP to allow you to either read your linux drive (explore2fs, zip file attached) or read and write, which I've never bothered with and can't even remember the name, but google will find it I'm sure.

To do things in the opposite direction you simply need to mount your windows drive, either with a line in your fstab file:-
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

 or mount it manually with the command:-
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222


Change the dev/hda# if needed to suit your machine.

Or you can install the ntfs drivers needed in your ubuntu to read/write to ntfs from linux.  Search ntfs in synaptic to find what you need.

---

### Post by pelle.k on 2007-09-14
[explore2fs]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs-old.htm")

---

