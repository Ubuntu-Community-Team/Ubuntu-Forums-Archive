---
title: "Hard Drive Dead?"
date: 2009-03-26
forum: System76 Support
---

### Post by Beridel on 2009-03-26
Hi everyone,

It seems that my hard drive on my GAZV5 is dead or dying.  I have a dual boot of Vista/Ubuntu set up with GRUB as my boot loader (set up on 3 partitions, 3rd being the SWAP) and I can currently cannot boot into either partition.  Both OSes go into the loading screen before the login screen, chug away for a while and then eventually freeze up.  Ubuntu gives a little bit more info and tells me that some blocks on partition can't be read/aren't correct or something like that. Recovery console/Safe Mode does not work as well.

I wanted to do a NTFS chkdsk with my XP CD recovery console, but the install does not see any hard drives available.  
I also tried using fsck on my linux system rescue cd ([http://www.sysresccd.org/](http://www.sysresccd.org/)) I have, but I couldn't get that to work either.  fsck /dev/sda1 (my main parition where windows is) said that the drive was not clean, so I tried again with fsck /dev/sda1 -r and it just echoed the version of fsck without doing anything.  -a and -y did echoed the version number of fsck as well.
I then tried my 8.10 Ubuntu Live CD with fsck and Ubuntu wasn't even able to return a proper fdisk -l, and all fsck commands said they couldn't find the desired drive.  It was as if my computer had no disk drives, similar to what happened when trying to use the XP recovery console.

So what am I to do now to try and recover my hard drive?  Or am I just out of luck?  Thanks in advance for your replies and help.

---

### Post by lindsay7 on 2009-03-27
Can you find out what brand the hard drive is. A number of the manufactures have software that you can download from their sites that will let you test the drive. I did this witha Western Digital drive that was acting up. When I went to their site to look into warranty the software was listed and they requested that it be run before they would give me an rma to return it. I have seen the same thing for other manufactures.

---

### Post by betrunkenaffe on 2009-03-27
My father likes this program.

[http://www.grc.com/sr/spinrite.htm](http://www.grc.com/sr/spinrite.htm)

---

### Post by thomasaaron on 2009-03-27
It definitely could be your hard drive going belly up. Try re-seating your drive first. Sometimes that does wonders.

If you can't access your hard drive, though, from a live CD, I'm not sure how you will recover your data without sending it in to some expensive data recover outfit.

---

### Post by Beridel on 2009-03-27
So I got the diagnostic tool from Seagate (which is the brand of the drive in my GAZV5) and it passed the "long test" available on the bootable DOS cd they have.  So now I'm all out of ideas.  So far out of all of these tests, it either does not recognize the drive, tries to fix/scan the drive says it can't, and now it finds the drive, scans it for an hour, and then says everything is okay.

I think at this point Thomas, if its possible, I just need a new hard drive.  Unless some other people have any other useful insight?

---

### Post by thomasaaron on 2009-03-27
> Ubuntu gives a little bit more info and tells me that some blocks on partition can't be read/aren't correct or something like that.

It sounds like it may be an irreparably hosed filesystem. I've seen stuff like that happen if the machine takes a bump while the hard drive is writing. If that is the case, you're gonna have to re-image it -- just like you will with a new hard drive.

Here's what I suggest:

First, fill out this form, so I can get started on getting you a new drive...
[http://system76.com/article_info.php?articles_id=39](http://system76.com/article_info.php?articles_id=39)

In the meantime, (since I probably won't have the RMA authorization back before Monday), you can go ahead and try re-imaging to see if it fixes the problem.

---

### Post by mal_conductor on 2009-03-29
Try testdisk and/or photorec.

These are my notes:
[http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=5b659bde0dba72b97f7ec40ada4772a6e04e75f6e8ebb871)

---

