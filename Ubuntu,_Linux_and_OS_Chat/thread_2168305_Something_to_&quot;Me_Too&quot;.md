---
title: "Something to &quot;Me Too&quot;"
date: 2013-08-17
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2013-08-17
**Add bookmark to Ubuntu Forums in Firefox default**:  [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1213354](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1213354) opened by  Lars Noodén.

---

### Post by Elfy on 2013-08-17
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by evilsoup on 2013-08-17
Good idea, +1.

---

### Post by ibjsb4 on 2013-08-17
We should be there

---

### Post by BlinkinCat on 2013-09-14
An excellent idea!

---

### Post by s.fox on 2013-09-17
Branch firefox, make the changes and then request a merge.

---

### Post by Lars Noodén on 2013-09-17
> **s.fox said:**
> Branch firefox, make the changes and then request a merge.

It looks like it is not as simple as pulling a branch and editing a file.  The file *./firefox/debian/patches/ubuntu-bookmarks.patch* is simply a patch to some other file unfamiliar to me.  It looks like it is necessary to find that original file, patch it, modify it, and then make a new diff.

---

### Post by s.fox on 2013-09-17
> **Lars Noodén said:**
> It looks like it is not as simple as pulling a branch and editing a file.  The file *./firefox/debian/patches/ubuntu-bookmarks.patch* is simply a patch to some other file unfamiliar to me.  It looks like it is necessary to find that original file, patch it, modify it, and then make a new diff.

Some work has already been done before on [this bug]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/602265"). Look at comment #19 and the [attached file]("https://launchpadlibrarian.net/97006157/bookmarks.html").

Not sure if this helps you / someone get started.

---

