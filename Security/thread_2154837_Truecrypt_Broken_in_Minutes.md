---
title: "Truecrypt Broken in Minutes"
date: 2013-06-16
forum: Security
---

### Post by ki4jgt on 2013-06-16
[http://www.prnewswire.com/news-releases/passware-kit-forensic-decrypts-truecrypt-hard-disks-in-minutes-89502507.html](http://www.prnewswire.com/news-releases/passware-kit-forensic-decrypts-truecrypt-hard-disks-in-minutes-89502507.html)

Basically it involves the user leaving the TC drive open and putting the computer on standby. Then you simply plug in a firewire cable and fish around for the encryption key. Does Ubuntu allow this and what's being done about it? It would seem like a security vulnerability in itself if someone could plug a cord into your computer and get anything off of it, nevermind the password to a highly secured virtual hard-drive.

---

### Post by Cheesemill on 2013-06-16
It's always been a good idea to disable firewire unless you actually use it. Because of the way it was designed firewire has direct access to the system memory (unlike usb which has to be processed by the CPU first). I think it's misleading to say that this breaks the TrueCrypt encryption as this method is just retrieving the key from memory instead of attacking the TrueCrypt algorithms.

This isn't a new thing,  there have been Windows exploits that use the same method since 2006...
[http://www.darkreading.com/vulnerability/tool-physically-hacks-windows/211201211](http://www.darkreading.com/vulnerability/tool-physically-hacks-windows/211201211)

This all just highlights the importance of physical security and why you shouldn't let random people plug cables into your machines.

---

### Post by CharlesA on 2013-06-17
Moved to Security.

I think Cheesemill pretty much covered it though.

---

### Post by HermanAB on 2013-06-18
Windows has a very weak security stance by default, but even when a high security profile is applied to it, I still don't trust it much and it doesn't have an App Armor or SE Linux equivalent either.

---

