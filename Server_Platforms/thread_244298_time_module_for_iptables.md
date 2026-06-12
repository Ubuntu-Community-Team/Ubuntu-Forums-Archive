---
title: "time module for iptables"
date: 2006-08-26
forum: Server Platforms
---

### Post by scav on 2006-08-26
Hi, Im trying to setup some time rules to prevent students visiting certain sites in class..

but when i try to load the time module it says it doesnt find it, ive tried searching the repo but cant find it!

anyone?

---

### Post by Woei on 2006-08-26
> **scav said:**
> Hi, Im trying to setup some time rules to prevent students visiting certain sites in class..

but when i try to load the time module it says it doesnt find it, ive tried searching the repo but cant find it!

anyone?

Well, the time module is an extension for the Netfilter code that is not shipped by default in a plain vanilla kernel, so it's not available by default on Ubuntu either. You'll want to read up on the '[patch-o-matic' system](http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO.html)', which makes these extra matches availabe to netfilter. However, that document is horribly outdated, the CVS server mentioned in the documentation has been out of service for some time now, replaced by a Subversion server.

So, first off, apt-get install subversion. Make a temporary directory, cd into it, and enter
```

svn co https://svn.netfilter.org/netfilter/trunk/patch-o-matic  patch-o-matic
svn co https://svn.netfilter.org/netfilter/trunk/iptables .

```

That will check out fresh sources for both the core iptables code and patch-o-matic. There's a readme file in the patch-o-matic directory, telling you what to do to patch your kernel sourcecode (you'll have to apt-get that too, it's in the *linux-source* package). After everything's patched, rebuild your kernel modules like you'd always do, and install them with make modules modules_install. After that, iptables should have the new time module available for use.

---

