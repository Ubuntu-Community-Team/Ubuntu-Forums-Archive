---
title: "Graphical sudo does not work, but terminal does work"
date: 2006-11-16
forum: The Cafe
---

### Post by user1397 on 2006-11-16
im using feisty kubuntu (i know that it is supposed to be buggy, so dont take this as a complaint or anything, just as an observation, unless u know the solution of course)

so yesterday everything was working fine, but then today i tried opening adept updater and found that graphical sudo will not accept my password, even though i tried it in a konsole and it worked.  trust me, ive tried it a million times, it just wont accept my password when sudo is in a GUI (kdesu)

is this just cause of the alpha-ness of feisty, or is it something a lot rarer, and perhaps a huge bug?

---

### Post by user1397 on 2006-11-19
anyone know?

---

### Post by patwack on 2006-11-20
this happens me in kubuntu edgy too, not sure why, works sometimes, not others

---

### Post by frup on 2006-11-20
I'm not using feisty but this is what terminal gives me on edgy.

(gedit:7418): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

still works though when i first began testing edgy my whole gksudo was broken...

---

### Post by mrgnash on 2006-11-20
> **frup said:**
> I'm not using feisty but this is what terminal gives me on edgy.

(gedit:7418): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

still works though when i first began testing edgy my whole gksudo was broken...

That's a standard message, it's not an indication that anything is actually wrong.

---

### Post by frup on 2006-11-20
okie :o lol

---

### Post by user1397 on 2006-11-25
weird...it suddenly works now (must've been those updates)

---

### Post by DoctorMO on 2006-11-25
I've found the gnome admin tools are borked, they always ask for the root password even when run from root user and hardly any of them function correctly.

---

### Post by user1397 on 2006-11-25
> **DoctorMO said:**
> I've found the gnome admin tools are borked, they always ask for the root password even when run from root user and hardly any of them function correctly.hmmm...well that's not good!  do you know if they're planning to fix this at all?

---

