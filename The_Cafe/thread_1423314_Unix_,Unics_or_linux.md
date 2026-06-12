---
title: "Unix ,Unics or linux?"
date: 2010-03-06
forum: The Cafe
---

### Post by nene7 on 2010-03-06
hi to all,
 i was searching in the web sometime about what are the diferents of Unix and linux, but i dont really understand well. I know linux is not unix, but i still confuse why is said linux is like-unix? And what are the difference?

---

### Post by juancarlospaco on 2010-03-06
[B]Linux=Kernel
Unix=Spec[/B]

:)

---

### Post by cap10Ibraim on 2010-03-06
"
Let’s get one thing clear right from the start. Even though Linux is not called UNIX, it is a complete UNIX implementation. It conforms to many of the same standards as off-the-shelf, genuine, dyed-in-the-wool UNIX (in fact, better than many commercial UNIX versions), and it would be very difficult for even a veteran UNIX user to know whether they were working with Linux or UNIX without using tools that specify the identity of the system. Why isn’t Linux called UNIX? Copyright reasons.

Because Linux is UNIX in all but name, it’s a great way to learn UNIX. Not only can Linux run on most PCs that are sitting around your basement (try that with most commercial UNIX versions today; most of them need a Pentium or fast 80486), it is a fraction of the cost of a full-blown UNIX. Anything you learn with Linux is directly transferable to a UNIX platform. Applications you write under Linux can usually be recompiled under UNIX and work perfectly.

Having said all that, Linux is an obvious way to learn the joys of UNIX. UNIX is one of the most powerful operating systems available and is commonly used by large corporations and other companies focusing on research and development. The reason is simple: UNIX puts the most power at a developer’s fingertips. It’s also the best way to network a bunch of machines. While you may not need to know UNIX now, you never know what will come up in the future. It looks great on your résumé, too."

Linux Unleashed, Third Edition     
(Imprint: Sams) 
(Publisher: Macmillan Computer Publishing) 
Author: Tim Parker 
ISBN: 0672313723

---

### Post by wojox on 2010-03-06
Unices - Linux is a type of unix

---

### Post by amauk on 2010-03-06
[http://ubuntuforums.org/showthread.php?p=6557569#post6557569](http://ubuntuforums.org/showthread.php?p=6557569#post6557569)

---

### Post by Bachstelze on 2010-03-06
[This](http://www.netbsd.org/about/call-it-a-duck.html) applies to Linux as well.

---

### Post by amauk on 2010-03-06
but naming / trademark issues aside,
the BSD's are a direct descendant of Unix
Linux is not

Linux is a clone of Unix, not a descendant

*edit*
(insert "GNU/" in the above, where appropriate...)

---

### Post by DeadSuperHero on 2010-03-06
> **wojox said:**
> Unices - Linux is a type of unix

Partially, not quite though. Linux is unix-like, and functions in very similar ways to UNIX. From a technical standpoint, I would argue that it's actually closer to UNIX than Mac OSX is.

However, Linux is not fully [POSIX]("http://en.wikipedia.org/wiki/POSIX")-compliant, and therefore does not meet the required criteria to be a [UNIX-certified kernel]("http://www.opengroup.org/platform/unix_certification/").

Existing Unix distributions are the 'BSDs, as well as OpenSolaris. (OpenSolaris, oddly enough, is derived from [SystemVR4]("http://en.wikipedia.org/wiki/UNIX_System_V"), and is the only Open Source Unix around.)

---

### Post by Bachstelze on 2010-03-06
> **Mr. Psychopath said:**
> From a technical standpoint, I would argue that it's actually closer to UNIX than Mac OSX is.

Tell me more about it.

---

### Post by kaldor on 2010-03-06
OS X changes the file hierarchy. No more /home/username, it's now /Users/username. No /usr, /opt/ etc. 

/Library
/Applications
/Users


At the OP:

-When you think UNIX, think about operating systems like *BSD, Solaris, AIX, HP-UX, IRIX etc. Linux is a clone of them; MINIX in particular. 

-Ubuntu, Debian, Mint, Fedora, SuSE, Slackware, etc are all distributions built on top of the Linux kernel. This makes an OS called GNU/Linux.

-*BSD, Solaris, AIX, others are built on top of a true UNIX kernel. 

-The Linux kernel was intended to be a free replacement for UNIX due to high costs of UNIX systems at the time.

UNIX is a family of operating systems. It is also a specification to certify an OS is a true UNIX system.

If you want to see a true UNIX OS, try out OpenSolaris LiveCD ([www.opensolaris.com](www.opensolaris.com)).

---

### Post by Bachstelze on 2010-03-06
> **kaldor said:**
> OS X changes the file hierarchy. No more /home/username, it's now /Users/username. No /usr, /opt/ etc. 

/Library
/Applications
/Users


You are wrong. /home and /usr are present by default on OS X. /home is not used by default, but /usr is. /opt is not present by default on many other OSs either.

---

### Post by juancarlospaco on 2010-03-06
BSD is not Unix.

---

### Post by Bachstelze on 2010-03-06
> **juancarlospaco said:**
> BSD is not Unix.

#define BSD ?

---

### Post by ibuclaw on 2010-03-06
> **kaldor said:**
> OS X changes the file hierarchy. No more /home/username, it's now /Users/username. No /usr, /opt/ etc. 

/Library
/Applications
/Users



Open a terminal in Mac OSX, and type in:
```

cd /
ls

```
and tell us what you see. ;)

---

### Post by juancarlospaco on 2010-03-06
> **Bachstelze said:**
> #define BSD ?

*BSD is not Unix

---

