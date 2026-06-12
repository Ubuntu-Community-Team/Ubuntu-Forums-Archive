---
title: "SELinux vs AppArmour"
date: 2008-04-14
forum: Security Discussions
---

### Post by Duckyspetrie on 2008-04-14
Should I install SELinux in 8.04 (is it better than AppArmour) and if I do, can it coexist with AppArmour? Are there any advantages to running it?

---

### Post by HermanAB on 2008-04-14
SELinux is mainly intended for government use, to keep data with different classification levels separated on the same machine.  It can be used in a degraded mode for common server security.  However, my feeling about SELinux, is that it is strictly for masochists only.

---

### Post by netlogic on 2008-04-14
> **HermanAB said:**
>    However, my feeling about SELinux, is that it is strictly for masochists only.

yea, i have my gun handy for Sendmail and Selinux.

---

### Post by kutjara on 2008-04-14
> **HermanAB said:**
> SELinux is mainly intended for government use, to keep data with different classification levels separated on the same machine.  It can be used in a degraded mode for common server security.  However, my feeling about SELinux, is that it is strictly for masochists only.

"Intended for government use" tells me everything I need to know about that piece of software. ;)

---

### Post by Duckyspetrie on 2008-04-15
So how easy is deploying it and using it on a regular desktop? The way you talk about it makes it sound more secure than AppArmour, which can't be a bad thing, eh? And what about coexistence between the two?

---

### Post by Chayak on 2008-04-15
The quick and dirty...

SELinux works by > enforcing mandatory access control policies that confine user programs and system servers to the minimum amount of privilege they require to do their jobs. When confined in this way, the ability of user programs and system daemons to cause harm when compromised (via buffer overflows or misconfigurations, for example) is reduced or eliminated.

AppArmor was created by Novell as an alternative for SELinux.  It's simpler to configure and uses file paths rather than inode addressing.  It's basically a dumbed down version of SELinux though that doesn't say it doesn't work.  It's just a lot easier to configure.

Can they live together? I wouldn't try it.  SELinux is much more granular in it's control and configuration.  It would be good for servers with a large target profile.  AppArmor on the other hand is a lot easier, does a good job and much less painful to use on a desktop or workstation.

---

### Post by HermanAB on 2008-04-15
If you really want to know how to secure a system, read this: 
[http://www.nsa.gov/snac/os/redhat/rhel5-guide-i731.pdf](http://www.nsa.gov/snac/os/redhat/rhel5-guide-i731.pdf)

Cheers,

Herman

---

