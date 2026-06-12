---
title: "NFS for PHP Scripts?"
date: 2010-02-23
forum: Server Platforms
---

### Post by ThomWilhelm on 2010-02-23
Hi there, just need a quick bit of advice.

I have an application server and a backend server which perform PHP operations for the same site, both need access to about 20 identical scripts inside an /includes/ directory in their /var/www/ directory.

The problem is keeping these files synchronised if I change one of them as they should be exactly the same if I fix a bug for example. I know I could use rsync but if possible I am looking into one server loading the includes directory from the other server using NFS.

This must be a common problem for other websites, does this sound like a sensible solution performance wise? Or can anyone recommend anything better...

Thanks.
Thom.

---

