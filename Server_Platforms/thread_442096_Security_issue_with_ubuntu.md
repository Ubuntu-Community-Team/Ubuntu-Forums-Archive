---
title: "Security issue with ubuntu?"
date: 2007-05-13
forum: Server Platforms
---

### Post by A*p on 2007-05-13
I had an issue with my laptop earlier which made me boot into a recovery console to fix it.  I was placed at the root prompt so I could sort the issues out.

Now I remember when I first tried ubuntu and was surprised that no root password was needed, but it is a simple task to set one up, so I did.  Like most things I have found to be true with Linux, things are easily done, it is the finding out how they are easily done that can be the hurdle.  Which is where new users may have issues, do they know that the root password in not set by default and that they need to set it? do they know what root is?

Now that ubuntu is going to be truly at the frontier of desktop deployment with the Dell deal etc.. is this not a big security issue?   Ubuntu linux boxes all over the world with an easy to access unprotected root account.  With allot of newbies to linux using ubuntu are they being exposed to an unnecessary risk.  There is no mention of setting up a root password during install, or other warning/note about it, an extra step during install would be easy enough.  A simple reboot and selection of the recovery mode in grub could let someone take total control of probably 80%+ ubuntu machines!

---

### Post by rich.bradshaw on 2007-05-13
If you have physical access to a computer, then you are root.

You can password protect grub if you like, but someone can still boot from a CD and be root on your system.

In a nutshell, there is no point worrying about this, as if someone is sitting in front of your PC, they are already in - changing the way this works doesn't change much, in the same way that booting from a Linux live cd can let you change/find out Windows passwords (ophcrack live cd lets you do this).

---

### Post by MrHorus on 2007-05-13
> **A*p said:**
> A simple reboot and selection of the recovery mode in grub could let someone take total control of probably 80%+ ubuntu machines!

This is not a security problem with Ubuntu or Linux in general - this is a misunderstanding of the problem.

if someone has physical access to your machine then having them reboot and gain root access is the least of your problems - it means that someone has compromised any physical security you have and might as well just steal your hard drive, in which case the data is gone.

Physical access controls can be as elaborate as a data centre with biometric access with 100% CCTV coverage or it can be as simple as the locks on your front door but this is nothing I worry about as to put it simply, nobody is going to be rebooting my computers without me seeing them plus the only person with physical access to them besides myself is my girlfriend, and I trust her with sudo anyway :)

---

### Post by A*p on 2007-05-13
Yeah, I understand that, but why make it easy to be able to do so much damage?

---

### Post by A*p on 2007-05-13
It could be potentially disastrous for a company that takes on a Linux trial or changeover to then discover that they were exposed in this way.  I may be over reacting a bit here, but in my job I am left by computers in companies that I could compromise if I so wished, and I know that if said companies moved over to Linux which I wished they would, that they would be no better off and in fact in many cases worse off as I would have full admin privileges.

---

### Post by elst on 2007-05-13
I think that this is definitely a problem for publicly accessible machines (including laptops). I'm fairly sure that the issue has been raised, but it may have been just a mailing list discussion, as the only related thing that I can find is this spec:

[https://blueprints.launchpad.net/ubuntu/+spec/friendly-recovery](https://blueprints.launchpad.net/ubuntu/+spec/friendly-recovery)

The issue with having the system be trivially hackable by default is that it can compromised undetectably. Once you know a laptop is lost you can assume that the OS has been compromised and take steps, whilst a hacked desktop could stay in that state for a long time.

---

