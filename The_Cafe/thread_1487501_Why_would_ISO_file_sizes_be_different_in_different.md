---
title: "Why would ISO file sizes be different in different OS'?"
date: 2010-05-19
forum: The Cafe
---

### Post by GarmaZed on 2010-05-19
I'm burning copies of 10.04 to hand out to friends that are interested and also to others at work.  I originally downloaded the ISO on my Windows 7 computer, and it was never able to burn the image to a standard CD-R (700MB).  I was only finally able to burn it to a larger DVD-R, and finally install with that.  It turns out the file actually was around ~716MB.

Later on, I torrented the file on the Ubuntu installation and it actually saves it to something like 699MB, and I'm able to burn it to CD without any issues.  Does anybody have any idea on why it's smaller on Ubuntu, and therefore able to burn to CD?  Just curious, but I'm happy I could spare CDs instead of DVDs to share the freedom.

PS - 3 CDs handed out today, with 2 more interested already.  We work in a tech support call center and none of us were really trained with troubleshooting issues on Linux systems.  So I'm trying to work on that, at least for our service.  With a group of about 400 workforce, 6-7 is a pretty good start for the first day.  :)

---

### Post by Diluted on 2010-05-19
Have you checked to see if the hashes are the same as the one [here](https://help.ubuntu.com/community/UbuntuHashes)?

---

### Post by GarmaZed on 2010-05-19
> **Diluted said:**
> Have you checked to see if the hashes are the same as the one [here]("https://help.ubuntu.com/community/UbuntuHashes")?


I just checked on the Windows machine using winMd5Sum, and on the Ubuntu machine using the terminal command, and they both match up on the site.

It's the 10.04 32-bit desktop, so:
d044a2a0c8103fc3e5b7e18b0f7de1c8

---

### Post by ronnielsen1 on 2010-05-19
I've ran across that issue myself.

---

### Post by parn on 2010-05-19
In the property windows in both ubuntu and windows 7 - do they have the same bytes?

Example, I have 2 identical files, in windows it is 1.7MB and ubuntu 1.8MB - that is because I adjusted the file system's cluster size when I format the HDD.

---

### Post by 3rdalbum on 2010-05-19
Windows measures files by "fake" megabytes, where a megabyte equals 1000 kibibytes.

Ubuntu measures files by mebibytes, where a mebibyte equals 1024 kibibytes. It's the computer-correct way of counting storage space. The Ubuntu ISOs are carefully restricted to 700 mebibytes (MiB) because that's the correct capacity of a CD-R.

Some Windows-based burning software is dumb and measures using the fake megabytes (MB), and has the assumption that a CD-R holds 700 MB rather than 700 MiB. So the ISO is 716 MB and the burning software thinks that it's too big for a CD.

---

### Post by CharlesA on 2010-05-19
Try a different burning software.

I show ubuntu-10.04-desktop-i386.iso as being 716,230KB (or 699MB) on both Win7 and XP. Ubuntu shows it as an even 700MB.

@3rdalbum: Which version of Windows measures Megabytes that way?

---

### Post by saulgoode on 2010-05-19
> **GarmaZed said:**
> I'm burning copies of 10.04 to hand out to friends that are interested and also to others at work.  I originally downloaded the ISO on my Windows 7 computer, and it was never able to burn the image to a standard CD-R (700MB).  I was only finally able to burn it to a larger DVD-R, and finally install with that.  It turns out the file actually was around ~716MB.

The "problem" is that your Windows software is writing the CD using Multisession. This requires that "bookkeeping" information for a second session gets written at end of the first session (so that when the second session is added later, the reader will know how to find it). When using Multisession you lose about 15Mb for each session on the CD.

If you do not expect to ever go back and add files to your CD -- as in the case of burning Ubuntu ISOs -- then there is no need to use Multisession and you can fit about 15Mb more of actual data on the CD.

---

### Post by GarmaZed on 2010-05-19
> **saulgoode said:**
> The "problem" is that your Windows software is writing the CD using Multisession. This requires that "bookkeeping" information for a second session gets written at end of the first session (so that when the second session is added later, the reader will know how to find it). When using Multisession you lose about 15Mb for each session on the CD.

If you do not expect to ever go back and add files to your CD -- as in the case of burning Ubuntu ISOs -- then there is no need to use Multisession and you can fit about 15Mb more of actual data on the CD.

Huh, I guess it could be this.  I just checked the properties of both files on the machines and the reported file size in the properties windows are the same... but in Windows Explorer, the file being recognized as an ISO for some reason shows it as 714MB.  Once it associates the file with the disc imaging program (which is part of Windows, not third-party), that's when it shows as +716 MB.

Well, thanks for the help.  I'll mark this solved and request for the thread to be closed, ty.

---

### Post by philinux on 2010-05-19
Probably why aysiu links to infrarecorder.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

