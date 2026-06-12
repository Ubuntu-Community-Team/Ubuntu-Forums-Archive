---
title: "Gentoo on 1.66GHz CPU?"
date: 2011-03-15
forum: The Cafe
---

### Post by armageddon08 on 2011-03-15
Hi everybody.

I've a laptop with a 1.66 GHz Core Duo CPU and 1.5GB RAM. Is it enough to build Gentoo on it? And if I do end up building it, how long is it gonna take to compile stuff on it?

---

### Post by Khakilang on 2011-03-15
I am not familiar with Gentoo but base on your spec it is good enough for any Distro.

---

### Post by wojox on 2011-03-15
Build as in compile everything yourself, ya but it will take time and I mean time :P

---

### Post by LowSky on 2011-03-15
Gentoo has been around since 2002.. During that time most users had Pentium 3, Pentium 4 and Celeron's. Most just above 1GHz. Most users didn't even have 1GB of RAM.

You Core Duo is well above those old chips.

Remember Gentoo can be as resource hungry or light as you wish.

---

### Post by 3Miro on 2011-03-16
Gentoo will compile without any trouble, the only issue is "How long will it take?" The answer here depends not only on the CPU, but also on the HDD, RAM, Internet connection ...

I can install Gentoo on my Laptop over a weekend. The Laptop is Pentium Dual Core 2.4Ghz, 3GB of RAM, 5400RPM HDD. When I say install, I mean install Gnome with OpenOffice, media players and codecs, Firefox + Chromium, LaTeX and basically a stable working system. KDE would take longer. I am also very familiar with the Gentoo installation procedure (having doe it several times on my 4-core desktop), if you are unfamiliar with Gentoo, then reading manuals a such would take much longer.

If you know Gentoo, I would guess you would need 4 days to compile a functioning system. If you are not familiar with Gentoo, give it couple of weeks as things will go amiss the first time.

---

### Post by Dragonbite on 2011-03-16
It will be a helluva lot faster than when I was running Gentoo on my P3 @ 500MHz w/128 MB of RAM and downloading everything over dial-up (whyyy did I do that to myself.. oh, yeah! I was learning Linux!)

Yes, I took many overnights of downloading to get all of KDE downloaded and installed (twice!)

That's why I came to Ubuntu; easy, simple and I didn't worry about telling my wife in the morning before I go to be "uh, something I did last night broke the computer, but I'll fix it tonight!". So she's happy I found Ubuntu too! ;)

---

### Post by RiceMonster on 2011-03-16
Going to take a while, as in you might be leaving your computer compiling over night. It might be worth it, though, if you want to be able to brag about how your computer launches vim 0.1 milliseconds faster than everyone else.

---

### Post by armageddon08 on 2011-03-16
So, is it not worth it? What is the educational value of getting a gentoo system up and running compared to one with arch(which I've done) ?

---

### Post by 3Miro on 2011-03-16
> **armageddon08 said:**
> So, is it not worth it? What is the educational value of getting a gentoo system up and running compared to one with arch(which I've done) ?

Arch has a "next-next-finish" installer which takes you to a base CLI system. Gentoo has to do everything manually step by step, installing the base system layout and setting up even the most basic services (like vixie-cron and syslog).

Arch has a pre-build kernel that works on almost all Linux supported hardware, in Gentoo you have to build your own kernel knowing what you need and don't need in terms of modules (that alone took me 4 attempts to figure it out).

---

### Post by gnomeuser on 2011-03-16
Bah chickens, back when I was a Gentoo user I built from stage 1 (if Gentoo still calls it that, as close to scratch as possible backen at least) on an 386 with 128MB of ram.

---

### Post by NightwishFan on 2011-03-16
> **gnomeuser said:**
> Bah chickens
:popcorn: Hahaha.

@op It will take some time (days) to do. Have fun. :P

---

### Post by gnomeuser on 2011-03-16
> **NightwishFan said:**
> :popcorn: Hahaha.

@op It will take some time (days) to do. Have fun. :P

I learned a lot running Gentoo, the build system at least back then was insanely easy to master sufficiently to make major changes. It encouraged me to learn a lot.

I haven't been involved with Gentoo in years though, I don't know if it still retains those qualities.

Yeah the initial install is likely going to be slow, slower than a binary distribution and it won't initially feel any better. You have to invest time in learning how the system works and what your computer can do to start benefiting from the flexibility Gentoo style systems bring to the equation.

---

### Post by Dragonbite on 2011-03-16
> **gnomeuser said:**
> Bah chickens, back when I was a Gentoo user I built from stage 1 (if Gentoo still calls it that, as close to scratch as possible backen at least) on an 386 with 128MB of ram.

Uphill... both ways! :lolflag:

---

### Post by mips on 2011-03-16
It will work fine on your cpu but I have no idea how long it will take. I played with Gentoo back in the day but the compiling time is just not worth it for me. I'd rather have Arch. And I did this on a Prescott based Celeron.

---

### Post by Dustin2128 on 2011-03-16
Heh, gentoo. [http://funroll-loops.info/](http://funroll-loops.info/)

---

### Post by spupy on 2011-03-16
I used to use Gentoo on 1.4 GHz Celeron CPU with 512MB of RAM. It was a lot more faster than stock Ubuntu back then (9.x I think) and faster than Arch and Debian.

From start to a fluxbox environment with the necessary apps took me about 2 days. Mostly compiling on and off, but I spent a lot of time reading, since I was still a linux noob. I'd say a day for reading and initial setup, then leave it overnight to compile. The next day complete the compilation if it hasn't finished, and tweak the finished system to make it usable to your likings (this might take a while as well).


If you are feeling more adventurous and have another more powerful computer you can use distcc. With it you can distribute the compile process across several machines. In the Gentoo documentation there is an article on installing using distcc.

---

