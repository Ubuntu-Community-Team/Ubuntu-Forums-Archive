---
title: "is Debian etch going to be biarch?"
date: 2006-09-27
forum: The Cafe
---

### Post by NoTiG on 2006-09-27
its supposedly "supporting" 64 but does that mean it will get biarch support ?

---

### Post by Wolki on 2006-09-27
No, supporting an architechture means that there are official builds for it. Sarge has no official AMD64.

---

### Post by plb on 2006-09-27
etch will have an official amd64 build

---

### Post by bonzodog on 2006-09-27
The debian 64 bit philosophy is to keep it "pure". This means that all 64 bit libs go in /usr/lib64 and all 32 bit libs go in /usr/lib32. 
/usr/lib is merely a symlink to /usr/lib64.

This makes it hard to go bi-arch without major alterations to the tree.

Most bi-arch distros not based on Debian, like Suse, Redhat, and gentoo, have just 2 directories;

/usr/lib which contains 32 bit libs and /usr/lib64 for the 64 bit libs.

---

