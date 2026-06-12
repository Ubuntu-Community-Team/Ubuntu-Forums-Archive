---
title: "Request: Clearlooks 0.6.2"
date: 2005-07-01
forum: Ubuntu Backports
---

### Post by MadMan2k on 2005-07-01
its already in debian-sid and it looks better :)

---

### Post by Slo Mo Snail on 2005-07-02
I'll package it when it hits breezy ;)

---

### Post by rpgcyco on 2005-07-05
According to [this](http://packages.ubuntu.com/breezy/gnome/gtk2-engines-clearlooks) page, it's not in Breezy, but I updated to 0.6.2 this morning on my Breezy running PC. :)

- Rpg Cyco

---

### Post by Mez on 2005-07-05
It is in breezy now.... It just hasnt been shoved over onto p.u.c

---

### Post by Slo Mo Snail on 2005-07-06
Uploaded for x86 a few minutes ago... please test it

---

### Post by bored2k on 2005-07-06
[QUOTE=Slo Mo Snail]Uploaded for x86 a few minutes ago... please test it[/QUOTE]
 I'm not sure if its just my imagination, but after applying the Clearlooks found my box feels slightly snappier.

Imagination or not, everything's going great here :D.

---

### Post by Slo Mo Snail on 2005-07-06
That's possible as they fixed a memleak (and I had the same feeling after updating from 0.5 to 0.6.1 ;) )

---

### Post by bored2k on 2005-07-06
[QUOTE=Slo Mo Snail]That's possible as they fixed a memleak (and I had the same feeling after updating from 0.5 to 0.6.1 ;) )[/QUOTE]Great :D
 BTW, is the sun-jre package in staging ok to use ? I made my own .04 package so I still haven't upgraded to the onme in UBP.. ?

---

### Post by Slo Mo Snail on 2005-07-07
Well I use the sdk package in staging and it works for me ;)

---

### Post by Virtual DarKness on 2005-07-16
I can't find this package in backports anyway I've backported clearlooks 0.6.2 using the .py script provided by jdong with the breezy src repo and seems to work well..

jdong let me know if I should send it to you..

bye,
Giovanni.

p.s.
i've also backported gnome-art but it returns an error related to ruby and doesn't start...

**edit**:
solved both.. clearlooks is in the staging repository and the version of gnome-art that can be found on 

[http://packages.ubuntu.com/breezy/gnome/gnome-splashscreen-manager](http://packages.ubuntu.com/breezy/gnome/gnome-splashscreen-manager)
[http://packages.ubuntu.com/breezy/gnome/gnome-art](http://packages.ubuntu.com/breezy/gnome/gnome-art)

works on hoary too, just install also the package librexeml-ruby1.8 ;)

---

