---
title: "KDE hardware requirements blown out of proportion"
date: 2006-06-04
forum: The Cafe
---

### Post by qalimas on 2006-06-04
[http://linuxreviews.org/software/desktops/](http://linuxreviews.org/software/desktops/)

Now, maybe it's just me, but that confuses me a little, and I worry that it'll turn up in too many Google results and give people the wrong idea.

The article says KDE needs 512MB of RAM.  I have 724MB in my laptop, but I have a Karama theme monitoring my system, I've never seen it use over 256MB, not even while I'm doing a lot of multitasking.  The same goes for Gnome.  And my friend had his Xfce install down to using only 30MB, 50 or so once Gaim, Firefox, XMMS and the like were running...

I just though I'd get clarification of what they suggest so much RAM for, if anyone knows or has any ideas? :-k

---

### Post by stimpack on 2006-06-04
Prima BS article. Not least Gnome and KDE with the current versions have completly identical ram usage. Anyone can test that if they have both installed.

---

### Post by aysiu on 2006-06-04
I've used KDE on 128 MB, and after some KPersonalizer tweaks, it runs just fine.

---

### Post by ComplexNumber on 2006-06-04
guys, don't forget that not all RAM runs at the same speed.

---

### Post by aysiu on 2006-06-04
[QUOTE=ComplexNumber]guys, don't forget that not all RAM runs at the same speed.[/QUOTE] Tell that to the person who wrote the article.

---

### Post by Mathias-K on 2006-06-04
[QUOTE=ComplexNumber]guys, don't forget that not all RAM runs at the same speed.[/QUOTE]

That's right, but if KDE loaded 500MBs of klibs/kicker/kio-slaves/ktanlibglk5.0-1-2 files into your RAM, performance would go down even if your lone 256MB stick was the most insanely overclocked DDR2 PC2-1000 speed :)

---

### Post by njf on 2006-06-04
[QUOTE=Mathias-K]That's right, but if KDE loaded 500MBs of klibs/kicker/kio-slaves/ktanlibglk5.0-1-2 files into your RAM, performance would go down even if your lone 256MB stick was the most insanely overclocked DDR2 PC2-1000 speed :)[/QUOTE]

Stop the fud non-sense please.

---

### Post by jdong on 2006-06-04
KDE and GNOME [the environments themselves] will both run comfortable within a 128MB system. However, if you expect to be able to run more than one program at a time, you'd want to step up for 256. Even at 256, running a particularly RAM-hungry program (Azureus or Openoffice, as examples) can cause RAM starvation and the kernel to terminate a RAM hog.

As a result, I recommend at least 256MB RAM to use KDE/GNOME, while I'd say that 'power users' want in excess of 512MB. I personally stick 1GB in all my systems, as more RAM yields better overall performance (especially with Linux's caching abilities).


As far as GNOME vs KDE, nowadays both are around equal in terms of RAM consumption. As far as performance, that's really a touchy and mixed field. Most of the times they are on par, but with 2.14 GNOME has received a bunch of performance tweaks that should improve its performance compared to KDE. I have only seen GNOME numbers to support that claim and I do not really feel any difference in my day-to-day use, so I can't confirm that except by running synthetic benchmarks and saying "Yep. It draws 10,000 windows faster than KDE. Wonderful."

---

### Post by Jucato on 2006-06-04
But then again, those RAM-hungry programs aren't KDE apps at all. And the same programs would behave the same way (RAM hungry) whether or not they run in KDE, GNOME, or even Windows! Specially these two, as they are using Java (particularly Azureus).

I was able to effectively and satisfactorily run KDE on my system with only 256 MB of RAM. and that's with SuperKaramba themes and some other apps running in the background. 512MB RAM for KDE? that's just plain *@%$#!!!

---

### Post by jdong on 2006-06-04
I'm not defending the article's author. I agree that saying KDE  (or GNOME or whatever DE is commonly available) requires 512MB RAM is just ridiculous.

However, a desktop environment is just the base and is beneath everything you do on your system, so there definitely are users that would need 512MB RAM. Is it KDE's fault? Not at all. It's whatever program demands so much RAM. Often times it's not a bit associated with KDE.

However, if that person is to use, say, Fluxbox (which uses under 5MB RAM at all times), would that make a difference? Perhaps, if the 80 or so MB of RAM that KDE would be using is freed, it could make the difference between run and doesn't run.

---

### Post by briancurtin on 2006-06-04
[QUOTE=qalimas]The article says KDE needs 512MB of RAM.[/QUOTE]
yeah, but if you tell people you only need 128 mb of ram, they will expect to be able to run everything they ever wanted on 128 mb of ram. 512 is a safe number

---

### Post by aysiu on 2006-06-04
[QUOTE=briancurtin]yeah, but if you tell people you only need 128 mb of ram, they will expect to be able to run everything they ever wanted on 128 mb of ram. 512 is a safe number[/QUOTE] Except that the article says Gnome needs only 384 MB: ```
Desktop 	Required RAM 	Required CPU
fluxbox/idesk 	48 	100 MHz
XFCE4 	128 	200 MHz
Gnome 1.x 	256 	500 MHz
Gnome 2.x 	384 	800 MHz
KDE 3.x 	512 	1 GHz
```

---

### Post by jdong on 2006-06-04
That article is clearly biased against the full-blown desktop environments with a particular grudge against KDE. Don't believe those ludicrous requirements for 'running KDE' or even 'running GNOME' :)

---

### Post by Sushi on 2006-06-05
I did a test with KDE once. Someone was telling the usual "KDE is bloated and eats RAM for breakfast!"-claim in Slashdot. And I wanted to shut him up. What did I do? I tried my best to make KDE eat as much RAM as possible. And I did that by loading bunch of apps. I believe I had Kspread, Kword, Kpresenter, Konqueror, Amarok, Konsole, Kate, Kdevelop, Karchive, Kstars, Calculator, Juk, Kontact, Kopete, Codeine, and few others all up & running, and IIRC the system was consuming about 360MB of RAM (not including cache and buffers).

So if someone claims that KDE NEEDS 512MB of RAM, you can be rest assured that he's full of crap.

---

### Post by Mathias-K on 2006-06-05
[QUOTE=njf]Stop the fud non-sense please.[/QUOTE]

I made no FUD, just a joke towards the funny naming schemes of KDE/Linux/UNIX system libraries like "glibgjc1-2". In fact, I prefer KDE over GNOME, I'm just exploring Ubuntu a bit. :)

What I really mean, and some may have overlooked, is that if a desktop environment (and I used KDE because it is the topic) has to use more RAM than you've got, your harddisk will be the bottleneck no matter how fast memory sticks you've got.

This is not a hardware enthusiast forum, and sometimes it's noticed. In Linux, people tend to overlook some basics principles of modern hardware.

---

