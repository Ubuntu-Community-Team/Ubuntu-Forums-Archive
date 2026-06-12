---
title: "cannot get to grub menu after full disk encryption"
date: 2010-01-13
forum: Security
---

### Post by DouglasAWh on 2010-01-13
this isn't really a security question, per se, so feel free to move.  It is related to full disk LVM encryption though.  Full disk didn't work for me with grub2 after running dd to a remote server, so I downgraded to grub1. No biggie.  However, I have neither grub or grub2 as selected in Synaptic.

Let's say I forget which I have installed.  How would I determine what version of grub is installed at the moment.  I'm assuming it's somehow installed on in the mbr but not on the OS.  I didn't mean to do anything funky.  Is that the normal setup?  I'm deploying these systems to users and want to be able to troubleshoot issues in the future (hopefully that will not be needed!)  grub --version does not work because it is not installed.

NOTE: I do not have any "problems", I just want to be able to tell a version number in case of problems later.

---

### Post by adam814 on 2010-01-13
I do have GRUB2 installed and the grub --version command doesn't work for me.  Doesn't the actual GRUB menu show the version of GRUB running?  I know it does for me.

---

### Post by DouglasAWh on 2010-01-14
> **adam814 said:**
> I do have GRUB2 installed and the grub --version command doesn't work for me.  Doesn't the actual GRUB menu show the version of GRUB running?  I know it does for me.

No. I meant to mention that.  When you use LVM full disk encryption you don't get a grub menu.  It just boots the encryption screen.  ATM, I don't need to change kernels and there are zero plans to dual boot, but that would be a good thing to know how to do also.

Actually, in an attempt to get this working, I pressed random buttons and still got no menu but somehow made it unbootable.  No biggie, since it's a test box.  I see the no grub menu in Jaunty, Karmic and Lucid.

---

