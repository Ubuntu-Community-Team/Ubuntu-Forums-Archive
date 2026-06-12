---
title: "Server version for VM with native mysql 5.1"
date: 2013-01-07
forum: Virtualisation
---

### Post by 1clue on 2013-01-07
Hi,

I'm looking for a minimal version of Ubuntu to be put on a VM, that came with mysql 5.1.  Rather than try to back-port 5.1 onto 12.x I want to get a stable distro that actually had it.  I think that's more likely to be stable since the older stuff is only on maintenance releases now.

This is to be a stored build environment for old versions of our software, to support existing customers.  I will NEVER update it as far as installed packages, only (possibly) source code which we write.

The distro must be 64-bit intel, would prefer an LTS but right now I'm thinking 11.10 looks pretty good too.

Would love to hear your recommendations.

Thanks.

---

### Post by Cheesemill on 2013-01-08
Doing a quick search of the Ubuntu package database shows that Lucid uses mysql-server 5.1.66.
[http://packages.ubuntu.com/search?keywords=mysql-server&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=mysql-server&searchon=names&suite=all&section=all)

10.04 (Lucid Lynx) is an LTS release and is supported until April 2015 for servers, so there is just over 2 years of support remaining.

---

### Post by 1clue on 2013-01-08
Thanks.

---

