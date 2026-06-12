---
title: "[SOLVED] HELP! Encrypted system not booting!"
date: 2008-08-16
forum: Security
---

### Post by pofigster on 2008-08-16
So, my desktop has a fully encrypted hard drive (except for /boot) that I set up using passphrases and the alternate CD. It's been working great, but this morning I installed the updates which required a system restart - when I restarted I get:
> [SIZE=2]BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
 Enter 'help' for a list of built-in commands.
 (initramfs) 			 		[/SIZE]
Any idea on what happened and what I can do to fix it?

---

### Post by panhandle on 2008-08-16
See this thread:

[http://ubuntuforums.org/showthread.php?t=440912](http://ubuntuforums.org/showthread.php?t=440912)

---

### Post by pofigster on 2008-08-17
Eh, I have no idea what caused the original problem but booting from the Alternate CD into "Repair" mode and then tarballing the /home partition allowed me to copy to a friend's external HD.  Reinstalling Ubuntu now and plan tomorrow on copying everything back.

Repair mode correctly identified the encryption and prompted for passphrases, which is what let me do what I did.

---

