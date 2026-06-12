---
title: "Which Debian spin for a 256MB RAM computer?"
date: 2010-02-14
forum: The Cafe
---

### Post by Pogeymanz on 2010-02-14
My dad has an old Dell desktop that I believe has 256MB RAM (Could be 512, but I doubt it).

He wants to try Linux dual-booted with WinXP just because I told him he can do all the same stuff and it wont get slower over time. He was surprised to learn that he can edit Word documents and browse with Firefox in Linux. :)

I'm pretty set on Debian Stable for him because he wont care about upgrading stuff and my experience tells me that Debian is nicer to old machines than Ubuntu LTS. And I do want him to do some stuff for himself (i.e. Learn to use Synaptic).

I really want to use Gnome because it's easy and well-polished. XFCE and LXDE do not feel as refined and stable as Gnome (**I always prefer XFCE for myself, just not for others**), but that whole 256MB RAM thing tells me that Gnome will probably choke.

Has anyone any input on whether I should use the XFCE or LXDE spins of Debian? I don't want to spend all day configuring stuff either.

He's not totally bad with computers, but he only knows Windows. He can even wipe his hard drive and reinstall Windows, but it is a step-by-step recipe for him; he doesn't really understand what he is doing. And like I said, he'll probably just want to double-click Ooo-Writer and double-click Firefox.

---

### Post by squilookle on 2010-02-14
I'm not sure how much memory Debian stable uses at the minute, but the last time I used it, it really didn't take much at all till I installed ATI drivers, then memory usage by X went through the roof... 

I seem to remember it idling at just over 100mb, and this is without disabling any services. Maybe you could install gnome but then take out as many services as you dare, you might *just* get away with it? 

AS I say, it's more than a year since I used Debian stable, so I might be wrong.

---

### Post by NightwishFan on 2010-02-14
Debian stable is fairly light with Gnome, but use Xfce to really save a bit of memory. The newer XFCE is great, I gave it to some friends of mine and they really have fun with it.

---

### Post by Zoot7 on 2010-02-14
Crunchbang would be a great candidate here IMO, the only potential issue being a lack of a DE.

At the moment I've Lenny with Gnome atop Openbox on a 7 year old machine with 512MB, and it does its job as an internet browser/music/video machine fine, I don't think I've ever seen it to max out the RAM.

I'm not sure how you'd get on a 256MB machine but I'd imagine with LXDE it might be fine, although the better option IMO would be just to run say Openbox or Fluxbox alone. Depends on whether you Dad would like not having a DE or not. :)

---

### Post by gsmanners on 2010-02-14
Once you get up to about 256 MB, I find that it isn't so much the DE as much as your choice of applications that causes problems. Make sure you find lightweight apps to go with your choice of DE if you want a good experience.

---

### Post by Twitch6000 on 2010-02-14
I suggest tinyme. It is based on PClinuxOS and is meant for small usage.

[http://tinymelinux.com/doku.php/download](http://tinymelinux.com/doku.php/download)

Oh and did I mention it isn't debain based :D.

---

### Post by tjwoosta on 2010-02-14
I installed Debian Lenny XFCE on my parents computer with 256mb ram about a year ago and its still going strong. I just stuck with all lightweight xfce apps and its not too bad. Its a good thing my parents aren't big multi-taskers though because if you open iceweasel and openoffice writer together the ram usage maxes out and it starts going into swap.

---

### Post by XubuRoxMySox on 2010-02-14
LXDE is under such heavy development, things keep changing... but it will probably even out and become more stable by the end of the year, at the rate they're going (just a guess).

The new Xfce is really sweet! Very "Gnome-like," but without as much demand on resources. I'm using it on Debian Testing and it rawks! I think it's good for newbies too.

-Robin

---

### Post by themarker0 on 2010-02-14
I don't know if Flux works with debian, but i've used it with other distros on linux, and it was amazing. Hardly any usage.

---

### Post by Pogeymanz on 2010-02-15
I just installed Debian with Gnome in VirtualBox using 256MB RAM. It works perfectly fine. Since I still believe that Gnome is the easiest DE in the world, I will be going with this.

P.S. Holy Crap! OpenOffice 2.4! Yikes...:P

---

### Post by snowpine on 2010-02-15
Debian Stable is a great choice. Once you create a swap partition, 256mb ram will be a non-issue. Good luck!

---

