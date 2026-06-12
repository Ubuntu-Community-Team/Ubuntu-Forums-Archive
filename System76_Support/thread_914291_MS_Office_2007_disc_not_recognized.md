---
title: "MS Office 2007 disc not recognized"
date: 2008-09-08
forum: System76 Support
---

### Post by glacialfury on 2008-09-08
Just wondering if anyone else had this problem.  I have a Serval (SERP4), and when I put the MS Office 2007 disc in the drive, it isn't recognized at all; Ubuntu can't mount it or do anything useful with it (that I can see); it's as if there's nothing in the drive.

When I put the disc in a Windows machine, it starts right up like a normal disc.

Anyone else have this, or have access to a disc they can use to test it?  It's a legit copy.

---

### Post by Sef on 2008-09-08
I suspect that has something to do with Microsoft.  It won't boot up unless it gets some signal from the OS.

---

### Post by glacialfury on 2008-09-11
That shouldn't make a difference, I'd think.  Even if another OS couldn't run the disc, it should be able to view the data on it in some form.

---

### Post by thomasaaron on 2008-09-11
> it starts right up like a normal disc.

I'm not sure we have the semantics right here...

Are you saying that when you insert the disk in Ubuntu, you don't even get a file browser? Or are you saying it doesn't auto-start some installation program, like many Window disks will?

If it is the former, then glacialfury is right. You should at least get a file browser.

If it is the latter, Ubuntu will not run the files that autostart Windows installers. And for good reason: You can't install Microsoft Office directly onto Ubuntu.

Please clarify...

---

### Post by chanavs on 2008-09-11
Hi.
   May be the machine on which you have UBUNTU. that drive is not working properly

---

### Post by thomasaaron on 2008-09-11
It's probably not the drive if it will work every time in Windows. However, if this is occurring after a recent upgrade (say, from Feisty to Gutsy, or from Gutsy to Hardy), it could be a bug that we've seen around here.

---

### Post by glacialfury on 2008-09-11
To clarify: the drive works fine on the serval; the machine is fairly new, has undergone little traveling, and all other CDs - whether "Windows", burned, or audio - have worked fine.

The Office 2007 disc is both recognized by Windows *and* autoruns a program on loading; however, I'm not in the habit of autorunning programs, so failure to do so on Ubuntu doesn't bother me.

On Ubuntu, on the serval: when you insert the disc, you neither receive - nor can get - a file browser to look at the data.  The general problem is that the disc is not mounted.  All other discs I've tried simply automount when I insert them.  There is some sort of error in the mounting process when I try to access this disc; if I remember correctly, it was something like "Media not found.", but I'll grab the discs later and get the exact wording.  I cannot browse to the disc in nautilus.

Also, there have been no major upgrades since the purchase of the system.  It came with Hardy Heron installed.

---

### Post by thomasaaron on 2008-09-11
OK, so if *only* that disk doesn't automount in Ubuntu, it's the disk.

Here is a similar situation...
[http://sudan.ubuntuforums.com/showthread.php?t=736582](http://sudan.ubuntuforums.com/showthread.php?t=736582)

---

### Post by glacialfury on 2008-09-11
Well that's the thing.  Presumably, if the disc were damaged, it wouldn't load properly in Windows either.  That post you referred to - the user there had the same disc I have (student edition of Office 2007).  The disc is brand-new.

Can you force-mount a disc in the drive if Ubuntu doesn't want to automount it?  Or can it be assumed that if the automount doesn't work, Ubuntu just won't mount it under any conditions?

---

### Post by thomasaaron on 2008-09-11
I'm not suggesting the disk is bad. I'm thinking more along the lines of what SEF said. It's some sort of MS issue.

---

### Post by Kaloma on 2008-09-11
> **Sef said:**
> I suspect that has something to do with Microsoft.  It won't boot up unless it gets some signal from the OS.

I'm no legal expert, but that smells of anti-trust.

---

### Post by elspic on 2008-09-20
I haven't had a chance to check it myself, but my mom is having the same problem. The disk works just fine in multiple windows pcs, but isn't automounted under ubuntu. When I talk to her again, I'll see if it can be mounted from the command-line. I'm pretty sure mounting my iso of office works just fine as well.

---

### Post by scratman on 2008-09-20
A few things you may wish to consider.

1.  Can you not make an ISO image of the disk, and burn that as an ISO image (still compressed) to a blank DVD.  Then copy the ISO image to your Ubuntu machine, and mount that to install?  

2.  Could you not download a copy using Transmission?  Bittorrent download of Microsoft software is on dodgy legal territory, but as you own a legit copy, you are allowed to take a backup.

---

### Post by glacialfury on 2008-09-22
The iso technique is worth trying.  Since Windows recognizes, I can make the iso on Windows and transfer the file over.

As for downloading, that's a no-go.  As part of the military, I have to keep it strictly legal, and the problem with downloading it via BitTorrent is that I'm simultaneously uploading it - that's how BitTorrent works - so even though I own it, I would technically be sharing it with others.

---

### Post by valrossie on 2008-09-22
When I insert the MS Office Enterprise 2007, OEM version, disc into my DVD drive I get an error message that I need to insert a disc into the drive. I am using a NEC DVD_RW drive - ND 3550A, with the most current firmware updates. I have tried several other DVD's in this drive and without exception they are recognized, DVD movies, DVD backup's, other DVD software installation disks. I took my copy of MS Office Enterprise 2007 to a local PC repair company and when they placed the disc in their DVD drive the DVD disc was recognized as being in the drive tray and the disc was able to be accessed.
------------------------------------------
valrossie
[ opinion leader]("http://www.drivenwide.com")

---

