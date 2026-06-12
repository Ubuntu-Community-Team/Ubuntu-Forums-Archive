---
title: "Debian and Linux"
date: 2009-08-25
forum: The Cafe
---

### Post by jheaton5 on 2009-08-25
When Debian 6 (squeeze) is released it will no longer have the linux kernel.  It is being released with a modified FreeBSD kernel.  Will Ubuntu follow suit?

---

### Post by ubudog on 2009-08-25
Probably not.

---

### Post by Le-Froid on 2009-08-25
Where was this announced?

---

### Post by earthpigg on 2009-08-25
ummmm my understanding was they where going to start maintaining two releases each of the 5 million architectures they support: Debian GNU/Linux and Debian BSD.

Debian GNU/Linux for i386
Debian BSD for i386
Debian GNU/Linux for amd64
Debian BSD for amd64
etc

so, total of 10 million of releases instead of the previous 5.

which, btw, i think is awesome. Universal Operating System indeed.

---

### Post by achianese on 2009-08-25
Hopefully still relevant:

[http://linux.slashdot.org/article.pl?sid=09/04/05/222239](http://linux.slashdot.org/article.pl?sid=09/04/05/222239)

---

### Post by slakkie on 2009-08-25
> **jheaton5 said:**
> When Debian 6 (squeeze) is released it will no longer have the linux kernel.  It is being released with a modified FreeBSD kernel.  Will Ubuntu follow suit?

It is a side project, it will not replace the GNU/Linux kernel:
[http://wiki.debian.org/Debian_GNU/kFreeBSD](http://wiki.debian.org/Debian_GNU/kFreeBSD)

You will then have GNU/Linux and GNU/kFreeBSD.

---

### Post by Regenweald on 2009-08-25
Question though : Would the kernel-rolling infrastructure from BSD remain or would the Debian infrastructure replace it ? Creating a custom kernel in FreeBSD looks to be some simple goodness, if it were to remain I'd certainly cross my fingers and hope for Ubuntu adoption.

Unlikely? i know.

---

### Post by Bachstelze on 2009-08-25
> **Regenweald said:**
> Question though : Would the kernel-rolling infrastructure from BSD remain or would the Debian infrastructure replace it ? Creating a custom kernel in FreeBSD looks to be some simple goodness, if it were to remain I'd certainly cross my fingers and hope for Ubuntu adoption.

Unlikely? i know.

They would probably pick the kernel of some FreeBSD release and stick to it, so it wouldn't be "rolling" at all. FreeBSD releases only get security patches, nothing more.

Of course, unless you update your kernel sources to -CURRENT and build it yourself, but I have no idea how well that would work with Debien. Probably not well at all.

---

### Post by Regenweald on 2009-08-25
> **HymnToLife said:**
> They would probably pick the kernel of some FreeBSD release and stick to it, so it wouldn't be "rolling" at all. FreeBSD releases only get security patches, nothing more.

Of course, unless you update your kernel sources to -CURRENT and build it yourself, but I have no idea how well that would work with Debien. Probably not well at all.

I see, thanks. When i said rolling i actually meant custom kernel building, but your second statement answered that for me. I guess at some point I'll install FreeBSD for the experience. I know that some say a custom kernel does not necessarily offer much of a performance boost, but something has to be said of the learning experience :)

---

### Post by slakkie on 2009-08-25
I hope I can find my make-world.sh script again.. And my default LINT files..

---

### Post by tubasoldier on 2009-08-25
Debian also ships with a Hurd kernel.
[http://www.debian.org/ports/hurd/index](http://www.debian.org/ports/hurd/index)

LOL, RMS is still chugging away at an initial release of it.

---

### Post by SunnyRabbiera on 2009-08-25
Personally I might give Debian BSD a shot, BSD is a great family but i really dont like most of its variations.
Debian might give it the angle it needs.

---

### Post by Regenweald on 2009-08-26
I was just thinking, native zfs now ?

---

### Post by PurposeOfReason on 2009-08-26
So would it use ports then and just be another BSD variant?

---

### Post by Bachstelze on 2009-08-26
> **PurposeOfReason said:**
> So would it use ports then and just be another BSD variant?

No. Like everything Debian, it uses Apt.

---

