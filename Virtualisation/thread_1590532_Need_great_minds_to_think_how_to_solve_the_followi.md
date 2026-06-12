---
title: "Need great minds to think how to solve the following...."
date: 2010-10-08
forum: Virtualisation
---

### Post by drhiii on 2010-10-08
I have the Complete Human Anatomy Primal 3D Interactive Series 9CDs that runs on Windows.  To run it, one inserts the CD into the drive and the program runs self contained.  So when one wants to look at a body part, one inserts the corresponding CD.   All of which is fine except it is cumbersome, and it runs on Windows and I can't post a list long enough about everything I detest about Windows except to say at the top is having to reinstall it whenever something blinks.

Anyway.... the program runs under Wine.  And it will run under Virtualbox or similar virtual machines.

What I want to do is see if I can create 9 .iso's, and run it off an external flash drive for means of portability and also having a stable OS.  

Creating a boot flash drive, easy.  But am trying to learn how to do the rest.  Should I create a Virtualbox environment, then learn how to 'mount' .iso's under that which is essentially a Windows environment but still portable.  Or........ can anyone thing of another way to skin this cat?  It may be possible to run each .iso under Wine.  I have not tried that yet, but wanted to ask this saged group your opinions while I dig deeper.

Tx for any ideas....

---

### Post by HermanAB on 2010-10-08
Yes, you can do all of the above.

To copy a CD to a file:
$ cat /media/cdrom /wherever/whatever.iso

To use an ISO file under VMware Player is done with a couple clicks of a mouse in the settings tab of the VM.

---

### Post by scrooge_74 on 2010-10-09
As HermanAB said, copy the disks as iso and then tell Virtualbox where those .iso are that way is just a click on the top bar to mount one of those disks

---

