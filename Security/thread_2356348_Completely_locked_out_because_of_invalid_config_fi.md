---
title: "Completely locked out because of invalid config file (/etc/login.defs) (umask)"
date: 2017-03-22
forum: Security
---

### Post by toniofurbo on 2017-03-22
Hi,

We are quite newbys and managed to completely locking us out of our server.
We added the last line in the file (/etc/login.defs) with "umask 002" which locked us out completely. 
We still have FTP access to the home folder of the user and http access.

Any ideas for a workaround to regain control?

Hardware access is very limited.

Thank you for any hints.

Tonio

---

### Post by TheFu on 2017-03-22
umask 002 shouldn't have any impact to logins.  You did something else.

BTW, the correct use should have been (UPPERCASE)
```
UMASK 002
``` - which makes the user's default group have write to newly created files/directories, by default. Meh.  What you did shouldn't matter. I'm 99% certain that it didn't. Something else happened.

I'm more concerned that plain FTP is allowed - at all.  That protocol should have been killed off in 1994 and definitely shouldn't be allowed on systems managed by "newbys." There are many subtle things necessary to run a FTP in a way that doesn't cause harm.

With physical access, you can hack in and fix whatever the issue is. Getting in is pretty trivial with 3 main different methods used all the time.  This is usually taught in the first few days of a beginning Linux admin class.  You can do it from grub, from a rescue boot disk or from the ubuntu disk you used to install the OS - provided whole-disk encryption wasn't used.  If it was used, then things are slightly more complex, but still possible, provided disk corruption isn't the reason for a locked up system.  

Of course, if you have a backup from the prior night (and you should!), then just preform a recovery. It usually takes a few attempts to get backups doing what you need to restore them in the way you need.  Take this opportunity to test that.  If you don't have backups - that should happen before you screw around with things next time.  

If you setup ssh, then use that to get in and fix things.

And don't feel too bad about locking yourself out.  I'd just installed a 14.04.5 system a few weeks ago for a class I'm teaching, then screwed up a file in /etc/sudoers.d/ which prevented my userid from having any sudo access. Ended up hacking in using a rescue disk and proceeded to lock myself out again, almost immediately. ;)

It can happen to anyone.

---

