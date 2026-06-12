---
title: "Errors on startup without root password"
date: 2005-04-12
forum: Server Platforms
---

### Post by MWAAAHAAA on 2005-04-12
Today, I had unplugged my second hard drive and forgot to comment out the appropriate line in /etc/fstab, so when I booted my system, fsck came up with errors, and the system automatically switched into single user mode. Now without a root password set, it didn't ask for one and boots up into a console with root access. This does not seem to be very secure default behavior of Ubuntu to me.

---

### Post by Papaskunk on 2005-04-12
Well, if someone had to physically take out your drive to get it to happen, you've probably got bigger security problems. If they were able to manually edit the runlevel, then they've already got root access anyway.

Since by default the root account is disabled and no password is set, I find it hard to believe it simply "boots up" into root. You had to have set the root password in order to enable the account. It's just a different security model, with its own strengths and weaknesses. However, I really don't think this is one of them...

---

### Post by MWAAAHAAA on 2005-04-13
[QUOTE=Papaskunk]Well, if someone had to physically take out your drive to get it to happen, you've probably got bigger security problems. [/QUOTE]

That's not my point. Obviously it is possible to have the system boot into a console with full root access, provided there is no root password set. I don't know what else could trigger such an event, I just noted that it is possible in case a hdd is removed. This does not occur when the root password is set, which I tried, since it then asks for a root password.

---

### Post by shakin on 2005-04-13
[QUOTE=MWAAAHAAA]That's not my point. Obviously it is possible to have the system boot into a console with full root access, provided there is no root password set. I don't know what else could trigger such an event, I just noted that it is possible in case a hdd is removed. This does not occur when the root password is set, which I tried, since it then asks for a root password.[/QUOTE]

Booting into single user mode on all Linux distros (and many other Unix-like operating systems) will give you root access without typing a password. It doesn't matter whether you've got a root password set or not. Try it in Red Hat or Suse.

The number one rule of security is that if a hacker gets physical access to the machine he's going to be able to break in. Windows, Linux, Solaris... doesn't matter. At least when single user mode is available it allows the administrator to recover from a lost root password if necessary.

---

### Post by jdong on 2005-04-13
Sure, you can password-protect single user logins, but then you'd want to kill yourself (or we'll die laughing) when you forget your root password.

Even if single-user was protected, using "init=/bin/bash" as a boot argument will still drop you to a root shell.

Even if you password-protected GRUB, anyone who brings in boot media can still read your Linux partitions and write to them.

Bottom line? Physical security can't be replaced by software countermeasures.

---

### Post by dataw0lf on 2005-04-13
If someone has physical access to your machine, it might as well already be broken into.

---

