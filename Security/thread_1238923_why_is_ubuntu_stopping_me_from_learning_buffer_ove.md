---
title: "why is ubuntu stopping me from learning buffer overflow?"
date: 2009-08-12
forum: Security
---

### Post by Seathan93 on 2009-08-12
To make a long story short, i bought a book on programming/hacking concepts and everything was going great.

Until...i got to the part of buffer overflow and followed the instructions in the book, but instead of buffer overflowing my test program, i got a bunch of lines of terminal code from ubuntu followed by the program crashing.  However in the book it has a VERY different output.

So my question is, what is it in ubuntu 9.04 that is stopping me from being able to buffer overflow my own computer?

Obviously since buffer overflow is a hacker technique i can understand if i cant get an answer about this subject, but if anyone knows a way that i can get ubuntu to allow me to buffer overflow my own computer it would be appreciated

i even tried sudo and then buffer overflowing my computer but that still didnt work

---

### Post by arky on 2009-08-13
Maybe the program buffer overflow issues have been fixed.

---

### Post by bodhi.zazen on 2009-08-13
Your information is (obviously) outdated , we have patches for those things.

I suggest you use [DVL](http://www.damnvulnerablelinux.org/)

---

### Post by Seathan93 on 2009-08-13
thanks i'll look into that

---

### Post by rookcifer on 2009-08-13
Ubuntu also has a few built in protections such as ASLR and stack smashing protections that specifically stop certain kinds of buffer overflows (though I don't believe the protections are as extensive as Fedora, though someone may correct me on that).  

Basically, it would be wise to use DVL, as bodhi said, for testing such exploits.

---

### Post by Seq on 2009-08-13
Stack protection is a feature of gcc that has been enabled by default in Ubuntu for a while now. You will need to disable it when compiling your programs (add -fno-stack-protector to your makefile or gcc arguments)

There is a [thread with an example]("http://ubuntuforums.org/showthread.php?t=570676") here in the forums

---

