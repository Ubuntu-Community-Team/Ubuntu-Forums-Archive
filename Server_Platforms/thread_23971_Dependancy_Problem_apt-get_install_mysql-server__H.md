---
title: "Dependancy Problem: apt-get install mysql-server : Hoary-RC"
date: 2005-04-04
forum: Server Platforms
---

### Post by capi on 2005-04-04
On Hoary, apt-get can't seem to find 'libstdc++2.10-glibc2.2'. From what I can gather there is no problem when you upgrade from warty. zliblg-dev is also missing. I ran apt-get update to no avail.

Any ideas.

---

### Post by PMO6022 on 2005-04-04
I am seeing libstdc++2.10-glibc2.2 in the Hoary repo's:
 ```
 pmorris@ubuntu:~ $ apt-cache search glibc2.2
libg++2.8.1.3-glibc2.2 - The GNU C++ extension library - runtime version
libstdc++2.10-glibc2.2 - The GNU stdc++ library
``` 

I don't know why you aren't getting it if it is a dep for mysql-server.  Maybe try installing it separatly, then installing mysql?

I'm not having much luck locating zliblg, though.  I'll post again if I find anything.

---

### Post by capi on 2005-04-04
[QUOTE=PMO6022]I am seeing libstdc++2.10-glibc2.2 in the Hoary repo's:
 ```
 pmorris@ubuntu:~ $ apt-cache search glibc2.2
libg++2.8.1.3-glibc2.2 - The GNU C++ extension library - runtime version
libstdc++2.10-glibc2.2 - The GNU stdc++ library
``` 

I don't know why you aren't getting it if it is a dep for mysql-server.  Maybe try installing it separatly, then installing mysql?

I'm not having much luck locating zliblg, though.  I'll post again if I find anything.[/QUOTE]
 zliblg was my fault. It is actually zlib1g, My screen font didn't show the L and #1 to be different. I figured it out right after I posted, However, I still cannot get the glibc2.2. apt-cache show and apt-cache search reveal nothing. I get libstdc++5-3.3 and I get libstdc++6 . I typed in the exact same thing as you above and it came up blank. I think I may be missing a source. Here are the ones in /etc/apt/sources.list

> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

#and then my dot.deb files.
deb [http://packages.dotdeb.org](http://packages.dotdeb.org) ./
deb-src [http://sources.dotdeb.org](http://sources.dotdeb.org) ./

Out of curiousity, I'm going to try and see if I can find then in the Universe? I shouldn't need to have to do that though, should I. :\

?


EDIT**Uncommenting the Universe seems to have solved all my problems. If anyone knows of another way, I'd be happy to hear, but it loks like that solved it.**

---

