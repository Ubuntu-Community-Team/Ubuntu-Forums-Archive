---
title: "how to debug apt-get (xenial)"
date: 2016-09-23
forum: Server Platforms
---

### Post by allanj on 2016-09-23
Hi

I am setting an Automatic server install up for trusty and xenial, and the trusty setup is almost done, but now I am having problems with the xenial setup.

It is with PXE boot and preseed, and the install finishes OK, but after I am missing a lot of software, and when I look in /var/lib/apt/lists/ only the files for main, main/restricted, updates main and updates main/restricted is there, while all universe, multiverse and  backports are under /var/lib/apt/lists/partial/ which Means they are not available, but I can find no clue to why these lists are not usable ?

There are a lot of errors when I run apt-get update, but these are mainly with missing i386 files, which I dont need. I am using a local mirror, that is updated nightly with apt-mirror, if that makes a difference.

Best regards
Allan

---

### Post by allanj on 2016-09-23
Offcause I found the reason for the problem just 1 hour after posting it, it was the missing i386 packages that caused it, so after i ran "dpkg --remove-architecture i386" everything is OK.

---

### Post by ajgreeny on 2016-09-23
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

