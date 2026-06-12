---
title: "WINE32 in 20.04"
date: 2020-04-05
forum: Ubuntu Development Version
---

### Post by ping-wu on 2020-04-05
Has anyone successfully installed Wine32 in 20.04?

---

### Post by TheFu on 2020-04-05
> **ping-wu said:**
> Has anyone successfully installed Wine32 in 20.04?

Looks like using an LXD container is going to be the less hassle way to support WINE stuff.  
[https://ubuntuforums.org/showthread.php?t=2438654&p=13940195#post13940195](https://ubuntuforums.org/showthread.php?t=2438654&p=13940195#post13940195)

---

### Post by mc4man on 2020-04-05
Not sure what you mean by wine32?
wine installs and works fine here, most of the packages installed were i386..

---

### Post by kc1di on 2020-04-05
wine32 is no longer available.  You now need to install wine32:i386.  That being said the one 32 bit program I need will not run in 20.04.

---

### Post by DuckHook on 2020-04-05
> **kc1di said:**
> &#8230;the one 32 bit program I need will not run in 20.04.
Hi kc1di,

Though it's not an easy install, I've been able to get valuable old apps to run in older versions of WINE by running them within a LXD container. In my case, an old Windows game that won't run on newer WINE versions works perfectly in a WINE instance running within a containerized image of Trusty. The container sandboxes the EoL Trusty which allows WINE to run securely.

I should add that the version of WINE in Trusty is what it always was: 32-bit WINE.

---

### Post by kc1di on 2020-04-07
> **DuckHook said:**
> Hi kc1di,

Though it's not an easy install, I've been able to get valuable old apps to run in older versions of WINE by running them within a LXD container. In my case, an old Windows game that won't run on newer WINE versions works perfectly in a WINE instance running within a containerized image of Trusty. The container sandboxes the EoL Trusty which allows WINE to run securely.

I should add that the version of WINE in Trusty is what it always was: 32-bit WINE.

You can also install playonlinux which allows you to install most older versions of wine and places each program in it's own virtual file.

---

