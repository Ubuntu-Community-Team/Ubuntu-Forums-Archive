---
title: "LinuxRCD"
date: 2010-09-22
forum: The Cafe
---

### Post by nerdopolis on 2010-09-22
Hi.

I am trying to make a easy to use system rescue live CD for unbootable Linux/Ubuntu systems, kind of like how the ERD Commander is for Windows. Its here: [http://sourceforge.net/projects/linuxrcd/](http://sourceforge.net/projects/linuxrcd/)

Right now its still not complete at all, and I think it only works for *Ubuntu, not 100%.** Don't use it for a production system**. 

For example: Do not do anything involving aptitude, dpkg, apt-get on this cd just yet, as if it tries to update /etc/ld.so.cache, it fails, and the package manager quits itself. ( I just found that one out)

Anyway, I'm just looking for feedback judging on its ease of use, or features it needs, or problems with it.

---

### Post by phrostbyte on 2010-09-22
What tool did you use to develop this?

---

### Post by nerdopolis on 2010-09-22
Bash scripts, and remastersys.

The bash files make a chrooted system, and then the bash files remastersys it up.

---

