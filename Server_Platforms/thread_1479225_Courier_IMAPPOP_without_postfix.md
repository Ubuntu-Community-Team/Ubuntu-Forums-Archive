---
title: "Courier IMAP/POP without postfix"
date: 2010-05-10
forum: Server Platforms
---

### Post by LinuxRocks on 2010-05-10
Hello all,

I have installed qmail on my 10.04 server (Because I prefer qmail and dont want to use postfix) and I would like to just install courier IMAP/POP server without the Postfix (Or other mail servers).

Is there an apt-get install switch that will install just what I want to install without deps; or at least a way to block unwanted deps from being installed.

All this without breaking my updates.

Thanks!

Joe

---

### Post by cdenley on 2010-05-10
You don't need postfix, but you do need an MTA. If you installed qmail from the package built with the build-qmail command provided by the qmail-src package, this dependency would be met.

[http://packages.ubuntu.com/lucid/qmail-src](http://packages.ubuntu.com/lucid/qmail-src)

---

### Post by LinuxRocks on 2010-05-10
> **cdenley said:**
> You don't need postfix, but you do need an MTA. If you installed qmail from the package built with the build-qmail command provided by the qmail-src package, this dependency would be met.

[http://packages.ubuntu.com/lucid/qmail-src](http://packages.ubuntu.com/lucid/qmail-src)

Ahh yes. I do see that package in apt-cache.

I will give that a try.

Will I have to remove my existing qmail install? I used LWQ to install it so it should be a standard install.

Thanks!!!

Joe

---

### Post by cdenley on 2010-05-10
> **LinuxRocks said:**
> Ahh yes. I do see that package in apt-cache.

I will give that a try.

Will I have to remove my existing qmail install? I used LWQ to install it so it should be a standard install.

Thanks!!!

Joe

Yes, you should remove your existing install first.

---

