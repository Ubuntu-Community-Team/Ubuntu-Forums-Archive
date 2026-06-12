---
title: "opening repos from synaptic pkg manager pulls 100% of both cores"
date: 2013-03-10
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-10
A fresh install of raring-desktop-i386.iso USB(non updated) and when opening repositories using synaptic it draws 100% from both cores on P4 2.66GHz Dual Core. updating now.

---

### Post by mc4man on 2013-03-10
on a dual core here it just uses 1 though they do switch once during the routine

Considering how long "Software and Updates" continues to take to open, (8-10 sec here),  the more cpu the merrier

---

### Post by ventrical on 2013-03-10
Thanks for the reply. No difference here after update. Still maxing both cores.

---

### Post by VinDSL on 2013-03-10
> **mc4man said:**
> on a dual core here it just uses 1 though they do switch once during the routine [...]
Exactly the same here!

I'm running a Netburst P4EE CPU -- a real oddball -- a Xeon MP server CPU, built on a Socket 478 form factor. LoL!

Anyway, it pegs "CPU1" @ 96% (when loading the PPAs) then switches to "CPU2" @ 100% (as it displays them).

Gotta say, since Conky is always in_my_face, this is nothing new, at least for me.

Synaptic has been acting this way for a l-o-n-g time, on this rig.  ;)

---

### Post by ventrical on 2013-03-11
I usually get the same thing on all my HT and Dual Core machines but this install seems a little different. I used an 80GB EIDE WD HD (new - almost), EXT4, Nvidia GeForce218/210. The only other thing different is that I chose nomodeset during setup. After the install there was acutally no video driver installed so I installed nvidia-current through terminal. Perhaps I will try nouveau, try nouveau. Hello .. is there am echo in here ! :) .. lol .. I just left that in there because I double dittoed 'try nouveau'.

---

### Post by ventrical on 2013-03-11
Nouveau solves the problem! Honestly , I don't get it. I can only assume that nvidia-current has something to do with this.

---

