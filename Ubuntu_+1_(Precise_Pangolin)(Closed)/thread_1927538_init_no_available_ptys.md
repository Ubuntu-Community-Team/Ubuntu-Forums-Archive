---
title: "init: no available ptys"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by puccaso on 2012-02-18
cant boot  my system after recent updates.

Any help?

Get error msj

Init : no available ptys 

Repeats over and over

---

### Post by mtecknology on 2012-02-18
I'm seeing the same thing. Haven't figured out why or how to fix yet.

---

### Post by puccaso on 2012-02-18
could it be a pty permissions issue?
or could it be fixed with makedev pty (had a similar problem with redhat4 YEARS ago :)

---

### Post by mtecknology on 2012-02-19
> **puccaso said:**
> could it be a pty permissions issue?
or could it be fixed with makedev pty (had a similar problem with redhat4 YEARS ago :)

It's not a permission issue as far as I can see. I'm rather certain it was caused by an update. Unfortunately, I really don't have much more yet.

---

### Post by clytle374 on 2012-02-19
> **mtecknology said:**
> It's not a permission issue as far as I can see. I'm rather certain it was caused by an update. Unfortunately, I really don't have much more yet.

I am using Precise for building a machine control using Linuxcnc.  I have developed the same issue after updateing, but only with the rtai patched 2.6.38.8 kernel that worked beofre the update.  The stock kernel still functions properly.:confused:  Sorry, I know that is of almost zero help... Just didn't want you to feel alone.  

Cory

---

### Post by mtecknology on 2012-02-19
If you add --no-log as a kernel parameter, you can get around this issue. It's an issue with upstart. Check out [https://launchpad.net/bugs/936667](https://launchpad.net/bugs/936667).

---

