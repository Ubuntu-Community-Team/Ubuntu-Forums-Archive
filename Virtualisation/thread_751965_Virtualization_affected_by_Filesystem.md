---
title: "Virtualization affected by Filesystem ?"
date: 2008-04-11
forum: Virtualisation
---

### Post by laserline on 2008-04-11
Hello All,

Currently using Gutsy  and it has default EXT3 filesystem.
I'm planning clean installation of Hardy and this machine (laptop). It's about to perform desktop tasks and a lot of Virtualization (with Virtualbox).

I want to dump EXT3 as a Filesystem and having a hard time deciding between JFS, XFS and ReiserFS.

I've used all in the past (JFS feels the fastest) but I would like to hear some more thoughts.

Thanks in advance,
Idan.

---

### Post by Gen2ly on 2008-04-11
hmm, just a question, why do you wish to change filesystems?  True XFS and JFS can provide speed increases are sure speed is wanted in filesystem?

---

### Post by laserline on 2008-04-11
First, I want a clean install on all my systems.
For example, I won't be upgrading Tiger to Leopard on my iMac, instead wipe everything and reinstall.

So same on my Ubuntu system. I prefer knowing that this LTS installation is clean.

Second, I need some Windows applications, mostly Powerpoint and MathType documents from school that OOo doesn't open correctly. And my Bank's web site that runs only on IE (and Wine doesn't support typing in Hebrew, so I have to Virtualize that).

Now let's say an Average VM Image takes about 20GB, and I'm sure I'll have more then one (I like to play with many OS's, Darwin, BSD, and other Linux distros). That counts to some very large files, that always change.
At first I thought of storing every VM in it's own Image, but that makes it highly complicated to manage if I ever want to reclaim the disk space.

So the option that makes the most sense is to choose the best Filesystem that will give me the performance I need as a Linux desktop (This is a laptop - will XFS play well, I heard it doesn't like power outages etc...)  and to minimize  the performance hit the system gets from using the VMs and maximize the performance of the VMs 

On my Mac (HFS+ Filesystem) I bought Parallels and VMware Fusion (I was a private beta tester for both) and I can see how the hit happens on I/O reads when using a VM (doesn't matter on which product).

I hope the reason for my questions are more clear now (and I'm sorry for the long post)

Idan.

---

### Post by Gen2ly on 2008-04-11
Hmm, sould like you got a lot of choices to make.  If I were you I'd consider the possibility of a [Logical Volume Manager](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29").  It would require a quite a bit to set it up but once it is set up it will allow an *easier* adjustment of volume sizes.  As for filesystems, I'm not sure choosing XFS or JFS will make a rtremendous difference - i could be wrong.

---

### Post by insane_alien on 2008-04-11
XFS is good for large files, though you may find that if your system suddenly loses power at the wrong time your files will be unrecoverable. JFS is better at holding together on sudden power loss.

---

### Post by laserline on 2008-04-11
> **Dirk.R.Gently said:**
> Hmm, sould like you got a lot of choices to make.  If I were you I'd consider the possibility of a [Logical Volume Manager](http://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29").  It would require a quite a bit to set it up but once it is set up it will allow an *easier* adjustment of volume sizes.  As for filesystems, I'm not sure choosing XFS or JFS will make a rtremendous difference - i could be wrong.

I read the article, but what benefit will I really gain by using LVM ?

Idan.

---

### Post by articpenguin on 2008-04-11
i doubt the filesystem will make a difference for virtualization. if there is a difference we are talking milliseconds in difference.

---

### Post by laserline on 2008-04-11
> **articpenguin said:**
> i doubt the filesystem will make a difference for virtualization. if there is a difference we are talking milliseconds in difference.

I'm not sure I agree with you...
The slowest part on the system is the Hard-drive. When you start a VM, let's say from suspend, mot of what your system will do is read from the disk.
Same when stopping and using the VM.

Maybe on he benchmarks you "gain" a few milliseconds, but the overall responsiveness of the system is affected by all the VM operations.
So I think that choosing the "right" filesystem could improve things.

About LVM - as I have only one disk, I think it's a bit of an overkill...

Idan.

---

### Post by fjgaude on 2008-04-11
I have VMware Server 1.0.5 running on both Gutsy and Hardy beta, both with ext3 filesystem, and I find the speed of the disk just fine, quick. All my data is on a raid5 array, but the VM is NTFS as it is WinXP. I'm happy with this setup.

---

### Post by laserline on 2008-04-12
Did you mean that your Raid setup is EXT3 and the VM's filesystem is NTFS?
How many drives do you have?

---

### Post by fjgaude on 2008-04-12
> **laserline said:**
> Did you mean that your Raid setup is EXT3 and the VM's filesystem is NTFS?
How many drives do you have?

Yes, raid5 is ext3, Windows XP Pro is NTFS... that's the way Windows sets itself up when you install from the CD.

Works great! You have to use Samba to Share folders, both ways, Ubuntu to Win, Win to Ubuntu.

---

### Post by laserline on 2008-04-12
How many hard-drives do you have?

---

### Post by fjgaude on 2008-04-12
> **laserline said:**
> How many hard-drives do you have?

My raid5 array has four 300G drives... the rest of the system has two more drives for the OS and for that all important backup of data that is on the raid array.

I usually keep at least three partitions on one drive, a Raptor and a Seagate for versions of Ubuntu. Like two for a beta so I can move from one to the other after an update has broken one. And one for Gutsy. On the portable box I have at least three partitions for backup and OSs.

I usually only have one partition on the laptop, and that is for Gutsy, installed at least a month after it was released.

I use Unison to keep the laptop in sync with data on the raid5; grsync to handle the backup to other drives on the main box and to the portable.

So, I've been at this data stuff since the late '70s, and don't like to lose data. <smile>

---

