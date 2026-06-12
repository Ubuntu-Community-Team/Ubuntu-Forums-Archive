---
title: "Warty Backport: Firestarter 1.0.3"
date: 2005-02-17
forum: Ubuntu Backports
---

### Post by jdong on 2005-02-17
**Synopsis**
User request for newer Firestarter (1.0.0 was in Backports previously)

**Backporting Process**
The source archive directly came from Hoary. I was able to meet all dependencies. 

One modification: I modified the desktop shortcut to use gksudo instead of gksu. :)

**Packaging Status:**
i386 -- Staging at revision 49
amd64 -- Not packaged
ppc -- Not packaged

**Beta tester notes:**

---

### Post by jdong on 2005-02-17
firestarter: Depends: iptables (>= 1.2.11) but 1.2.9-10ubuntu0.1 is to be installed



Hmm, investigating...

---

### Post by jdong on 2005-02-17
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271078](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271078)

looks bad

---

### Post by Nano on 2005-02-27
[QUOTE=jdong][http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271078](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271078)

looks bad[/QUOTE]
 Running Firestarter 1.0.3 without problems.
Just installed the Debian package

---

### Post by jdong on 2005-02-27
Here's the deal:

Some new Firestarter 1.0.3 features require new IPTables features that the Warty version of IPTables doesn't offer. You may get "Invalid Argument" errors at bootup, and you certainly won't get that protection you specified.


If that's O.K. with you guys, I'll continue and mark it stable. I don't want to backport IPTables, as that's too critical a system component.

---

