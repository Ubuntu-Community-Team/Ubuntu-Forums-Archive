---
title: "are they updated or not?"
date: 2007-01-01
forum: Repositories &amp; Backports
---

### Post by MCBTunes on 2007-01-01
I just had to go in and uppdate my repositories so I could install kubuntu-desktop with Ubuntu and now I'm trying to enable myself to program so I need to install stuff to compile etc.

I was told that to
 
install everything you need to compile stuff type:
sudo apt-get install build-essentials

You could be more specific:
sudo apt-get install g++

However I get the same error's that I thought I had resolved with the kubuntu-desktop instalation. (I'm very new to linux so I could be way off base though). Anyway.

I typed sudo apt-get install update

then sudo apt-get install build essentials and I got this.

michael@michael-udesktop:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essentials
michael@michael-udesktop:~$  

Is there easy simple way of resolving this where I do not risk mucking up my system?

Cheers,
Mike.

---

### Post by bapoumba on 2007-01-02
Hello,
build-essential, no "s" ;)

---

### Post by bernied on 2007-01-02
The package is called build-essential
no 's'

---

### Post by bernied on 2007-01-02
you make me look slow

---

### Post by bapoumba on 2007-01-02
> **bernied said:**
> you make me look slow
MCBTunes posted 10 hours ago, guess we both are :P

---

### Post by bernied on 2007-01-02
yeah, but that's in western australia - they're 10 hours ahead, right?

---

### Post by bapoumba on 2007-01-02
So this is why timing of a post is in "hours ago" or "days ago" or "weeks ago" and so on. "10 hours ago" means 10 plain hours before you and I posted, whatever timezone is defined in user profiles.
Unless I misunderstood the whole rationale ;)

Anyway, Happy New Year to you and to MCBTunes when he/she comes back :)

---

