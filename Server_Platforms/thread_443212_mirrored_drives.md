---
title: "mirrored drives"
date: 2007-05-14
forum: Server Platforms
---

### Post by twinax on 2007-05-14
Hello 

I have added two  new 750 Gb drives to a plain  desktop with 40GB IDe drive. The OS will remain on the 40Gb IDe drive but I want to mirror the 2 750 GB drives.  The two new drives are installed,  recognized by the bios.  I have restarted the computer with the two new drives and it boots up ok. Looking for help to mirror the drives and make them available to use. 
Thanks

---

### Post by galeron on 2007-05-14
Hi twinax

I wrote a guide on running software RAID (as opposed to fakeraid or real-raid) over here: [http://nodebox.metaforix.net/articles/running-software-raid-on-ubuntu/](http://nodebox.metaforix.net/articles/running-software-raid-on-ubuntu/)

Some of the options (e.g. SATA drives) may not apply to you, so YMMV.

Let us know how it goes. And I'm especially interested in knowing what you do with your hard disk space, because I have too much space and too little data ;)

Cheers!

---

### Post by twinax on 2007-05-14
Hi Galeron,

Thanks for that .  Looks great!  One question,  what is the command to see if Ubuntu "sees" the drives? I know Bios is seeing it!
Appreciate your help
Regards

---

### Post by wetland on 2007-05-14
The command is 

```
cat /etc/fstab
```

Here is a [link]("http://www.bellevuelinux.org/etc_fstab.html")

---

### Post by twinax on 2007-05-14
> **galeron said:**
> Hi twinax

I wrote a guide on running software RAID (as opposed to fakeraid or real-raid) over here: [http://nodebox.metaforix.net/articles/running-software-raid-on-ubuntu/](http://nodebox.metaforix.net/articles/running-software-raid-on-ubuntu/)

Some of the options (e.g. SATA drives) may not apply to you, so YMMV.

Let us know how it goes. And I'm especially interested in knowing what you do with your hard disk space, because I have too much space and too little data ;)

Cheers!

So Ubuntu recognized both 750 GB Sata drives.  
I was going to prepare drives , but I see from fdisk -l the following:
dev/sdb1  1 66 530113+ 82 Linux Swap
dev /sdb2 67 91054 730861110 83 Linux


Am I correct in assuming that Ubuntu prepared the drive already? If I need to prepare use ":
sudo fdisk /dev/sdb1 ? what about sdb2 ?
Thanks
RS

---

### Post by Weidbrewer on 2008-04-06
No idea if anyone is still monitoring this thread, but I have a question related to this:   I am about to do pretty much the same thing on my rig, and here's my question :

If the HD containing the OS smokes,  can that be replaced and have the two large, mirrored drives remain intact?

---

### Post by Spenzer4Hire on 2008-04-06
Yep.  If you lose the OS drive, you can load Ubuntu onto another hard drive and connect up the mirrored drives, and with a little trickery, reinstate your RAID array.  I don't know any specifics tho.  (It shouldn't be too hard to mount the array while using a Live CD, also.)

---

### Post by Weidbrewer on 2008-04-06
> **Spenzer4Hire said:**
> ...and with a little trickery, reinstate your RAID array...



:lolflag:

...That's a loaded statement if I ever heard one.  But, at least it can be done.


Here's the next question...is it possible to load in one HD and then mirror it at a later point?  (Say, if budget precludes getting both drives from the get go.)  Not 100% needed, but it would make life easier.


(Thanx for the fast reply, BTW Spenz)

---

