---
title: "grsecurity"
date: 2008-09-08
forum: Security
---

### Post by Achilles124 on 2008-09-08
I am a desktop user of ubuntu, that is I don't use it as a server. Now I have read an article about security on ubuntu:
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/]("http://www.itsecurity.com/features/ubuntu-secure-install-resource/")

In it is mentioned the program: **grsecurity**. Does anyone have experience with this program? Would very much like to know.

---

### Post by rogeriopvl on 2008-09-08
I'm sure that if you don't use your machine as a server, you won't need that software.

Don't fill in your Ubuntu with unnecessary software, you are only slowing down your system for nothing.

---

### Post by Achilles124 on 2008-09-08
Okay, thank you for answering, rogeriopvl.

---

### Post by /etc/init.d/ on 2008-09-09
grsecurity is not for the feint of heart.  It is a kernel patch that requires compiling your own kernel and makes your system unsupportable.  It requires thought and knowledge of the various configuration options otherwise you will break your system.  Before attempting to patch your kernel with grsec you'd need to be familiar with rolling your own kernel in general and the various config options required for your system (drivers etc.)

---

