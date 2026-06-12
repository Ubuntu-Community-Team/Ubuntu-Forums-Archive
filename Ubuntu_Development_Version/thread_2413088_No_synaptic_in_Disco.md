---
title: "No synaptic in Disco?"
date: 2019-02-21
forum: Ubuntu Development Version
---

### Post by ping-wu on 2019-02-21
No synaptic in Disco repository?

---

### Post by deadflowr on 2019-02-21
It should be.
Is universe enabled?

---

### Post by Kris_M on 2019-02-21
I have found that sometimes when you try to install it it says it can't, but at the moment I have it installed - I think they fixed some stuff in background, or are fixing it. Just try install it from Ubuntu software every day or so.

---

### Post by ping-wu on 2019-02-21
I am running Disco on a persistent LiveUSB.

Guess my question should be: How do I add repositories in a persistent LiveUSB?

BTW, Disco runs really great on my HP 15" Envy 360 2-in-1 (AMD Ryzen 5 2500U).  Big, I mean BIG, improvements!!!

---

### Post by ping-wu on 2019-02-21
Just add this line: 

 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) disco multiverse
to the /etc/apt/source.list , no problem in installing synaptic, no difference from an installed system.

---

