---
title: "Programs that take the longest to compile."
date: 2009-09-17
forum: The Cafe
---

### Post by dragos240 on 2009-09-17
Just a random topic. I think VLC and OpenOffice take the longest.

---

### Post by juancarlospaco on 2009-09-17
*KDE4.x from sources... *
:)

---

### Post by tcoffeep on 2009-09-17
> **juancarlospaco said:**
> *KDE4.x from sources... *
:)

The worst experience I ever had was installing KDE3 on Gentoo. And after a week, upgrading to KDE4.

---

### Post by Bachstelze on 2009-09-17
> **tcoffeep said:**
> The worst experience I ever had was installing KDE3 on Gentoo. And after a week, upgrading to KDE4.

So you weren't there for the Big Xorg Migration (6 to 7)?

---

### Post by tcoffeep on 2009-09-17
> **Bachstelze said:**
> So you weren't there for the Big Xorg Migration (6 to 7)?

I was with Arch for the Xorg upgrade that caused a lot of problems. (can't be sure how long ago that was.)

---

### Post by scragar on 2009-09-17
> **tcoffeep said:**
> The worst experience I ever had was installing KDE3 on Gentoo. And after a week, upgrading to KDE4.

Why? I've never really understood why anyone would choose KDE with gentoo anyway, I mean the computing time taken to compile it is so huge it's painful to think about, let alone try, to do that yourself, for every single upgrade?

The only thing I've ever seen take longer to compile is android, but then android's an entire OS, KDE is just a WM.

---

### Post by PurposeOfReason on 2009-09-17
> **Bachstelze said:**
> So you weren't there for the Big Xorg Migration (6 to 7)?
I wasn't there for that, but GCC upgrades are far worse.

---

### Post by tcoffeep on 2009-09-17
> **scragar said:**
> Why? I've never really understood why anyone would choose KDE with gentoo anyway, I mean the computing time taken to compile it is so huge it's painful to think about, let alone try, to do that yourself, for every single upgrade?

The only thing I've ever seen take longer to compile is android, but then android's an entire OS, KDE is just a WM.

It was my first time using gentoo. I underestimated :>

I now use dwm.

---

### Post by rifak on 2009-09-17
i haven't done any compiling of window managers, but what i have done that takes the longest is a physics research programming environment called ROOT. the 64 bit version was a mess to try and get working and took a long time. its a wonderful tool though after it's finished.

---

### Post by kevdog on 2009-09-17
and I thought pidgin took a while to compile??? Guess I was wrong!

---

### Post by Firestem4 on 2009-09-17
Now how long are we talking here..minutes? hours? I compiled Nagios from source...small program but took nearly 30 minutes to compile on the machine I was using. (Dell XPS M1210)

---

### Post by ~sHyLoCk~ on 2009-09-17
> **kevdog said:**
> and I thought pidgin took a while to compile??? Guess I was wrong!

Not that long, Xulrunner takes a long time. Openoffice takes  day. :D

---

### Post by scragar on 2009-09-17
> **Firestem4 said:**
> Now how long are we talking here..minutes? hours?

> An```
emerge kde
```took round about 2 days on a G4/400 with 960MB RAM. But there was no qt or any other stuff installed so far, just the base system and xfree (which took round about 2 and a half hours) 
Days.

---

### Post by kk0sse54 on 2009-09-17
I've compiled KDE4 loads of times and it isn't too bad although it takes a number of hours. The worst for me has to be open office although I hate gcc and firefox updates.

---

### Post by ~sHyLoCk~ on 2009-09-17
> **C!oud said:**
> I've compiled KDE4 loads of times and it isn't too bad although it takes a number of hours. The worst for me has to be open office although I hate gcc and firefox updates.

Firefox update is still ok, but gcc update = 1st gcc compile takes a few hours and then to ensure links are intact you might have to do ```
emerge -ev system && emerge -ev world && revdep-rebuild
``` which is gonna take a few days depending on your number of packages. :popcorn:

---

### Post by scragar on 2009-09-17
> **~sHyLoCk~ said:**
> Firefox update is still ok, but gcc update = 1st gcc compile takes a few hours and then to ensure links are intact you might have to do ```
emerge -ev system && emerge -ev world && revdep-rebuild
``` which is gonna take a few days depending on your number of packages. :popcorn:

Yet another reason to invest in your own cluster of super computers... :p

---

### Post by MaxIBoy on 2009-09-17
Yeesh, and I thought the kernel was bad...

---

### Post by kk0sse54 on 2009-09-17
> **~sHyLoCk~ said:**
> Firefox update is still ok, but gcc update = 1st gcc compile takes a few hours and then to ensure links are intact you might have to do ```
emerge -ev system && emerge -ev world && revdep-rebuild
``` which is gonna take a few days depending on your number of packages. :popcorn:

In all honesty when I used gentoo, unless it was a major update rather than rebuilding my entire system I generally only rebuilt libtool.

---

