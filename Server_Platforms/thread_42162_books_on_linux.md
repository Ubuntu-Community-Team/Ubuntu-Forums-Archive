---
title: "books on linux"
date: 2005-06-16
forum: Server Platforms
---

### Post by [pl]ice on 2005-06-16
hi, i'm new to linux, as a hobby only, but i cannot find good books to start with,
i'm not after something like linux for idiots ... ;)
  I have an option to recommend books for my uni; what i'm looking at is:

setting up samba (we got an old one...)
setting up vsftpd        [http://www.informit.com/title/0131861506](http://www.informit.com/title/0131861506)  ?? will check that


securing ssh

kernel explanation, from compilation to procedures call etc

i can't figure out how the all libraries are linked, and still i haven't seen any books to explain the topic more throughly...

the concept about the linux architecture, not the standard stuff, but eg. how  socks behave, more inside bits


Please advise, but be realistic,

thanks.

---

### Post by desdinova on 2005-06-16
Most of the O'Reilly books - Essential Systems Administration springs to mind, though Linux in a Nutshell is in more depth then its title suggests

---

### Post by relix42 on 2005-06-17
Samba = The Samba 3 Howto and Reference Guide and Samba 3 by Example- Part of the Perens Series - Full of wonderful examples for many different situations - small to large.

vsftpd = Really the EXAMPLES file is the best resources for this.  Once you read through the man page on vsftpd.conf you're about 90% of the way to understanding the whole thing - it can be tricky but isn't that complicated.

SSH = Lot's of on the 'net references.  Essentially, turn off every option you don't need, use only SSH Version 2, don't allow root login, use key exchange instead of passwords if possible, firewall the machine to only allow port 22 connections from known hosts.

Kernel Explanation, Complilation, procedure calls, etc - This is *big* topic and not likely to be answered by any single reference.  Pick one thing to start with (i.e. compilation) and move on from there.  You're likely to find more electronic documentation then primted because the kernel internals can be such a moving target.

HTH

---

### Post by [pl]ice on 2005-06-19
thanks

---

