---
title: "Problem with Jack"
date: 2009-03-22
forum: Ubuntu Studio
---

### Post by clamsd101 on 2009-03-22
Well, I wanted to make some music so I installed ubuntustudio-desktop. That worked except for numpy, which I already installed for a game. Since jack requires it for a reason unknown to me I can't use jack and I can't use a lot of my software. Any fix? Thanks.

---

### Post by clubsoda on 2009-03-31
If you mean jackd, I have that installed.  I've already removed ubuntustudio-desktop and can remove python-numpy at any time without losing jackd.
You could try removing numpy (and the game), reinstalling ubuntustudio and then adding the game back.

---

### Post by Stochastic on 2009-03-31
ahh, name confusion.  JACK audio server is not the same as the jack package in the repos:
[http://packages.ubuntu.com/hardy/jack](http://packages.ubuntu.com/hardy/jack)
[http://packages.ubuntu.com/hardy/jackd](http://packages.ubuntu.com/hardy/jackd)
Jack - yet another CD ripper grabbed the jack name before the JACK audio server could, so JACK now uses jackd.

Jackd does not require any pythonness so there shouldn't be any conflicts.

---

