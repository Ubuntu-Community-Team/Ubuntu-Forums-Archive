---
title: "How can I re-install 'Linbread'?"
date: 2009-10-26
forum: Ubuntu Christian Edition
---

### Post by atyar on 2009-10-26
While trying to uninstall Bible trivia, which I found annoying and always clicked to close whenever I fire up the pc, I wound up also uninstalling Linbread by mistake. 

How can I re-install Linbread?
Thanks!

---

### Post by david_kt on 2009-10-26
> **atyar said:**
> While trying to uninstall Bible trivia, which I found annoying and always clicked to close whenever I fire up the pc, I wound up also uninstalling Linbread by mistake. 

How can I re-install Linbread?
Thanks!

You could remove trivia and linbread from start up application without uninstalling it:

System >> Preference >> Start up apllication

Un-tick or delete trivia/linbread.

If you have remove it, you could install using below method:

sudo apt-get install ubuntu-ce

or

sudo apt-get install linbread.

DK

---

### Post by atyar on 2009-10-26
Thanks.....learn something new every day about U.c.e. :popcorn:

---

### Post by atyar on 2009-10-26
Hmm...I tried both when I got home from work, and neither worked - this is what I got:

dad@dad-laptop:~$ sudo apt-get install linbread
[sudo] password for dad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linbread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linbread has no installation candidate
dad@dad-laptop:~$ sudo apt-get install ubuntu-ce
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntu-ce is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-ce has no installation candidate
dad@dad-laptop:~$

---

### Post by david_kt on 2009-10-26
> **atyar said:**
> Hmm...I tried both when I got home from work, and neither worked - this is what I got:

Then you have to follow instruction on below page:

[http://ubuntuce.com/convert.htm](http://ubuntuce.com/convert.htm)

Choose the correct one (i386 or amd64).

DK

---

