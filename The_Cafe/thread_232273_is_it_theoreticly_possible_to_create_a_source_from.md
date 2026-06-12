---
title: "is it theoreticly possible to create a source from a program ?"
date: 2006-08-08
forum: The Cafe
---

### Post by MaximB on 2006-08-08
yeh I know if it was possible now, you would create a source of winxp ;)
but is it _**THEORETICLY**_ possible to create a source from a program ?
yes/no why ???

---

### Post by weatherman on 2006-08-08
> **MAXDDARK said:**
> yeh I know if it was possible now, you would create a source of winxp ;)
but is it _**THEORETICLY**_ possible to create a source from a program ?
yes/no why ???

yes, it's called reverse engineering. it's been done many times but usually it's illegal.

---

### Post by ember on 2006-08-08
It is possible. You can dissamble the binaries and as far as I know there are even code generators for C code. But you would not want to read that ;)

---

### Post by MaximB on 2006-08-08
if it is indeed possible , why do we have to wait until say - ATI releases the source ? we could create our own so it would work with linux ?

---

### Post by ember on 2006-08-08
Because

a) It is illegal
b) The re-engineered source code is unstructed and contains no comments, so it is nearly impossible to understand.

---

### Post by Tomosaur on 2006-08-08
You won't end up with the source code, you'll end up with something which may or may not resemble the source code.

---

### Post by G Morgan on 2006-08-08
I think the point is when I write source code I title my variables like this

int namethatusefullydescribesthevariable;

just a little shorter ;).

The same can be applied to functions, classes, whatever. You won't have any descriptions for 'decompiled' code. You would have to work out every little millimeter, piece by piece. Also its illegal as has been mentioned.

---

### Post by mips on 2006-08-08
> **ember said:**
> Because

a) It is illegal


Depends on how you do it. [http://en.wikipedia.org/wiki/Clean_room_design](http://en.wikipedia.org/wiki/Clean_room_design)

---

### Post by aysiu on 2006-08-08
I don't know anything about programming, but I'd imagine it's like trying to figure out the recipe for a well-cooked dinner by just tasting the dinner...

---

### Post by aktiwers on 2006-08-08
> **MAXDDARK said:**
> yeh I know if it was possible now, you would create a source of winxp ;)


Some people are trying to make a clone of windows without stealing there code.

[http://www.reactos.org/xhtml/en/index.html](http://www.reactos.org/xhtml/en/index.html)

I have been watching this project for more than 2 years.

---

### Post by ember on 2006-08-08
Nice description :)

---

### Post by bonzodog on 2006-08-08
Reverse engineering has been used extensively in Linux code, but has been damn near impossible to prove, and for some reason, no-one has ever bothered to really do anything about it.

The Samba project is a prime case in point - getting windows protocols to work on linux code. They worked out these protocols by reverse engineering, and, ironically, MS now contribute code to the project to advance cross communication between the two OS's.

This also happened with earlier versions of Gaim, where working out the MSN protocols was done by hackers, then reverse engineering them.

Likewise. the wine project was an early project in attempting to work out the windows API by using reverse engineering.

One of the prime reasons MS has never taken these people to court (although they were thinking about it with Samba), is because, if anything, it has saved them work, and also, the people doing it have remained highly anonymous, and no-one really ever knew who they were - just some nicknames in a collaborative website based in a neutral country that MS would have problems shutting down.

This also happened with various hardware drivers used in xorg. Yes, people, linux IS the work of genuine Hackers. But, ultimately it had a good purpose, and now most work and code in Linux is legitimate and no-one seems to mind (except maybe SCO!!!!).

---

### Post by MaximB on 2006-08-08
I think that now novell (the complany that developed unix -if I'm not mistaken) is crying - they never knew what would imarge from there source code...
I'm pretty sure they regret it now.

---

### Post by bonzodog on 2006-08-08
oh, trust me, SCO is entirely in the wrong about this - they thought that novell had licensed the code to them. IBM and Novell will win this, and, in the process sink SCO once and for all. 

[http://en.wikipedia.org/wiki/SCO_v._Novell](http://en.wikipedia.org/wiki/SCO_v._Novell)

---

### Post by darrenm on 2006-08-08
> **bonzodog said:**
> , ironically, MS now contribute code to the project to advance cross communication between the two OS's.

Got any sources for that info? I really don't think MS contribute any code to Samba. Microsoft are producing documentation on Windows communication protocols because the EU is forcing them to. AFAIK no code has ever changed hands.

---

### Post by forrestcupp on 2006-08-08
True reverse engineering is not illegal.  It is not illegal to figure out how something works with no prior knowledge of how it was created, and make a new compatible clone from the ground up.  What is illegal is when you actually use some of the original code in your project.

The Windows clone, ReactOS, ran into a little trouble when they found out someone developing for them had at one time been a developer for MS.  So to avoid lawsuits, they had to go through all of their code to make sure none of it was stolen.

Reverse engineering is not illegal.

And no, I don't think it is really possible to get source out of a binary.  A compiled program is changed to machine code which is all 1's and 0's.  Most of the higher level language stuff is converted to lower level routines that is actually nothing like how it was programmed.  That is the benefit of programming languages, that you can write something more simple, and the compiler will make it into a complex thing that the computer can understand.  It is impossible to even tell what programming language a binary was made from.

---

### Post by %hMa@?b&lt;C on 2006-08-08
as to add to Mips' post
[http://en.wikipedia.org/wiki/Chinese_wall](http://en.wikipedia.org/wiki/Chinese_wall)

---

### Post by bonzodog on 2006-08-09
> **darrenm said:**
> Got any sources for that info? I really don't think MS contribute any code to Samba. Microsoft are producing documentation on Windows communication protocols because the EU is forcing them to. AFAIK no code has ever changed hands.

yup, I knew that there was an article somewhere:

[http://www.cbronline.com/article_cbr.asp?guid=8F9E4BC2-A79C-405A-AEA9-69D31357223C](http://www.cbronline.com/article_cbr.asp?guid=8F9E4BC2-A79C-405A-AEA9-69D31357223C)

---

