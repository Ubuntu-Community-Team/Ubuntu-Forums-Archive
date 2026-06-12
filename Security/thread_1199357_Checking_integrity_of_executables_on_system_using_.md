---
title: "Checking integrity of executables on system using dpkg"
date: 2009-06-28
forum: Security
---

### Post by nick_d on 2009-06-28
Recently my uni server has been hacked, among other things the intruders replaced the ssh client with one that sends any passwords to a site in Hungary.  In the meantime I probably logged into my home server from there, so I have to assume they have harvested my password, logged into my home server and given it the same treatment.  Of course I can zero in on the ssh client itself, perhaps remove and reinstall openssh using dpkg, but more generally, I would like to use dpkg to verify all installed files against the distribution release after having used digital signatures to verify the package files.  Is this possible?  Also, can dpkg tell me if other stuff has turned up in directories such as /sbin, i.e. list any files that aren't under package management?
Many thanks,
cheers, Nick

---

### Post by x3roconf on 2009-06-29
You should back up important files and do a complete re-install.

---

### Post by bodhi.zazen on 2009-06-29
> **x3roconf said:**
> you should back up important files and do a complete re-install.

+1

---

### Post by scorp123 on 2009-06-29
> **nick_d said:**
> can dpkg tell me if other stuff has turned up in directories such as /sbin There are packages that keep an eye on that such as "**tripwire**" ... But you have to install such tools **_BEFORE_** you get hacked, afterwards it's **_too late_** as you can't be really sure what else the hackers did manipulate or not.

So I second what you were already told: **Reinstall everything.** It's the only safe way to be sure that everything the hackers installed is gone.

And when you're done: **tripwire**. So you're better armed next time this happens.

---

### Post by rookcifer on 2009-06-29
> **scorp123 said:**
> There are packages that keep an eye on that such as "**tripwire**" ... But you have to install such tools **_BEFORE_** you get hacked, afterwards it's **_too late_** as you can't be really sure what else the hackers did manipulate or not.

So I second what you were already told: **Reinstall everything.** It's the only safe way to be sure that everything the hackers installed is gone.

And when you're done: **tripwire**. So you're better armed next time this happens.


I agree with the above.  However, Tripwire is not free.  You can use AIDE instead.

---

### Post by scorp123 on 2009-06-30
> **rookcifer said:**
> Tripwire is not free. Depends on which version you refer to. :D

[http://sourceforge.net/projects/tripwire/](http://sourceforge.net/projects/tripwire/)

> "Open Source Tripwire® software is a security and data integrity tool useful for monitoring and alerting on specific file change(s) on a range of systems. The project is based on code originally contributed by Tripwire, Inc. in 2000."

---

