---
title: "Yay! Removing Evolution != removing gnome components"
date: 2006-03-17
forum: The Cafe
---

### Post by lordofkhemenu on 2006-03-17
Not sure if it's a Gnome 2.14 thing, a Dapper Drake thing or just something that the developers did, but I was ***freakin thrilled***  to find out that when I opted to remove Evolution and the evolution-data-server thing (and various other Evolution-related debs) that no gnome components were to be taken out with it.
Whomever is responsible for this, **[COLOR=Red]THANKYOU[/COLOR] [COLOR=Blue]THANKYOU[/COLOR] [COLOR=Green]THANKYOU[/COLOR]**.

It's not that I don't like Evolution - it's an awesome program/suite - I just have no need for it and am just the type of person who doesnt see a point of having it installed if I'm never gonna use it.

---

### Post by WillemM on 2006-03-17
Thats good to hear, I was looking for someone to confirm this for me. 
Will start removing evolution right away, I dont use it and its only taking up space this way.

---

### Post by jc87 on 2006-03-17
Funny thing , i´m getting tired of thunderbird , and thinking in testing evolution in the near future (if for nothing else , Gnome integration is always nice).

---

### Post by mishranurag on 2006-03-17
It would be great to see if the user gets the flexibility to associate Time Applet in UBUNTU to Mozilla Calendar, or the ics calendar file could be read by Evolution so that I can see my appointments in the evolution calendar.

Thank You for having the flexibility to remove Evolution, for those who don't need it :)

Anurag

---

### Post by Kerberos on 2006-03-17
To be honest its always confused me why OS's feature SMTP clients so prominantly.  Very few people, apart from enterprise customers, actually use them and they seem to cause more harm than good.  I dont see why they have such a special place on the desktop - especially on LiveCD's where its about as useful as a handbrake on a canoe.

---

### Post by K.Mandla on 2006-03-17
So how can I do that cleanly? Just *sudo apt-get remove evolution*? I'd also like to get rid of that unnecessary weight.

---

### Post by sudomania4 on 2006-03-17
The same thing happened to me in breezy, so it's not just dapper. I was installing thunderbird, and decided to get rid of evolution. BIG MISTAKE! I ended up reinstalling things like gnome-panel and gnome-terminal using synaptic. Later, i tried to upgrade to Dapper by changing my sources.list, then sudo apt-get update, then sudo apt-get dist-upgrade. But it said something about evolution incoming mail alert unable to update, and after a reboot, totally hosed my system. I ended up reinstalling Breezy from cd, which would have resolved any evolution issues. whatever.

So yeah, it's integrated. = )

---

### Post by K.Mandla on 2006-03-17
Wait, I thought the point of the OP was that evolution could be removed from Dapper without too much hassle. Or am I confused again? :-k

---

### Post by Bandit on 2006-03-17
That sounds great. Now if they will just do multimedia apts like that..

---

### Post by sudomania4 on 2006-03-17
[QUOTE=]Wait, I thought the point of the OP was that evolution could be removed from Dapper without too much hassle. Or am I confused again?[/QUOTE]
Yeah, that's what I thought, I wish it was that easy. Is this whole thread sarcasm? Or, are there really people that are happy that their choice of email app is taken away? Do these people enjoy the damage and removal of vital system components this issue causes? Ahh!

---

### Post by NeoChaosX on 2006-03-18
sudomania: Sounds like the OP did a clean install of Dapper. Perhaps you carried over a setting that requires Evolution to be installed when you just dist-upgraded. Try doing a clean install and see if removing Evolution works.

---

### Post by klahjn on 2006-03-18
I was confused at first, but i think i've gathered what's going on.  The ones that are having problems tried to remove evolution in breezy badger (5.10).  Once the system was upgraded to gnome 2.14 they were fine on the dapper release.  But if they removed it before this release (pre-dapper w/ latest updates) then they had problems when removing and hosed thier system when upgrading to dapper.

---

### Post by lordofkhemenu on 2006-03-19
[quote=klahjn]I was confused at first, but i think i've gathered what's going on.  The ones that are having problems tried to remove evolution in breezy badger (5.10).  Once the system was upgraded to gnome 2.14 they were fine on the dapper release.  But if they removed it before this release (pre-dapper w/ latest updates) then they had problems when removing and hosed thier system when upgrading to dapper.[/quote]
That's exactly what happened. I was running Breezy, upgraded to Dapper, THEN removed Evolution and discovered the clean removal vs the removal of all that is gnome-ish.

---

### Post by rama on 2006-04-25
I upgraded from breezy to dapper and I am still not able to remove evolution without removing ubuntu-desktop. Is there a work around?

---

