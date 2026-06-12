---
title: "Couldn't somebody h4X0r-up a HD-DVD kernal thing?"
date: 2006-12-30
forum: The Cafe
---

### Post by SoloSalsa on 2006-12-30
This thread will discuss Toshiba's HD-DVD player.  It has been shown to be a Pentium 4 Redhat-based system.  More [here]("http://geekswithblogs.net/lorint/archive/2006/04/21/75795.aspx").

So, the whole system's firmware is on 256 MiB USB mass storage.  They've read the info of Redhat's Ext2 file system.  So, can't someone copy the kernel, then make a kernel module (I think it's called that), and then read the drive?  Unless it's already been done...
They said that they could not read the drive in Windows XP or Vista.  I do not know much about HD-DVD's compatibility (I am a Blu-ray supporter, I know it's supported in Mac OS, Linux, and Windows so far.), but shouldn't it be simple enough to get it for Linux?
Let's discuss it.

---

### Post by 3rdalbum on 2006-12-30
You're assuming that the driver is in the machine's kernel. Usually drivers are stored in the kernel, but Toshiba might have put the meat of the driver as a user-space application, so they wouldn't be obliged to release the source. Or, it could be an extra kernel module that only gets installed after the machine first boots up, so it would exploit a grey area in the GPL and therefore not have to be open-sourced.

Now, I'm not sure what you mean by "coping the kernel and making a kernel module". If Toshiba have released the source code as GPL or another open license, then it's possible. If it's one of the situations I mentioned above, then it may be virtually impossible.

---

### Post by SoloSalsa on 2006-12-30
I do not know much about the kernel.  I *think *what I mean is a module or something...  No, there is obviously no source or license or anything yet.  What I meant, is that the player's whole operating system is readable!  If they can mount the whole Ext2 file system, can't they see all the code?  Then, could it be dissected and altered or used on different machines?
I thought a module is a lump of code in the kernel that offers functionality; like USB mass-storage, or SATA access, etc.

---

