---
title: "Plan 9, forgotten?"
date: 2010-06-06
forum: The Cafe
---

### Post by infestor on 2010-06-06
i wonder why plan 9 still has not reached to masses and increased in popularity? (considering it was released to public in 1995)
is it the lucent license or not much improvement over gnu/linux?

---

### Post by dragos240 on 2010-06-06
I don't know, lack of third party support maybe?

---

### Post by BoneKracker on 2010-06-06
It could theoretically make a come-back, given the surge in research into grid-like application architectures and its unique suitability.  However, what's more likely is that its features would find their way into other operating systems.  This feature migration has been going on (slowly) with Linux for quite some time.  Remember that Plan9 is a research project -- a prototype, if you will.

There has been one at least one attempt to commercialize it, the upside of which is the availability of a more desktop-like system called Inferno which is also available as Free software.  It's got a complete toolchain, an IDE, a reasonably modern browser, some games, etc.  They say it can run in as little a 1 MiB of RAM.

[http://www.vitanuova.com/inferno/](http://www.vitanuova.com/inferno/)

---

### Post by cb951303 on 2010-06-06
> 
The long view of history may tell a different story, but in 2003 it looks like Plan 9 failed simply because it fell short of being a compelling enough improvement on Unix to displace its ancestor. Compared to Plan 9, Unix creaks and clanks and has obvious rust spots, but it gets the job done well enough to hold its position. There is a lesson here for ambitious system architects: the most dangerous enemy of a better solution is an existing codebase that is just good enough.


resource: [http://www.faqs.org/docs/artu/plan9.html](http://www.faqs.org/docs/artu/plan9.html)

Plan 9 looks nice though. It would be interesting to see a modern desktop environment on it such as KDE or GNOME.

---

### Post by SoFl W on 2010-06-06
Has anyone done a dual (or tri) boot with Plan 9?  I see the window's boot loader option but didn't know if there was a grub boot loader option.  (I looked [here]("http://plan9.bell-labs.com/plan9/").)  If anyone has any suggestions or tips for tri-booting with grub, I would appreciate it. 

I would like to try this on my laptop as well as the desktop but the laptop cd/dvd drive isn't working so I would have to copy just the kernal images.

(I have a busy week and will not be able to research or do any of this until next week, so I will have to check back then)

---

### Post by cb951303 on 2010-06-06
does anyone know how Rio compares to Xorg?

---

### Post by Shining Arcanine on 2010-06-06
Plan 9 is used on Blue Gene supercomputers. Most systems are no where nearly as modular and distributed as the Blue Gene, so it in a sense is overkill for them.

---

### Post by jrothwell97 on 2010-06-06
> **infestor said:**
> i wonder why plan 9 still has not reached to masses and increased in popularity? (considering it was released to public in 1995)
is it the lucent license or not much improvement over gnu/linux?

It's because it's both overkill for the majority of users, and no attempt has been made to make a "user-friendly" distribution of it. (Such a task would be a *massive* undertaking.)

---

### Post by mmix on 2010-06-06
IMHO, anyhow, this seems to be one of reasons.

[quote="[Plan 9 from Bell Labs](http://en.wikipedia.org/wiki/Plan_9_from_Bell_Labs)"]
Plan 9 was a Bell Labs internal project from its start during the mid 1980s. In 1992, Bell Labs provided the first public release to universities. In 1995, a commercial second release version became available to the general public. In the late 1990s, Lucent Technologies, having inherited Bell Labs, dropped support for commercial interests in the project. In 2000, a non-commercial third release was distributed under an open source license. A fourth release under a new free software license occurred in 2002.
[/quote]

---

### Post by amauk on 2010-06-06
As far as I know, Plan9 was always supposed to be more of a concept than an actual product

It was Unix revamped for the distributed age
Unix++

Most of the concepts that made Plan9 different from traditional Unix have appeared already in other OSs (including Linux)

---

### Post by cb951303 on 2010-06-07
> **amauk said:**
> Most of the concepts that made Plan9 different from traditional Unix have appeared already in other OSs (including Linux)

Which ones? From what I read the most notable feature of Plan9 is that the filesystem does everything. I know everything is a file in Unix systems but with Plan 9 even windows, drawing surfaces, remote devices etc. are files. I don't know any other OS doing this.

---

### Post by szymon_g on 2010-06-07
> **cb951303 said:**
> Which ones?

/proc directory and Unicode- those are the most important things taken from Plan9 (or, rather 'inspired by' than 'taken from')

---

### Post by nrs on 2010-06-07
I think the world has pretty much settled on Windows, OS X, and GNU/Linux. If something is to replace them it would have to be inconceivably better.

---

### Post by amauk on 2010-06-07
> **cb951303 said:**
> Which ones? From what I read the most notable feature of Plan9 is that the filesystem does everything. I know everything is a file in Unix systems but with Plan 9 even windows, drawing surfaces, remote devices etc. are files. I don't know any other OS doing this.
[http://swik.net/v9fs](http://swik.net/v9fs)

---

### Post by BoneKracker on 2010-06-07
For those interested, there are articles and papers available, written in the last five years, that provide a good overview of Plan9 and discuss its legacy.  One need only search the Web.

---

