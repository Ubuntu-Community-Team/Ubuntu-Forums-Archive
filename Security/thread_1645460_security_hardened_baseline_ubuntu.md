---
title: "security hardened baseline ubuntu"
date: 2010-12-14
forum: Security
---

### Post by dev.null on 2010-12-14
I'm tasked with creating a base image of ubuntu (one for server, one for workstation) that is locked down and has all the fluff taken out (naturally workstation will have more fluff left in it than server).

Task list looks about like this:

1. Create list of deb packages "allowed", write script to list/uninstall everything else.

2. Hook the logins into either enterprise kerberos or Active Directory (yuck).

3. Write scripts to check things like setuid/setguid, disabling su, checking sudo permissions, configure iptables, etc.

4. Use a scanner to scan the system from outside the system (was thinking of using backtrace).

5. Custom-compile the kernel to strip out all the unneeded modules.

Before embarking on this awesome task I figured I'd check with you guys to see if you know of some resources that would make this task easier/quicker. I'm sure someone out there has already headed down this branch.

PS My boss *loves* ubuntu and isn't to keen on going with a deb (or other) distro that is already "security trimmed" without some serious convincing. I'm sure there are some out there, and if you want to pass along a couple for consideration, I'll check them out, but no guarantees he'll let me use it.

Thanks In Advance!

---

### Post by bodhi.zazen on 2010-12-14
I think it is easier to start with a minimal install and add only what you need rather then remove things.

I also think there are better distros to do this with, Debian has less dependencies per package for example.

---

### Post by dev.null on 2010-12-14
> **bodhi.zazen said:**
> I think it is easier to start with a minimal install and add only what you need rather then remove things.

I don't disagree - is the vanilla install the absolute minimum needed to run?

> **bodhi.zazen said:**
> I also think there are better distros to do this with, Debian has less dependencies per package for example.

I don't disagree, but my boss...

He doesn't like how long it takes for debian to come out with updates. His perception is Ubuntu is more leading edge.

---

### Post by HermanAB on 2010-12-15
Howdy,

There are multiple reasons why government users use Red Hat, but probably the best reason is Kickstart.  The problem is that Ubuntu doesn't have it.

So, you can start with a server install and then add the desktop schtuff that you need, but how are you going to replicate it and how are you going to verify that you only installed what you said you installed? You got to solve that problem first - hence Kickstart and Red Hat/Suse/Mandriva.

If you want the gory details on how to lock systems down, read up on Common Criteria Certification.  There are quite a few guides for that, but again only for Red Hat like distros:

[http://h20338.www2.hp.com/enterprise/downloads/RHEL5-CC-EAL4-HP-Configuration-Guide.pdf](http://h20338.www2.hp.com/enterprise/downloads/RHEL5-CC-EAL4-HP-Configuration-Guide.pdf)

---

### Post by dev.null on 2010-12-15
> **HermanAB said:**
> Howdy,

There are multiple reasons why government users use Red Hat, but probably the best reason is Kickstart.  The problem is that Ubuntu doesn't have it.

Thanks Herman! A little poking around yields kickstart on ubuntu:

This:
[google search]("http://tinyurl.com/342pqm9")

Yields this [article]("https://help.ubuntu.com/community/KickstartCompatibility") as the second link.

I will be digging in.

Thanks again!

---

