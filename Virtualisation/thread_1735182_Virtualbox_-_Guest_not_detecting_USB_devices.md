---
title: "Virtualbox - Guest not detecting USB devices"
date: 2011-04-21
forum: Virtualisation
---

### Post by GridLynx on 2011-04-21
Hey all. 

I was just giving this whole virtualization thing a little run out of curiosity and got the following issue:

I tried plugging in my USB hard drive ( a Samsung S2 250 gbs) and apparently the Guest won't detect it!   When i look for the devices tab, it will display the name of said piece and if i hover the mouse over it, will display information regarding it and the statement ( Unavailable).   It has happened not only with that but with kingston memory stick as well, as well as an optic mouse ( which oddly enough even tho it displays it as unavailable, it runs :P) 

Just for the filling i have intalled the following:
- Vbox Guest additions.
- Vbox Extension pack.

Help would be appreciated!

---

### Post by GridLynx on 2011-04-21
**UPDATE ON MY SITUATION**

Apparently the only devices not being detected by the GUEST computer are those on which the HOST hasn't laid claim... i verified this by plugging in a custom Microcontroller programmer with drivers that are not present in  Linux distributions.

Well at least now i know the guest is working correctly... now, is there a way to make it detect said USB storage devices ? ( the ones i listed in my previous post)

---

