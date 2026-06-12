---
title: "GPG encryption in Thunar?"
date: 2007-10-16
forum: Server Platforms
---

### Post by DapperMe17 on 2007-10-16
I have GnuPG installed & would like to add a "custom command" in Thunar to ENCRYPT & DECRYPT (Right click menus!) a file.

What are those two commands? (I'd like a prompt for the password as well)

Thanks

---

### Post by /etc/init.d/ on 2007-10-17
Seahorse will do this, it's also a graphical frontend to other areas of GPG too (signing, key creation/management, etc).  It's in the repos.

---

### Post by WorldTripping on 2007-10-17
This works in Nautilus, don't know about Thunar.

[http://ubuntuforums.org/showthread.php?t=108513&highlight=seahorse]("http://ubuntuforums.org/showthread.php?t=108513&highlight=seahorse")

---

### Post by DapperMe17 on 2007-10-17
Thanks for the info...I'll try it.


I do have Seahorse, as a front-end. Would I enable "right click" in Seahorse's preferences, or would I still have to create a custom command in Thunar? If so, what would those commands be?


Thanks again!

---

### Post by DapperMe17 on 2007-10-21
Anyone care to take a look?

---

### Post by WorldTripping on 2007-10-22
If I remember rightly, Seahorse does have a context-sensitive right mouse button.

But it's been a while since I used it.

Sorry to not be more help.

---

### Post by motorsaege on 2007-12-11
Hello all together,

This ones should work:

Encryption:
xfce4-terminal -x gpg -ea %f

Decrypt/Verify:
xfce4-terminal -H -x gpg -v %f

command -H makes the Terminal window not shutting down after verifying the signature.

Sing (detached sign; replace gpg command 'b' by 's' if preferd):
xfce4-terminal -x gpg -ba %f

Shred (if you wanna copy the gpg4win functions :-) )
xfce4-terminal -x shred -u %f

Best regards from Bavaria
motorsaege

(found in: [forum.ubuntuusers.de](http://forum.ubuntuusers.de/topic/137406/?p=1104643#1104643))

---

