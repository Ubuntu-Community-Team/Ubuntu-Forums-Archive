---
title: "How to disable that Amazon thing"
date: 2012-11-26
forum: Security
---

### Post by MrIceBlock on 2012-11-26
Hi, first of all Lubuntu doesn't have that amazon thing correct? 

And in Ubuntu 12.10 how do I disable it? And if I disable it, nothing from computer is transmitted anywhere correct? 

I think that whole search thing is a bad privacy decision personally.

---

### Post by Lars Noodén on 2012-11-26
It's the package 'unity-lens-shopping ' and it can be removed.  It's not included in Lubuntu.  Without it, your local searches will not be forwarded off your computer.  

I don't think there is much else that sends information.  There might be '[popularity-contest](http://popcon.debian.org/)' which reports back about which packages are installed and a limited amount of info about their use.

---

### Post by MrIceBlock on 2012-11-26
> **Lars Noodén said:**
> It's the package 'unity-lens-shopping ' and it can be removed.  It's not included in Lubuntu.  Without it, your local searches will not be forwarded off your computer.  

I don't think there is much else that sends information.  There might be '[popularity-contest](http://popcon.debian.org/)' which reports back about which packages are installed and a limited amount of info about their use.
So if I remove that package it completely removes that amazon search?

---

### Post by cariboo on 2012-11-26
An even easier way is to turn of the search in System Settings->Privacy. IF you are still worried, you can use [Wireshark]("http://askubuntu.com/questions/74059/how-do-i-run-wireshark-with-root-privileges") to check what packets are being sent/not sent to Canonical.

---

