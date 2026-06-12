---
title: "Mac Games and Linux, BSD and Solaris"
date: 2008-07-01
forum: The Cafe
---

### Post by global citizen on 2008-07-01
hello community,


While I am not a Linux newbie as I have used Opensuse, Fedora, Freespire distros I am new to Ubuntu. Ubuntu has indeed become very popular now and I would like to test Ubuntu. Anyway just a small question from the ones who know much about Unix based Oses. Is it possible to play Mac games in Linux, BSD or Solaris since Mac is itself based on BSD Unix? If so with what modifications?

---

### Post by mips on 2008-07-01
No. It's not as simple as that.

---

### Post by quanumphaze on 2008-07-01
Sorry they can't.

Mac OSX uses different APIs for the desktop than other *NIX OS's. Plus it doesn't use an X server for the graphics either. It would require an implementation of Apple's APIs with something like Wine for Mac (Mine?).

One plus is that it should be easier for the developer to port it to Linux in the future since it's already made with cross-platform code. 2nd plus is the Windows version should run with more success in Wine if it has a hidden OpenGL option.

---

### Post by Dixon Bainbridge on 2008-07-01
BSD can run linux apps but not vice versa afaik.

---

### Post by madjr on 2008-07-01
mac is a close source OS even if unix based.

the only good thing is they have to use openGL

---

### Post by hanzomon4 on 2008-07-01
Also UNIX is a proprietary OS..... System V(5?) or something like that. All the other FOSS Unix OSs other are based on BSD with the exception of OpenSolaris which is Sys V.... I think?

---

### Post by eragon100 on 2008-07-01
No,linux was/is written from scratch, and is losely based on minix, not bsd.

---

### Post by hanzomon4 on 2008-07-01
> **eragon100 said:**
> No,linux was/is written from scratch, and is losely based on minix, not bsd.

I never said Linux was Unix ;)

---

### Post by zmjjmz on 2008-07-01
Nope.

---

### Post by quanumphaze on 2008-07-02
> **hanzomon4 said:**
> I never said Linux was Unix ;)

Obligatory: **[SIZE="4"]GNU's Not Unix[/SIZE]**

---

### Post by toupeiro on 2008-07-02
> **quanumphaze said:**
> Obligatory: **[SIZE="4"]GNU's Not Unix[/SIZE]**

His statement was accurate.  Most other FOSS UNIX OSes are based on the BSD model with exception to modern day Solaris and anything based on modern day Solaris.  Solaris was at one time based on BSD until they saw the beauty of runlevels.  GNU need not apply.  In fact, anything that uses an /etc/rc#.d and /etc/init.d model is using a system V model, whether it be UNIX/Linux/minix/GNU or anything else.

---

### Post by hanzomon4 on 2008-07-02
> **quanumphaze said:**
> Obligatory: **[SIZE="4"]GNU's Not Unix[/SIZE]**

I'm assuming we're in agreement, but if not allow me to clarify: When I say Unix I mean Unix, not Linux. Freebsd, OpenSolaris, AIX, HP-UX... all Unix. **L**inux **i**s **n**ot **u**ni**x**.

---

### Post by madjr on 2008-07-02
> **hanzomon4 said:**
> I'm assuming we're in agreement, but if not allow me to clarify: When I say Unix I mean Unix, not Linux. Freebsd, OpenSolaris, AIX, HP-UX... all Unix. **L**inux **i**s **n**ot **u**ni**x**.

**L**inux **i**s **n**ot **u**ni**x**.


does L.i.n.u.x really stand for that ?

---

### Post by toupeiro on 2008-07-02
> **madjr said:**
> **L**inux **i**s **n**ot **u**ni**x**.


does L.i.n.u.x really stand for that ?

Its definately clever, but Linux is Linus with an x. :)

---

