---
title: "Linux system from scratch"
date: 2011-06-15
forum: The Cafe
---

### Post by UART16550 on 2011-06-15
Has anyone ever built a Linux system from scratch? If so, would you please tell me the pro's and con's to it.

I figure one con will be that you have to manually update and keep in the loop of all updates for things on your system.

---

### Post by Bandit on 2011-06-15
> **UART16550 said:**
> Has anyone ever built a Linux system from scratch? If so, would you please tell me the pro's and con's to it.

I figure one con will be that you have to manually update and keep in the loop of all updates for things on your system.

Pros, your awesome..
Cons, you wasted 5 days of your life.


Here this will ease the pain.. This what I used before and it works well.
[http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

---

### Post by 3Miro on 2011-06-15
It is a good learning experience, but you will not be able to build and maintain a fully functional system. Maintenance is not a one-man-project.

If several of you get together, then you can do it of course.

---

### Post by smellyman on 2011-06-15
> **Bandit said:**
> Pros, your awesome..
Cons, you wasted 5 days of your life.


Here this will ease the pain.. This what I used before and it works well.
[http://www.linuxfromscratch.org/lfs/](http://www.linuxfromscratch.org/lfs/)

haha.  that's about right.

---

### Post by handy on 2011-06-15
Every now & then I consider committing to a LSF build, but I always seem to find something else that has a higher priority.

Perhaps one day I will do it...

I know that if/when I do, do it, that the result won't be as good as the system that I am currently using & that the whole LSF experience will basically be a VERY intense learning experience. (for me anyway)

---

### Post by prodigy_ on 2011-06-15
LFS is good if you want to study Linux in depth for whatever reason. But if you need a source-based distro for a production system, use Gentoo.

---

### Post by RiceMonster on 2011-06-15
> **bandit said:**
> pros, **none, unless you had nothing better to do**
cons, you wasted 5 days of your life.

ftfy

---

### Post by handy on 2011-06-15
> **prodigy_ said:**
> LFS is good if you want to study Linux in depth for whatever reason. But if you need a source-based distro for a production system, use Gentoo.

I'm an Arch user, which means that all but those packages that come via AUR are binary, which in comparison to doing it the Gentoo way means that my daily system upgrade mostly (sometimes there are lots of packages) happens really quite quickly.

Having said that, my ISP, which is always the users' choice no.1 in Oz, uses Gentoo on all their servers on which they run multiple virtual machines.

So I say courses for horses. :)

---

### Post by prodigy_ on 2011-06-15
> **handy said:**
> I'm an Arch user, which means that all but those packages that come via AUR are binary, which in comparison to doing it the Gentoo way means that my daily system upgrade mostly (sometimes there are lots of packages) happens really quite quickly.
I hear you. :) As long as your have sources for everything you need (or want) to customize, it doesn't really matter if the rest comes in binary form.

There's one little nuance re. optimization though. Gentoo allows you to specify compiler options for everything. If you know what you're doing you can get some extra performance for free.

---

### Post by handy on 2011-06-15
I'm very far from being anti Gentoo. I am certainly close to being a lazy system user though... :)

---

### Post by mips on 2011-06-15
> **prodigy_ said:**
> 
There's one little nuance re. optimization though. Gentoo allows you to specify compiler options for everything. If you know what you're doing you can get some extra performance for free.

If I'm not mistaken you can do that with arch as well for everything that resides in AUR.

---

### Post by giddyup306 on 2011-06-15
Funny I was going to make this same thread...

I got about a chapter into the LFS book, and it already assumes you know a lot about Linux.  Like moving files with the terminal.  It then said to read some other book.  That was the end of that for me.  It said outright that you probably won't get any help online.

---

### Post by handy on 2011-06-15
> **mips said:**
> If I'm not mistaken you can do that with arch as well for everything that resides in AUR.

Meaning PKGBUILD configuration?

Which gives you over 30,000 packages to play with.

Which makes me glad that I don't know how to play with them in that there PKGBUILD way, as my obsessive compulsive nature would cause me no end of trouble under those circumstances...

---

### Post by mips on 2011-06-15
> **handy said:**
> Meaning PKGBUILD configuration?

Which gives you over 30,000 packages to play with.

Which makes me glad that I don't know how to play with them in that there PKGBUILD way, as my obsessive compulsive nature would cause me no end of trouble under those circumstances...

lol.

Yes. You can set your compiler environment to optimise for your cpu. I recall one guy on the arch forums installing a minimum base system and then building all his packages from scratch with optimised compiler flags. Why I don't know, he might as well have just used Gentoo. Not my cup of tea, I don't hate Gentoo or source distros but I don't see myself ever trying one again.

---

### Post by sffvba[e0rt on 2011-06-15
> **giddyup306 said:**
> Funny I was going to make this same thread...

I got about a chapter into the LFS book, and it **already assumes you know a lot about Linux.  Like moving files with the terminal.**  It then said to read some other book.  That was the end of that for me.  It said outright that you probably won't get any help online.

Yes... I wouldn't recommend trying LFS if moving files from terminal is considered knowing a lot about Linux :p


404

---

### Post by handy on 2011-06-15
I like using Arch because it is so easy, I have become so lazy when it comes to computer maintenance (& I used to do it for others professionally!). 

I don't want to do any computer maintenance unless it is inescapable.

My simple daily maintenance routine is typing "aur" into the Terminal, "aur" being an alias in ~/.bashrc as follows:

```
### packer -Syu --aur  - packer being a yaourt replacement:
 
alias aur="packer -Syu"
```

& that's that. 

If anything unusual crops up, I read about it in the Arch wiki or forum & do what I'm told (thankfully it hardly ever happens).

I really like not having to think too much about computers these days... :)

*"Time has fallen asleep in the afternoon sunshine..."*

Kind of wraps it up for me.

---

### Post by giddyup306 on 2011-06-15
> **not found said:**
> Yes... I wouldn't recommend trying LFS if moving files from terminal is considered knowing a lot about Linux :p


404

Point is most people that use Ubuntu desktop and aren't IT professionals, or use servers don't move files that way.  At least I don't.  Nautilus FTW.

---

### Post by BrokenKingpin on 2011-06-15
Instead of going with something like LFS, you would be better off doing a Debian net-install or an Arch install (or even a Ubuntu mini.iso install). With these you basically build your system up the way you want... and in the process learning a lot about all the components that make up a fully function Linux desktop.

---

### Post by manzdagratiano on 2011-06-16
> **handy said:**
> I like using Arch because it is so easy, I have become so lazy when it comes to computer maintenance (& I used to do it for others professionally!). 


+1

People say Arch is targeted for advanced users, but I think save for the installation it really is the easiest system for daily use. I spend more time on Arch than on Ubuntu nowadays because of the invisible window bug with Compiz in Natty - I will pull my hair out if I keep running into it at work!

I have a Gentoo install alongside the other four on this machine, and the very thought of logging in and updating it, which may take hours upon hours, petrifies me!!! It therefore sits there for long periods of dormancy :)

---

