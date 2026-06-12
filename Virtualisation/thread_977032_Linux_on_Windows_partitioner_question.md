---
title: "Linux on Windows partitioner question"
date: 2008-11-09
forum: Virtualisation
---

### Post by BowG on 2008-11-09
Hi all,

I use Windows (vista, but that doesn't matter) and I want to install Linux (Ubuntu) via VMWare. I've installed VMware and I have dowloaded a 'live-session' cd (iso-file) of Ubuntu. I've configured all that stuff (already a month ago) and I am able to run a 'live session' of Linux on VMWare. (When I start up the .vmx-file he starts VMware and he asks me to install Ubuntu or run a live-session to give it a try. I always did the latter, but that way, if I exit VMware, I also lose my data and all the configurations i've made in Linux. (Unless I set in my VMWare options to 'suspend my virtual machine', then he 'hibernates', but I can't let him hibernate forever, e.g. after a crash I lost everything...)

So I want to install it, there is a wizard for that. After asking me some things about language and stuff, he starts the 'partitioner'. 

Now here is *where I am in trouble*. He asks me:

[I]PREPARE DISK SPACE
How do you want to partition the disk?
-> Guided - use entire disk **(what disk is this in windows, is this my C-drive?) **
     SCSIl (0,0,0) (sda) - 107,4 GB ATA VMWare Virtual I
-> Manual[/I]

My problem is, I just want to reserve (to install and run Linux) a couple of GB (e.g. 4GB) and not my entire disk, a have only 8 GB left on my C-drive. I am afraid to lose data from my C-drive, but during the installation I cannot see (or the installer cannot see) the data (I am aware that Linux has a different file-system (or however you call it)), so I don't know if the installer knows where he can write on my drive (will he warn me if there is not enough space...?)

When I check the 'Manual' partitioning - I think this is what I should do in my case - and press next, i get the following (i made a screenshot on) 
[http://img91.imageshack.us/my.php?image=ubuntuinstallga1.jpg]("http://img91.imageshack.us/my.php?image=ubuntuinstallga1.jpg")

Now here I don't know at all what to do, but I am afraid to try things out, I don't want to mess stuff up (lose files or something). And if I make a partition, does it mean that I have really (seen in Windows) an extra drive (not physiccaly of course), or is it just a file of (in my case) 4 GB that is made on my hard disk (that is what seems the best and what I hope for).

And more in general, is it possible to mess up things (on my hard drive or other stuff) when I work in VMWare? (During installation of Ubuntu or at other moments).

I hope you guys could help me out, I suppose these questions have easy answers for you. I would thank you forever :)

Grtz from BowG

---

### Post by BowG on 2008-11-10
Come on guys, this can't be that difficult. I will shorten my question:
[I]
Is it possible that you destroy/remove/overwrite files that you can see when you work in Windows, while working (in my case installing and partitioning) in Linux in VMWare?[/I]

If you don't want to read all the above, just answer me this one question plz

THX

---

### Post by Shazaam on 2008-11-11
This seems to be your setup...
```
Host=Vista (physically installed onto hard drive)
Guest= you are trying to install Ubuntu/linux via VMware
```
When you make a virtual machine basically what you are doing is creating files, not actually carving up your physical drive(s). You won't see another drive letter in Vista. So it's ok to partition/format the virtual machine using a linux livecd.
Start Vista then start VMware. Pop in the Ubuntu livecd and boot it using VMware so you have a running VMware/Ubuntu live session on top of Vista. Open gparted (System>Administration>Partition Editor), In the unformatted space choose "New", gparted will tell you that you need to make a "disklabel". Keep it default (msdos) and then hit Apply. Close gparted and then run the install. When you get to the partitioning stage choose "Guided-use entire disk".
I have ran a virtual machine that had two 100gig virtual hard drives with 8 different operating systems installed on it and it was only 3.2 gigs in total size running on top of Windows XP. If you make a virtual machine with a virtual hard drive size of 50gigs or less you will be fine.

---

### Post by BowG on 2008-11-11
Thanks, it worked  :)

---

