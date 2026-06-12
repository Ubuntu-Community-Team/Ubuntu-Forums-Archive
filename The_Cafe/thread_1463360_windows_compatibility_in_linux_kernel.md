---
title: "windows compatibility in linux kernel"
date: 2010-04-26
forum: The Cafe
---

### Post by nerdy_kid on 2010-04-26
just ran into this: [http://www.longene.org/en/index.php](http://www.longene.org/en/index.php)
what do you all think of this?  or am i the only one who didn't know it existed...

---

### Post by dgw on 2010-04-26
That looks interesting. Too bad the documents and wiki are in Chinese, I wanted to read more about it.

---

### Post by Doctor Mike on 2010-04-26
Well the end of may is not far away. And for my next trick I'll pull a rabbit out of my hat.

It sounds like a good thing, or is a unified open source OS that may become universally compatible with software bad for some and not others?

---

### Post by renkinjutsu on 2010-04-26
Wow that's amazing!
I didn't know about it either, but i can't wait to give it a try.... someday

---

### Post by Khakilang on 2010-04-26
It is always interesting when MS notice Linux as a OS that need to be reckon with. They simply cannot ignore Linux since the user are growing especially form the server end.

---

### Post by nerdy_kid on 2010-04-27
> **Doctor Mike said:**
> Well the end of may is not far away. And for my next trick I'll pull a rabbit out of my hat.

It sounds like a good thing, or is a unified open source OS that may become universally compatible with software bad for some and not others?

well the only obvious con about the whole thing is that the kernel would be vulnerable to viruses.

---

### Post by Doctor Mike on 2010-04-27
> **nerdy_kid said:**
> well the only obvious con about the whole thing is that the kernel would be vulnerable to viruses.Not sure if the kernel would be vulnerable or just the applications. The [http://www.longene.org/en/download.php](http://www.longene.org/en/download.php) page has Ubuntu kernels available for download. Wonder if I should try to do a test infection. Would need a test virus (etc.) that is basically 'harmless' to do that though. Gave up playing with virus' back when they were basically harmless (your pc is stoned).

Just curious if anybody has tried the downloads?

---

### Post by nerdy_kid on 2010-04-27
the download server isnt responding over here :(
at least not for the ubuntu packages

---

### Post by Doctor Mike on 2010-04-27
> **nerdy_kid said:**
> the download server isnt responding over here :(
at least not for the ubuntu packages
Working for me, you must be on the wrong end of the pond...:)

---

### Post by Jpenguin on 2010-04-27
I'm notn sure that's a good idea
people might stop programming for linux

---

### Post by Doctor Mike on 2010-04-27
> **Jpenguin said:**
> I'm notn sure that's a good idea
people might stop programming for linuxNo I think it might bring MS programmers into the fold... assuming most are not already testing the waters...

---

### Post by doas777 on 2010-04-27
it wouldn't be unprecedented. last year MS contributed some code to the kernel, that allows windows virtual guests to run better on linux hosts. 

now, what level of compatibility are we talking about? w32 compilers and runtime, or system APIs?

---

### Post by oobuntoo on 2010-04-28
> **dgw said:**
> That looks interesting. Too bad the documents and wiki are in Chinese, I wanted to read more about it.

Here you go:

[http://en.wikipedia.org/wiki/Linux_Unified_Kernel](http://en.wikipedia.org/wiki/Linux_Unified_Kernel)

---

### Post by xtremesupremacy3 on 2010-06-26
Firstly, most people seem to think that this will open Ubuntu up to viruses, but this isn't really true.

I mean, most of us that use Ubuntu as the main OS only turn to wine or longene to make programs we know work. Most viruses on Windows come from unknown sources so the chances we install them will be very slim. And even then, we have built in security that requires root to access the kernel, so therefore it makes it even less. But don't be under the impression linux has no viruses now, you would be mistaken, but I can quite confidently say it will be difficult to virus yourself if you have longene unless you start downloading and installing and allowing everything you see.

The deb packages are very awkwardly made as it will give you an error with the kernel install when trying to install that deb file. This is not your fault, I remember it being something to do with permissions. I can't remember how I went around that but anyway I managed to install both packages.

And then....it went wrong, maybe it was my laptop, maybe it was lucid or maybe the debs...I don't know, but loading that kernel caused me to be stuck at login. All looked normal, but my keyboard didn't respond, my mouse and touchpad didn't respond. I couldn't do anything. For me, it was a huge failure

Arthur

---

### Post by Austin25 on 2010-06-26
If this is vulnerable to the viruses, then there would be no point in this due to wine not being vulnerable to viruses. I think I'll just stick to using wine.

---

