---
title: "can i use ubuntu to &quot;clean&quot; a windows virus?"
date: 2009-12-17
forum: Security
---

### Post by ggezpz on 2009-12-17
Hi,

Okay, first off, I've already searched for this situation in the forums, and read through many of the posts that say it is EXTREMELY unlikely for a windows virus to have any effect in linux. But, here's my really convoluted situation:

I have an external HD that appears to be infected with a windows virus. I plugged it into a freshly formatted XP, and boom, up goes the system. I also have critical data on this HD so I can't just format everything and wipe it out. So, here is my plan - please tell me if this will work!

1) Reformat the windows partition and reinstall XP. 
2) Use Unetbootin to install a dual boot Ubuntu.
3) Copy files from the external HD to the Ubuntu partition. Not copying the entire hard drive, because this would just copy whatever files are associated with the virus, correct?
4) Format the HD
5) Copy the files back from Ubuntu to the external HD
6) Copy the files back from the HD to Windows XP partition.

Will this long convoluted path work for essentially "cleaning" the external HD of the virus? Thanks in advance!

---

### Post by EricDrijv on 2009-12-17
Yeah that will work, but don't copy the exe-files onto the new drive.

Or maybe you can make a live cd with a scanner on it and then solve the problem?
[http://www.raymond.cc/blog/archives/2008/11/15/free-drweb-livecd-to-scan-and-remove-virus-without-starting-windows/](http://www.raymond.cc/blog/archives/2008/11/15/free-drweb-livecd-to-scan-and-remove-virus-without-starting-windows/)

---

### Post by Some Penguin on 2009-12-18
Seems like it'd be much easier and more direct to simply disable autorun on external devices, plug in the external drive, and run something decent like Kasperksy or Malwarebytes to clean the drive.  Unless you actually try to *run* a program, it's just data, no matter how malevolent, and if you have something that auto-runs even when the auto-run is disabled, you have problems before you ever plugged in the drive.

See [http://support.microsoft.com/kb/967715](http://support.microsoft.com/kb/967715) for how.

---

### Post by mikewhatever on 2009-12-18
> **Some Penguin said:**
> Seems like it'd be much easier and more direct to simply disable autorun on external devices, plug in the external drive, and run something decent like Kasperksy or Malwarebytes to clean the drive.  Unless you actually try to *run* a program, it's just data, no matter how malevolent, and if you have something that auto-runs even when the auto-run is disabled, you have problems before you ever plugged in the drive.

See [http://support.microsoft.com/kb/967715](http://support.microsoft.com/kb/967715) for how.

+1. Ubuntu isn't a virus cleaning tool.

---

### Post by ggezpz on 2009-12-18
> **Some Penguin said:**
> Seems like it'd be much easier and more direct to simply disable autorun on external devices, plug in the external drive, and run something decent like Kasperksy or Malwarebytes to clean the drive.  Unless you actually try to *run* a program, it's just data, no matter how malevolent, and if you have something that auto-runs even when the auto-run is disabled, you have problems before you ever plugged in the drive.

See [http://support.microsoft.com/kb/967715](http://support.microsoft.com/kb/967715) for how.

So I ran Malwarebytes on the drive, but it came up empty. I ended up reinstalling XP and using an Ubuntu Live session to transfer over the important data. 

While I was browsing the hard drive, I found a folder called "BOOTEX" with a "thumbcache_131.exe" application in it, and also an autorun.inf file that linked to this exe. Not that this is relevant anymore to this particular forum, but would I be correct in assuming that this was the problem? Thanks for the replies everyone!

---

### Post by soldier4jesus on 2009-12-18
I don't know if this helps or not, but I found this tutorial on You Tube that tells you how to try to clean a virus off of a windows partition using Ubuntu.  Here's the link to the video:

[http://www.youtube.com/watch?v=9h3q5ss40oY&feature=PlayList&p=8AB8BFF28E616EF0&playnext=1&playnext_from=PL&index=58](http://www.youtube.com/watch?v=9h3q5ss40oY&feature=PlayList&p=8AB8BFF28E616EF0&playnext=1&playnext_from=PL&index=58)

God Bless!!
Wesley

---

### Post by Some Penguin on 2009-12-18
Searching for that particular filename brought me to

[http://forum.avast.com/index.php?topic=51761.0](http://forum.avast.com/index.php?topic=51761.0)

Looks pretty nasty.

---

