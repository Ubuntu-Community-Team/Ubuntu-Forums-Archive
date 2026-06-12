---
title: "Folders Getting Deleted"
date: 2010-09-18
forum: Security
---

### Post by Vinnare on 2010-09-18
Hello,

I'm having a problem. The folders are getting deleted by themselves. I don't understand why!!! :(
Please help.
I've lost some important data. Anyone has any idea why is it happening?

vinnare

---

### Post by Rubi1200 on 2010-09-18
What folders?

What version of Ubuntu are you using?

Are you the only user on the system?

Have you recently made any major changes to your settings?

Have you changed any file or folder permissions recently?

What does the output of ```
ls -l
``` show?

We need more information please.

---

### Post by Vinnare on 2010-09-21
1. Folders being written to Windows drive are getting deleted, i.e. in the NTFS drive

2.I'm using 10.04

3.Yep, I'm the only user

4.No, I've not made any changes personally. Changes are made automatically through Updates that OS takes

5.No, I don't remember having done that!

6. The output is:
> 1.nb
a.out
Desktop
Documents
Downloads
examples.desktop
homework.f90
homework.f90~
homework_q1_imp.f90
homework_q1_imp.f90~
homework_q2c.f90
homework_q2c.f90~
homework_q2.f90
homework_q2.f90~
Music
output
Pictures
Public
Templates
Untitled-2.pdf
Untitleddocument_bck.doc
Videos
vimbook-OPL.pdf


I hope that is would be useful to detect my problem. I'm avoiding Ubuntu since then, but I need it for my coding assignments, and such things are alarming!!!

---

### Post by Rubi1200 on 2010-09-21
How are you transferring the folders from Ubuntu to Windows?

This is just a wild guess, but have you enabled the option to view hidden files and folders in Windows?

---

### Post by Vinnare on 2010-09-21
The deleted folders were directly created in the windows partition through Ubuntu, like by mounting the drive and creating a folder in there, wherein I put desired files. The folder got deleted along with the files. I can access it neither from Ubuntu nor from Windows, and yes I've tried the 'show hidden' option too, without finding anything :(
It also happened so, that I had one file lying in my trash (in Ubuntu) that I had deleted from that folder which got deleted! When I tried restoring it, a message appeared telling that the location didn't exist (I had the concerned drive already mounted, so that possibility is ruled out).

Do you have ne idea what could be the cause! After this i have bought an external hard-disk to backup data, but I'm not till sure whether I should trust Ubuntu writing into it, coz even that drive is NTFS. What do you suggest?

---

### Post by Rubi1200 on 2010-09-21
I am out of ideas on this one; maybe a corrupted file-system or incorrect permissions?

I really don't know, but I hope someone else will come along with some other possibilities.

---

### Post by cariboo on 2010-09-21
Try testdisk and photorec to see if you can retrieve your files, the testdisk package is in the repostories. Why not just sve the documents and directories in your Ubuntu home directory?

---

### Post by Vinnare on 2010-09-22
> Try testdisk and photorec to see if you can retrieve your files, the testdisk package is in the repostories. Why not just sve the documents and directories in your Ubuntu home directory?

I have installed testdisk, but I am not able to understand how to use it to retrieve files! It showed options to retrieve lost partitions, not files.

I don't save files to Ubuntu home directory because I need them through Windows too, I'm new to Ubuntu and still require Windows for a number of applications. I use Ubuntu mainly for coding purposes. (I hope you don't mind me using Windows :wink: )

---

### Post by DonaldJ on 2010-09-22
It sounds like the trouble one has in copying a SeaMonkey document, then clicking SeaMonkey off, and being unable to paste the save into a blank word file..  Probably somewhere somehow your saves aren't being saved after the host program is shut down..  Pick Windows, or Ubuntu, and dump one...

Run a complete Clam Scan..  and a complete Node-32 scan...

---

### Post by Rubi1200 on 2010-09-22
I believe that Photorec can recover files. 

See here for more options:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

You may want to look at the Ntfsprogs software in particular.

---

### Post by Vinnare on 2010-09-24
Photorec Worked!!!:guitar:

I couldn't retrieve all the files but I got many of them! Maybe others got overwritten in all these days.

Thanks Rubi1200, cariboo907. But can't still understand why this happened! Please get back to me in case you understand why this happened. Meanwhile, I'm not risking writing in NTFS via Ubuntu again unless I make a reinstall.

---

### Post by Rubi1200 on 2010-09-24
Hi,
I am glad you managed to recover at least some of the files.

As I said before, maybe something got corrupted on the file-system that you were not aware of, thus causing files saved from one file-system type to become corrupted/deleted on the other one.

You may want to consider something like this:

A partition for Ubuntu: Ext4

A partition for Windows: NTFS

A partition for sharing files: FAT32

As far as I know, there should be no issues with Windows and Ubuntu sharing data via a FAT32 file-system as it is recognized by both.

---

