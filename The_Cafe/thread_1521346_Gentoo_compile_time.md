---
title: "Gentoo compile time"
date: 2010-06-30
forum: The Cafe
---

### Post by sandyd on 2010-06-30
Does anyone know how long it would take to compile a complete Gentoo with a compilete KDE installation? (from scratch)

---

### Post by dragos240 on 2010-06-30
> **carlee said:**
> Does anyone know how long it would take to compile a complete Gentoo with a compilete KDE installation? (from scratch)

I do! First hand! I used KDE on gentoo! It took me about a week of compiling and configuring, and about 12-15 hrs for KDE to compile. Not that long IMO.

---

### Post by Yes on 2010-06-30
Of course, it's going to vary greatly depending on your machine's specs...

---

### Post by dragos240 on 2010-06-30
It'll vary, but not too great. It should be around that time for the average computer with a dual core processor and 2gb or ram (my 2007 desktop).

---

### Post by sandyd on 2010-06-30
hmm... Im using a 2.2 GHz core2duo w/ 8GB ram

---

### Post by dragos240 on 2010-06-30
> **carlee said:**
> hmm... Im using a 2.2 GHz core2duo w/ 8GB ram

Should take about 4 times less than 1.5 weeks XD. Can I have your computer please?

---

### Post by Shazzam6999 on 2010-06-30
> **dragos240 said:**
> It'll vary, but not too great. It should be around that time for the average computer with a dual core processor and 2gb or ram (my 2007 desktop).
It can vary pretty greatly, took 12 hours on my Pentium 4 laptop, 2.5 hours on a quad core. Should take you like 6-8 hours with your processor. Start it before you go to sleep or make a drinking game out of it.

---

### Post by NMFTM on 2010-06-30
> **dragos240 said:**
> It'll vary, but not too great.
I haven't compiled very many things. About the only thing I sometimes need to compile is some kind of virtualization kernal module for Virtualbox when I update it and it doesn't work for some reason. Why is it that when I'm compiling I don't see my CPU meter working very hard? Wouldn't that be a CPU intensive task?

---

### Post by dragos240 on 2010-06-30
> **NMFTM said:**
> I haven't compiled very many things. About the only thing I sometimes need to compile is some kind of virtualization kernal module for Virtualbox when I update it and it doesn't work for some reason. Why is it that when I'm compiling I don't see my CPU meter working very hard? Wouldn't that be a CPU intensive task?

Both my processors  are at 95% when I'm compiling, no idea.

---

### Post by Noz3001 on 2010-06-30
Takes about 13 hours on my laptop with AMD Turion64 X2 (2Ghz) for a minimal usable Xfce4 desktop. KDE, probably a life time.

---

### Post by sandyd on 2010-07-01
what should I type in during the compile options section: (make.conf) for my core2duo?

---

### Post by sandyd on 2010-07-01
and is there a way to make it compile with two threads (make -j2) by default?

---

### Post by sandyd on 2010-07-02
And I just realized something.
I can simply chroot into gentoo, copy the resolv.conf over, and then I can run ubuntu, and compile gentoo at the same time.:popcorn:

---

### Post by GlazedDonut on 2010-07-02
> **carlee said:**
> what should I type in during the compile options section: (make.conf) for my core2duo?

I always just use -march=native so I dont have to worry about if i set the processor architecture right.

---

