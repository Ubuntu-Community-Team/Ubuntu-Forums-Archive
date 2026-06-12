---
title: "Secure Erase (wipe) of Files"
date: 2008-08-26
forum: Security
---

### Post by Euphorion on 2008-08-26
Hallo

Having recently migrated from Windows to Ubuntu, I wanted to install a program equivalent to Erase which allows one to securely wipe files using the context menu. I have searched the normal Ubuntu repositories (Applications -> Add/remove). Searching with keywords Erase, Wipe, Nuke etc did not bring any hits.

Does anyone know if there is a Linux equivalent and if so would be so kind as to supply a link.

Thanks in advance

---

### Post by 289Shelby on 2008-08-26
Two that come to mind are 'Shred' and 'SRM'. Shred I believe is installed by default and SRM (SecureReMove) needs to be installed via Synaptic, apt-get or aptitude.

---

### Post by HermanAB on 2008-08-26
This comes up all the time.

The problem is that secure erase of data from a hard disk doesn't actually work.  It doesn't work on Windows either.  However, if it will make you feel better when you run shred, go ahead...

---

### Post by 289Shelby on 2008-08-26
That's true. It's extremely difficult if not impossible to make data non-recoverable if the 'right' people want to get at it.

I've heard that when the Inland Revenue want to dispose of hard drives securely they have them put in a furnace.

---

### Post by Seti on 2008-08-26
> **289Shelby said:**
> That's true. It's extremely difficult if not impossible to make data non-recoverable if the 'right' people want to get at it.

I've heard that when the Inland Revenue want to dispose of hard drives securely they have them put in a furnace.

Even ashes can be re-assembled with the right tools.

/sarcasm

shred will do the job just fine for what you want to do. Let's say for instance you want to shred everything in a directory called foo.```
shred -uvz foo/*
```
Of course, have a peek at the manpage.
good luck.

---

### Post by Euphorion on 2008-09-02
Hallo to all who answered.

Thank you very much for your contributions. For my purposes Shred or SRM will do nicely. I just want to keep the inquisitive user at bay, so that they can't read deleted files containing personal information.

Thanks

---

### Post by Biochem on 2008-09-02
If you look around in the forums (sorry I don't ahave the reference handy) you will find how to recover files that were deleted with shred and srm. The point is that when you overwrite a file you don't actually write over the same sector. This is to prevent a system failure to wreck important data. However it renderes those wiping program useless. There is only two way to achieve what you want.

Shred or srm the whole partition
create a file that will use all the free space and then shred that file (for the less paranoid who consider one pass to be enought just create a file with /dev/random as input and erase it)

The most conveniant way to keep the inquisitive user at bay is to use encryption. You can create a fully encrypted system with the alternate cd.

---

