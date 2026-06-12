---
title: "Just how secure is plain old XScreenSaver w/PAM?"
date: 2011-04-13
forum: Security
---

### Post by deconstrained on 2011-04-13
Hello all,

I recently installed Xubuntu on a 5+ year-old Acer Aspire laptop. In spite of how the root, swap and home are volumes in an LVM2 group on top of a fully-encrypted harddisk, it's quite swift :D this computer isn't for me, however; it's for my old man. It's been my pet project for the past few weeks, as an exercise in making Linux both highly secure and user-friendly, so that even a technophobe like him could use it without fear of identity theft if it ever gets lost or stolen. I recently shipped it off to him...

The weakest part of security, however, I fear may be the screensaver, which is why I ask. I've searched and searched and cannot manage to find any information on security hardening practices (apart from banal advice such as "always choose a secure password" and "never log in to an X-session as root"). What I want to know is, just how safe is a locked screen?

Also...is it technically possible with the right tools to get a core dump of a running computer and thus extract the block device encryption key from memory? I know that your run-of-the-mill thief will just try hitting the power button and throwing in a livedisk, but hey, you never know.

Edit: found.
[http://en.wikipedia.org/wiki/Cold_boot_attack](http://en.wikipedia.org/wiki/Cold_boot_attack)
I guess I need to tell him how to set the BIOS password to thwart that sort of thing next time I talk to him on the phone...

---

### Post by HermanAB on 2011-04-13
Well, the problem with a locked screen is that your encrypted file system is still unencrypted and keys and data are still in RAM, so the data is not at rest.

However, the military is OK with the use of Xscreensaver and PAM on secret workstations.  So if it is good enough for Dir IMSecur, then it is good enough for me...

---

### Post by deconstrained on 2011-04-13
Thanks. I suppose there's a lot of vested interest in making XScreenSaver secure, since it's such a ubiquitous screen-locking solution on Unix systems, so I guess I'll trust it. 

...But is there a way in to the memory in a running but screenlocked system? Firewall is running, no SSH/FTP daemons, but plenty of little things like an IRDA device (although I haven't configured it to do anything...) the usual USB 2.0, S-Video out, etc.

---

### Post by HermanAB on 2011-04-13
Well, the problem is that the machine is still running, so if any one of the online server programs that you are running has an exploit then the machine can be compromised.  

However, judging by my own experience, it is not likely.  Linux is by default rather secure and active exploits are rare.

---

