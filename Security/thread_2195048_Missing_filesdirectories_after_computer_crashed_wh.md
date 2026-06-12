---
title: "Missing files/directories after computer crashed while running Cryptkeeper"
date: 2013-12-22
forum: Security
---

### Post by phathom on 2013-12-22
I am running Linux Mint 16. I am running cryptkeeper and have been for a while now. I keep all of my important documents encrypted with it so files cannot be viewed or more importantly accidentally deleted by someone since this is a shared computer (read, kids).

Just to give you an idea of what we're dealing with. I have a lot of text, excel, and pdf files saved in there under different directories by name, then by dates, etc. taxes, medical bills, bank statements, insurance policies, blahblahblah then like 2010, 2011, 2012, each of those having month files 01,02,03, etc.
Basically I'm kinda OCD about it and there are a LOT of directories.

I had it open and was organizing my files and decided to rename one of the parent directories. It came up with it's please wait window like it's working. Normally this doesn't pop up, or pops up for a few seconds if it does. Well it came up for several minutes. I just kinda let it do it's thing, eventually it stopped doing anything and froze. I tabbed to Firefox and did some surfing, letting it continue, hoping it would clear up. When I tabbed back it was still frozen, or more specifically blank.
I tried clicking on the window to see if selecting it would help somehow. It did not, but what it did do was lock the system up completely. Nothing would respond, my cursor disappeared, trying to put in any commands on the keyboard failed, the whole system was non responsive. I decided I would let it sit and do it's thing for another 10-15 minutes, to see if it would clear up and finish whatever it was trying to do.
It did not, in fact when I came back to check on it, the entire screen was black and there was nothing I could do to change that. 

I tried holding the power down to do a hard power off and then start again, even this was not working. I actually had to turn off the computer at the power supply. 

When I started it up, the first thing I did was load the encrypted folder to check on my files. Surely enough I had problems. 

The directory I had renamed, had not been renamed, it was still the old directory name.
Several sub directories of the parent directory I had tried to rename were missing as well as the files in them.
There was no record of the new directory name.
There was no trace of any of the directories or files anywhere that had been in the parent directory that got renamed.

I pulled the properties on the entire ENCFS partition and got the file count and size. I also pulled the properties from the directory that the ENCFs partition lives in and there is a huge difference between file size and file count. Basically the difference is what I estimate is about the right number of files I'm missing.

I figured there might be a problem with the file table or something, since this is a NTFS partition it is on, because it's a dual boot system, I booted to windows and ran chkdsk /r. It fixed the file system errors it found, I restarted back to linux, loaded Cryptkeeper, but still found no change.

Basically from what I'm seeing, the raw data is there somewhere, but it is not being displayed. Is there any way to remedy this.

Also yes, I do have a backup, but it is not recent. I backup everything here once a quarter and was doing mine for the end of the last fiscal quarter today, but was renaming the files first.

Any help would be greatly appreciated, thank you all in advance.

---

### Post by Irihapeti on 2013-12-22
What version of Ubuntu are you using? And what version of encFS?

---

### Post by phathom on 2013-12-23
-Linux Mint 16 Cinnamon 64-bit version 2.0.14, which is built off of Saucy. 
-Kernel 3.11.0-12-generic.
-Cryptkeeper 0.9.5
-encFS 1.7.4-2.4build2

---

### Post by Irihapeti on 2013-12-23
Thanks for the information. I asked because I came across a bug in encFS: [http://code.google.com/p/encfs/issues/detail?id=61](http://code.google.com/p/encfs/issues/detail?id=61). It refers to an earlier version, but it's possible that it might still apply.

Not what you want to hear, I'm sure. :(

I'm thinking you might be better off posting on the encFS Google site or posting a bug on Launchpad. It's just possible that the developers might be able to help you (though I'm not counting on that).

---

### Post by cariboo on 2013-12-23
I'd suggest running fsck, as it may just be a bit of a corruption issue after the crash.

---

### Post by Irihapeti on 2013-12-23
> **cariboo907 said:**
> I'd suggest running fsck, as it may just be a bit of a corruption issue after the crash.

Good point!

(now, why didn't I think of that???)

---

### Post by phathom on 2013-12-23
That bug you posted is exactly what happened down to the T. 
I'll take it that it was reported and never resolved?
Also I tried to run fsck, but it wouldn't do ntfs.
I downloaded ntfs-progs and ran it, for some reason it still couldn't read it, that's when I did a chkdsk /r from windows side. It didn't help...

---

### Post by Irihapeti on 2013-12-24
> **phathom said:**
> That bug you posted is exactly what happened down to the T. 
I'll take it that it was reported and never resolved?

Unfortunately, I think you might be right. :(

---

### Post by cariboo on 2013-12-24
I really don't think that bug applies in your situation, as you are using an unsupported file system. Due to the fact that NTFS access needs an extra layer of software in order to be useful, things are quite a bit more complicated.

Several releases ago, it was recommended that we run CHKDSK at least twice, after using gparted to resize a Windows partition, I'd suggest you run it several times on your problem partition. If that doesn't work, it may be time to check some of the Windows forums to see if any one else has run into similar probelms.

---

### Post by phathom on 2013-12-24
I also installed encFS on the windows side and I couldn't pull up the information on that either.
Since the bug reported fit my problem almost exactly, the only difference being NTFS vs EXT4 and being local, not cloud storage, I'm going to assume that it is what happened.
At this point I have moved all my existing data that wasn't lost (btw: found some corrupted files in the ones that remained as well) onto a newly created encFS partition. I then deleted all the encFS info and am working on replacing all those files.
The majority of them are online statements that should still be in my e-mail. 
There is still like 3 months worth of files I will have to update and rewrite, but at least it's not everything. I was hoping for a magic, "Run this, it will fix it" but it looks like I'm back to the old school, restore from backups and suck up whatever wasn't.

Bottom line: BACKUP!

---

