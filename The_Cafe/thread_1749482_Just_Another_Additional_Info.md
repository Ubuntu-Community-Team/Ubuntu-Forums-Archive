---
title: "Just Another Additional Info"
date: 2011-05-04
forum: The Cafe
---

### Post by sostentado on 2011-05-04
Hi!

I've been using ubuntu for a year now and i sort found out one of the most important libraries or core applications that should be installed on any ubuntu distro is the 'build-essential'.
This is very useful for runnying fully functional ubuntu system

command:

apt-get install build-essential

---

### Post by ajgreeny on 2011-05-04
> **sostentado said:**
> Hi!

I've been using ubuntu for a year now and i sort found out one of the most important libraries or core applications that should be installed on any ubuntu distro is the 'build-essential'.
This is very useful for runnying fully functional ubuntu system

command:

apt-get install build-essential
I think most users manage very well without it!

Why do you think it is necessary?   That package is only needed by users who wish to compile their own versions of software packages from source, and I would be prepared to bet that the greatest majority of Ubuntu users never get as far as compiling anything at all.

With repos the huge size they are, and now with so many ppa sources for more updated versions of so many packages, I have never built/compiled anything in my 6 years of using Ubuntu.

---

### Post by doas777 on 2011-05-04
indeed; a very useful collection of packages.

the main reason they don't package it with the default install. is security. usually, it is a security "best practice" to restrict use of compilers to admins. this is to  prevent an attacker who has compromised a low level account from compiling custom apps to steal additional privileges (called an escalation attack). Ubuntu just goes a step further and makes you install them (as root).

for systems that I'm using for productivity purposes, I almost never need the build packages except for the kernel headers for vid card drivers. for my dev or server boxes, it depends on whether I've ever had to compile something there, and forgot to uninstall them later.

---

