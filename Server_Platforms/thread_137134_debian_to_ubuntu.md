---
title: "debian to ubuntu"
date: 2006-02-27
forum: Server Platforms
---

### Post by emptymind on 2006-02-27
Hi

I have a server running Debian-testing but some of the software on it is unstable and I wanted to convert it to Breezy. Do I have re-install or can I just change the server-list in /etc/apt/sources.list to point from Debain to Breezy servers?
I am unsure that this will work and I was wondering if anyone has tried something like this.

Thanks.

---

### Post by Wide on 2006-02-27
Never did what your loking to do.

Debian is a great server flavor, why not just backport whats giving you issues or go to stable.


:D

---

### Post by emptymind on 2006-02-27
[QUOTE=Wide]Never did what your loking to do.

Debian is a great server flavor, why not just backport whats giving you issues or go to stable.


:D[/QUOTE]

I initially went to testing because the versions on the compilers on stable were too old and didn't keep pace with what was available. This is true with a lot of the other software as well. I guess I could compile the newer software I need from scratch but I don't maintain computers full time.
Also, I have started using Ubuntu on the desktop and am starting to like it. I can't imagine using any other distro not based on apt.

---

### Post by az on 2006-02-27
[QUOTE=emptymind]Hi

I have a server running Debian-testing but some of the software on it is unstable and I wanted to convert it to Breezy. Do I have re-install or can I just change the server-list in /etc/apt/sources.list to point from Debain to Breezy servers?
I am unsure that this will work and I was wondering if anyone has tried something like this.

Thanks.[/QUOTE]
Hmmm.   You would have to try it.  

A more sure path would be to wait a month and then dist-upgrade to Dapper.  Dapper will be the stable ubuntu release in a month.

The problem is that you are using the testing branch of debian.  If you were using stable, then dist-upgrading to breezy would be a jump ahead.  Since you are using testing, some packages you have installed may be earlier versions than breezy ones, in which case you upgrade to newer ones, but some may be later, which is the problem.  You will not have this problem with an Etch-in-testing versus Dapper upgrade. 

If you point your sources.list to breezy, update and then ask it to dist-upgrade, and it does not spit out ugly packaging problems, you should be okay, I guess.  Just remove the debian repositories from your list.

To jump from one release to another is far less pathological than to keep a mixed system (repositories from different releases at the same time)

---

