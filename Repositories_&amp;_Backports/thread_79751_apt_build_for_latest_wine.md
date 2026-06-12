---
title: "apt build for latest wine?"
date: 2005-10-20
forum: Repositories &amp; Backports
---

### Post by jdawdy on 2005-10-20
The latest source version of wine is 20050930, but all the .deb packages are 0725.  Is it possible to add the sourceforge repositories for the deb-src and apt-get build-dep and build source?  Will this result in the latest version or the 0725 version?

tnx
Jim

---

### Post by jamesstansell on 2005-10-20
[QUOTE=jdawdy]The latest source version of wine is 20050930, but all the .deb packages are 0725.  Is it possible to add the sourceforge repositories for the deb-src and apt-get build-dep and build source?  Will this result in the latest version or the 0725 version?

tnx
Jim[/QUOTE]
The result will be the 0725 version, since the sourceforge apt repositories (both binary and source) only have the 0725 version.

I was able to compile the 0930 version on hoary by downloading the tarball and using the breezy diff file with some changes.  It wasn't difficult, but I don't recall all the steps right now.  I have some notes about it somewhere.

-james.

---

### Post by jdawdy on 2005-10-21
[QUOTE=jamesstansell]The result will be the 0725 version, since the sourceforge apt repositories (both binary and source) only have the 0725 version.

I was able to compile the 0930 version on hoary by downloading the tarball and using the breezy diff file with some changes.  It wasn't difficult, but I don't recall all the steps right now.  I have some notes about it somewhere.

-james.[/QUOTE]

James,
A HOWTO on that would be great, or send me a copy of your notes and I will have a crack at it.  kc7rcy at yahoo.com

Jim

---

