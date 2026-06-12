---
title: "no diks drive was detected"
date: 2007-09-16
forum: Sun Sparc Users
---

### Post by ForFree_31 on 2007-09-16
Hello,

I have an Ultra 2 Enterprise for a while now.
When i try to install Ubuntu server and it comes to the screen where the hard drive needs to be detected, it says: "No disk drive was detected"
It seems i can't use any driver out of the list  that works.

Trying to install it on a dual 300MHz, 256MB RAM, 4GB scsi disks, on a serial console.

What should i do ?:confused:

---

### Post by netztier on 2007-09-16
> **ForFree_31 said:**
> What should i do ?:confused:

Hmm.. That's a though one.

Really tough. Oh.. 

I think I got it. Tried "ultra2" and "scsi" as search keywords in "Search this forum" ?

You'll find threads like
[http://ubuntuforums.org/showthread.php?t=203413&highlight=Ultra2+SCSI](http://ubuntuforums.org/showthread.php?t=203413&highlight=Ultra2+SCSI) or
[http://ubuntuforums.org/showthread.php?t=166882&highlight=esp+mkinitramfs](http://ubuntuforums.org/showthread.php?t=166882&highlight=esp+mkinitramfs)

There you go - very probably, you have to manually load the **esp** module so that SCSI works.

best regards

Marc

---

### Post by ForFree_31 on 2007-09-16
Okay thank you.

But what if i only use serial console at this time, at this moment i don't have a keyboard and mouse ?

---

### Post by netztier on 2007-09-17
> **ForFree_31 said:**
> Okay thank you.

But what if i only use serial console at this time, at this moment i don't have a keyboard and mouse ?

Ehm. Now you got me cornered.

How to open a second terminal when connected via serial console...

I'll have to investigate...

best regards

Marc

*Edit: which version of Ubuntu are you using, or do you intend to use? I think 6.06 was lacking the esp module in the initial initrd.img, but 6.10 and later had it built-in.*

---

