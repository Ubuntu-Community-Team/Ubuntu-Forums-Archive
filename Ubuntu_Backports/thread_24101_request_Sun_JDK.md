---
title: "request: Sun JDK?"
date: 2005-04-05
forum: Ubuntu Backports
---

### Post by gbusse on 2005-04-05
Greetings,

I noticed that the Sun JRE is available in the hoary-extras/restricted repository. This is great but I was wondering if it was possible to also add the Sun JDK? I know I can install it manually but I just love this apt-get thing.

Thanks in advance,
Gord

---

### Post by Leif on 2005-04-05
You can apt it by adding :

deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java

to your sources.

---

### Post by jdong on 2005-04-05
Sure, I'll get that packaged soon.

---

### Post by gbusse on 2005-04-10
jdong,

Thank you very much!

Gord

---

### Post by randell6564 on 2006-06-02
CRAP!

I added that source to my list and got this:

W: Couldn't stat source package list [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) warty/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_warty_java_binary-i386_Packages) - stat (2 No such file or directory)


WHAT GIVES?!

---

### Post by lithorus on 2006-06-03
[QUOTE=randell6564]CRAP!

I added that source to my list and got this:

W: Couldn't stat source package list [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) warty/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_warty_java_binary-i386_Packages) - stat (2 No such file or directory)


WHAT GIVES?![/QUOTE]
Because it's not there (too old I guess), btw. jdk is in the official Dapper repo (multiverse) now.

---

