---
title: "Ubuntu 10..4 LDAP Config is Crap."
date: 2010-10-13
forum: Server Platforms
---

### Post by openfly on 2010-10-13
Why is the default config on Ubuntu 10.4 for LDAP so utterly, inconceivably, and irrecoverably broken?

Has anyone managed to successfully enable replication using this messed up slapd.d config?

I am pretty sure it is impossible.  And the only documentation I could find on it was utterly incorrect.

Dear Ubuntu, please hit your ldap package team with a trout.

---

### Post by arrrghhh on 2010-10-13
Ubuntu isn't much of an enterprise OS.  If you want better LDAP support, look at SLES or RHEL.

---

### Post by openfly on 2010-10-13
Seriously, I understand most of the people involved with ubuntu are volunteers, and they do this out of the kindness of their hearts... but the guy packaging their LDAP configs needs to be fired.  I don't care if he is doing this for free, he's out of his mind and causing a lot of damage with his irresponsible zomg I can make config changes without restarting ldap ********.  

I like the idea, really... I DO.  But his approach is broken, untested, undocumented, and well... sub alpha.

Dude just cost me an hour and half of my life I will never get back.  And is forcing me to fork a local ldap package set.

Seriously.  I am angry here.  This is uncool man.  UNCOOL.

---

### Post by arrrghhh on 2010-10-14
> **openfly said:**
> Seriously, I understand most of the people involved with ubuntu are volunteers, and they do this out of the kindness of their hearts... but the guy packaging their LDAP configs needs to be fired.  I don't care if he is doing this for free, he's out of his mind and causing a lot of damage with his irresponsible zomg I can make config changes without restarting ldap ********.  

I like the idea, really... I DO.  But his approach is broken, untested, undocumented, and well... sub alpha.

Dude just cost me an hour and half of my life I will never get back.  And is forcing me to fork a local ldap package set.

Seriously.  I am angry here.  This is uncool man.  UNCOOL.

I already told you LDAP in Ubuntu is not a good idea... why are you trying to fit a square peg into a round hole?!?

---

