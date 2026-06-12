---
title: "Password Safe won't load."
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mjhatten on 2012-04-25
I downloaded the Password Safe package (passwordsafe-ubuntu-0.7.0BETA.i686.deb) to my two 64-bit 12.04 Ubuntu systems.  It loads into my Lubuntu system but not my Kubuntu system.  The Kubuntu system reports "wrong architecture 'i386'".

I'm a  total noob.  Any suggestions?

---

### Post by grahammechanical on 2012-04-25
I am guessing that you have Kubuntu i386 installed

Try running the command

```
arch
```

and see what it says.

Regards

---

### Post by z3nhakr on 2012-04-25
im not sure what your uses are and this is just my opinion but if you are going to use a password safe, you might as well use the same password for everything.

---

### Post by mjhatten on 2012-04-25
michael@michael-Aspire-5742:~$ arch
x86_64
michael@michael-Aspire-5742:~$ 


I use Password Safe because passwords are most vulnerable in transit or with phishing attacks.  If I use different passwords, then only one web site is affected.  Password Safe helps me keep track of which password goes where.
For someone to crack my password safe, they have to compromise my system directly in a way that also compromises Password Safe --  a much harder thing to do.

---

### Post by -Robert- on 2012-04-25
You can try to compile Password Safe yourself, and see if that works.
I guess you downloaded it from sourceforge.net: [http://sourceforge.net/projects/passwordsafe/files/Linux-BETA/0.7.0/](http://sourceforge.net/projects/passwordsafe/files/Linux-BETA/0.7.0/) ?
Password Safe 0.6.0 provides a 64-bit version: [http://sourceforge.net/projects/passwordsafe/files/Linux-BETA/0.6.0/](http://sourceforge.net/projects/passwordsafe/files/Linux-BETA/0.6.0/)

---

### Post by mjhatten on 2012-04-25
Thanks -- the page I found didn't have the 64-bit version of 0.6.  The 64-bit version appears to be loading.  Thanks.

---

