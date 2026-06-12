---
title: "compiled ffado &amp; jack in many ways but no way to let them work"
date: 2009-03-10
forum: Ubuntu Studio
---

### Post by aigore on 2009-03-10
Hello everybody,
I'm writing because I have some issues with ubuntu8.04 in compiling ffado drivers for my focusrite saffire audio interface.
I compiled the drivers and jack on my dell precision m6300 following offical ffado wiki, or guides on ubuntu forums.
When I run ./configure for jack, it tells me that I've already another jack installation in /usr/lib, so running the command with --prefix=/usr/lib succeds the compiling task, then with make commands I do the installation.
The fact is that, in qjackctl to run the new copy of jack I have to point at the folder where I have the sources (/home/../jack/jackd/jackd), so I figure out that I didn't compiled it well against the previous installation.
The problem is that, when I start jack compiled for ffado, it tries to boot up the device, but suddenly crashes.](*,)](*,)
I also tried to use a launchpad ppa precompiled for ffado and jack, but I obtain the same behaviour.
I noticed also that my ieee1396 chipset is not texas instruments, but a richo one, not very good for ffado driver. 
I tried to compile drivers and jack in another box with TI firewire chipset, and worked.
Also works on every pc with freebob drivers, but sometimes I lose sound response...](*,)](*,)

So I'm asking,
on my laptop is a matter of compiling jack against another (but in the other box succeded)?

How can I compile it over the preinstalled one?

Or it is a matter of bad chipset for ffado so I have to change it? may an express card with TI chipset can solve this and I'll be able to ork withmy firewire device? (like this [http://www.kraun.it/pages/products/datasheet.shtml?product_code=KR.G7&language=it](http://www.kraun.it/pages/products/datasheet.shtml?product_code=KR.G7&language=it) )

I notice also that jack could not run with RT enabled.
I attach the logs of ffado and jack
I hope somebody could help me, I really love linux audio software...
many many thanks

---

### Post by kayosiii on 2009-03-11
From memory the freebob driver works really well in 8.04... Will it did for me and my fp10

I know that ffado has more features but it seems to rely on newer versions of libraw1394 than is in 8.04 to work well.... and newer versions of jack - which means either fooling the compiled apps into thinking that they are running a different version of jack to what they are (and praying that he differences won't cause any damage) or compiling the apps form source. (I have done this with 8.10 since freebob is badly broken in 8.10 and 9.04)...


9.04 is a lot easier to test ffado on... if that is your aim.
Hope this helps

---

### Post by aigore on 2009-03-12
Thank you for your reply.
I'm trying to use freebob now in 8.04, but I've got some issues...
I'll post something about this later.
Thank you very much.
greets

---

