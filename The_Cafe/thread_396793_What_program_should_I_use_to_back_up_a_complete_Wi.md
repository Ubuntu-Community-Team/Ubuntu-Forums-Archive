---
title: "What program should I use to back up a complete Windows install??"
date: 2007-03-29
forum: The Cafe
---

### Post by billdotson on 2007-03-29
I have heard of Norton Ghost, Device Image, PartImage, and dd_rescue.  I have also heard of people using the Knoppix LiveCD to compress the Windows install is a bz2 file and simply unzip it back to the partition when you want to restore it.  I guess you could do a zip or rar file if you wanted also.

So the question is.. is there a reliable enough way to back up an entire Windows installation (of about 100GB NTFS) for free or is something like Norton Ghost that I have to pay for the only really reliable way to do it?

If the Knoppix way works pretty well I think I would prefer doing it that way.  Speaking of I am going to burn Knoppix back to a CD right now.

I would also like for a way to be reliable enough for business use, meaning it can pretty much never mess up.

---

### Post by cowlip on 2007-03-29
What about "Ghost for Linux", a FOSS Norton Ghost clone?

---

### Post by Compucore on 2007-03-29
I've used Veratas for my back ups onto DAT-3 tapes over here. And it runs fine under windows, linux, and sco-unix over here.

Compucore

---

### Post by frrobert on 2007-03-29
If you want a Windows solution


Create A Bart CD with Drive Image XML

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)  Bart Web site

[http://www.runtime.org/dixml.htm](http://www.runtime.org/dixml.htm)  Drive image web site


Hope it helps

---

### Post by billdotson on 2007-03-30
I want to backup my entire install programs and all.  Also, it needs to be good enough for professional use for a business.

---

### Post by Polygon on 2007-03-30
well, it depends. Do you want to be able to take this backup and install it on different computers with possibly different hardware? or do you just want a backup so if windows goes corrupted style on you, you can just restore the backup?

if you want the latter option, or just have a bunch of the same exact computers with same hardware and everything and want to backup literally the disk partiton, then you should use partimage. Its a linux program that runs in the CLI, but has a GUI (sorta like the breezy installation program) and it worked for me. it just duplicates the partiton onto a backup drive or whatever. So if you want to restore it, just have partimage restore the partiton and all will be good

but if you have different computers that you want to use this backup with, and they are not exactly the same (different hardware for example) then you need a program that backups the files, not the disk image

---

### Post by billdotson on 2007-03-30
I really just want to back it up for restoration on my PC.  I don't want to take it anywhere else.  Although, PartImage MUST be suitable for professional use.. as in will not mess up.  I have heard of Device Image but I don't know how good that is and if it is worth using.  I have downloaded it but I haven't really tried it.  
On the PartImage website it says this about NTFS:

The NTFS (Windows NT File System) is currently not fully supported: this means you will be able to save an NTFS partition if system files are not very fragmented, and if system files are not compressed. In this case, you will be able to save the partition into an image file, and you will be able to restore it after. If there is a problem when saving, an error message will be shown and you won't be able to continue. If you have successfully saved an NTFS NTFS partition, you shouldn't have problems as you restore it (except in the case of bugs). Then the best way is to try to save a partition to know if it is possible. If not, try to defragment it with diskeeper or another tool, and try to saving the partition again. 

Does that mean if I run a defrag that PartImage will successfully save it and be able to restore it?  I have heard of a guy using a Knoppix Live CD, compressing the Windows partition in a bz2 zip and being able to restore it from there.  Also, about system files being compressed.. how would one know that?

Later I will send a word doc with the screen of my fragmentation report so you can see fragmented (or defragmented) it is.

---

