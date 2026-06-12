---
title: "easy to upgrade to next Ubuntu version?"
date: 2005-05-10
forum: Repositories &amp; Backports
---

### Post by tigerstripedcat on 2005-05-10
I'm looking to switch to ubuntu from mandriva.  I've heard (I think) that debian was always great in upgrading to a newer release via the command line--no downloading isos and burning them and reinstalling them.  Just a simple command and everything is upgraded.    Is the same true of ubuntu?

---

### Post by az on 2005-05-10
Yup.  The packages are downloaded by apt, the advanced package manager.

---

### Post by tigerstripedcat on 2005-05-11
Just for clarification.  I'm not talking about apt in general--I know how that works.  But with something like urpmi for mandriva you can upgrade the entire sytem with urpmi --auto-select, but I still have to download a new release from mandriva's site and then install it when a new release comes out  say moving from 10.1 to LE2005.  But with ubuntu, are you telling me I'll never have to download an iso ever again,  I just type something like

apt-get --upgrade

or something like that and it will be upgraded from 5.04 to 6.04?  By the way, what would the command be to upgrade the entire system to the newest version?

Sorry if this is redundent, I'm just making sure I was clear.

---

### Post by Psquared on 2005-05-11
[QUOTE=tigerstripedcat]Just for clarification.  I'm not talking about apt in general--I know how that works.  But with something like urpmi for mandriva you can upgrade the entire sytem with urpmi --auto-select, but I still have to download a new release from mandriva's site and then install it when a new release comes out  say moving from 10.1 to LE2005.  But with ubuntu, are you telling me I'll never have to download an iso ever again,  I just type something like

apt-get --upgrade

or something like that and it will be upgraded from 5.04 to 6.04?  By the way, what would the command be to upgrade the entire system to the newest version?

Sorry if this is redundent, I'm just making sure I was clear.[/QUOTE]

From what I know upgrading from Hoary to Breezy will be a ....... "breeze." :D

Going from Warty to Hoary required changing the sources.list and the apt-get update, then apt-get dist-upgrade. The next upgrade will, I have hear, be even easier.

---

