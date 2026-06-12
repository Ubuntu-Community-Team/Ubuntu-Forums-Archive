---
title: "backport maybe"
date: 2005-08-26
forum: Repositories &amp; Backports
---

### Post by simple on 2005-08-26
i found this url [http://mirror.isp.net.au/ftp/pub/ubuntu/pool/](http://mirror.isp.net.au/ftp/pub/ubuntu/pool/) searching for a repository for ubuntu that contains blackdown java because i want to apt-get install blackdown java, but not sure how, do i add like deb thaturl multiserve?

edit
or how about a mirror on blackdowns website? i had java working building my own package, but i had troubles with it in synaptic still somehow it was there, and now it's not there again after i removed it.
[ftp://ftp.tux.org/pub/java/debian/pool/non-free/j/j2se1.4-i586](ftp://ftp.tux.org/pub/java/debian/pool/non-free/j/j2se1.4-i586)

---

### Post by chiefofthejojos on 2005-08-26
if you have the url then you can probably just add this line to /etc/apt/sources.list:
deb url main multiverse universe restricted

Also, you should probably check out [this](http://www.ubuntulinux.org/wiki/Java) page to see why it's not in your synaptic list anymore.

---

