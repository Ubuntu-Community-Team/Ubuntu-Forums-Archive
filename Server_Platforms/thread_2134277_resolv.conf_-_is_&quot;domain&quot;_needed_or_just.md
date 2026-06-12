---
title: "resolv.conf - is &quot;domain&quot; needed or just &quot;search&quot;?"
date: 2013-04-10
forum: Server Platforms
---

### Post by Hypnoz on 2013-04-10
I have resolv.conf set up in my environment for multiple search domains, and no "domain", which has always worked fine. However, a friend recently said this is the wrong way to set it up, and I *need* to have "domain" in there as well.

Currently it looks something like this

search sub.example.com example.com
nameserver 10.1.1.1

I'm not sure what I would gain by adding the "domain" option, or if it's needed at all.

---

### Post by Toxic64 on 2013-04-10
No search is ok anyway if you add anything to this file it will be back at previous state after reboot. so your domain entry won't be there anymore ...

---

### Post by Hypnoz on 2013-04-10
I believe the resolv.conf file only is overwritten if you have resolvconf running, or you have settings in /etc/network/interfaces. I have neither of these things on my servers, so the file isn't modified. And in any case, I have puppet managing the file, so if it was changed then puppet would just set it back.

---

### Post by CharlesA on 2013-04-10
> **Hypnoz said:**
> I believe the resolv.conf file only is overwritten if you have resolvconf running, or you have settings in /etc/network/interfaces.

Sorta. The dns settings in the interface file only apply if you have the resolvconf package installed. :)

---

### Post by jdthood on 2013-04-11
> **Hypnoz said:**
> I have resolv.conf set up in my environment for multiple search domains, and no "domain", which has always worked fine. However, a friend recently said this is the wrong way to set it up, and I *need* to have "domain" in there as well.

Unless you are using third-party software that itself looks for a "domain" line in /etc/resolv.conf, there is no need for a "domain" line in /etc/resolv.conf.

/etc/resolv.conf is a configuration file for the glibc resolver library. The resolver only uses either the "search" line xor the "domain" line but not both. The last one listed in the file wins. See resolv.conf(5). Because the "search" option is more flexible than "domain", allowing multiple arguments, resolvconf uses only the "search" option.

> **Hypnoz said:**
> Currently it looks something like this

search sub.example.com example.com
nameserver 10.1.1.1

Looks right.

> **Hypnoz said:**
> I believe the resolv.conf file only is overwritten if you have resolvconf running

When resolvconf is installed, other supported Ubuntu software talks to resolvconf instead of overwriting /etc/resolv.conf directly.

Resolvconf itself actually doesn't write to /etc/resolv.conf. It writes to /run/resolvconf/resolv.conf. This file is "active" if and only if /etc/resolv.conf is a symbolic link to /run/resolvconf/resolv.conf. In Ubuntu 12.04 and later, /etc/resolv.conf is normally a symbolic link to /run/resolvconf/resolv.conf.

> **Hypnoz said:**
> And in any case, I have puppet managing the file, so if it was changed then puppet would just set it back.

Removing the symbolic link at /etc/resolv.conf and putting a static file there, or a file managed by another tool, is supported. The resolvconf program never touches /etc/resolv.conf. The resolvconf *package* installs the aforementioned symbolic link on *initial* installation, or if the admin does "sudo dpkg-reconfigure resolvconf" --- but not otherwise.

---

