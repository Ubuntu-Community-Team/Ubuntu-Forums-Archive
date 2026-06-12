---
title: "Why is X so bad on hardware?"
date: 2005-11-01
forum: The Cafe
---

### Post by danron on 2005-11-01
Hello.

I want to know how it comes that X is sooo much worse than Windows when it comes to do its most fundamental job, displaying graphics on a monitor correctly :-P. I mean why is it so rare for me that the setup programs actually detects the sync rates and resolutions correctly? Even worse, most of the time I cannot even go to the same max resolution in X when I configure manually because of some uncanny stuff going on that I don't know about. Windows always fix this stuff automatically for me. I know how to configure X normally but everytime I have to do some workarounds with some external tool like 855resolution... 

Ok, sorry for the rant but I just really want to know the reasons so I can forgive X for it's behaviour :)

---

### Post by 23meg on 2005-11-01
Here's why:

[http://dri.freedesktop.org/~jonsmirl/graphics.html](http://dri.freedesktop.org/~jonsmirl/graphics.html)

---

### Post by jeremy on 2005-11-01
In my experience, x is much better that windows, on my hardware - matrox G550 + benq T905, it detected and set it up correctly. The same setup on windows xp needed proprietry driver installation, followed by a reboot, followed by configuration.
Give me x any day.

---

### Post by danron on 2005-11-01
Jeremy : Ok, it happened to me too that Windows didn't had built in drivers and I had to work a little bit for it to work. But never as much as in X, expecially when I use Intels integrated GPUs like GMA 900.


23meg : Wtf? So, many open source drivers are reverse engineered? I actually believed that there were some kind of specifications you could get from the GPU makers. Or at least the source for a reference driver for Linux .. This is so sad.

---

### Post by 23meg on 2005-11-01
It is indeed sad, and isn't likely to change anytime soon. But if XGL does deliver the promise, things are going to be better than ever.

---

### Post by zerhacke on 2005-11-01
[QUOTE=danron]23meg : Wtf? So, many open source drivers are reverse engineered? I actually believed that there were some kind of specifications you could get from the GPU makers. Or at least the source for a reference driver for Linux .. This is so sad.[/QUOTE]
Yes, many many OS drivers are reverse engineered.  It's a Windows world still.  Most GPU makers would rather not give out the nitty gritty on their cards because doing so makes it easier for the competition to learn from their work.  In Windows, the drivers are closed source.  We don't get to see how the code interacts with the hardware - it just works, and that's all that most Windows users care about.  Since the majority of *nix software is open source giving us open source drivers would mean giving the competition an easy way to learn from their cards.

There are a few closed source drivers for *nix.  nVidia, for one, makes a closed source driver.  We still don't get to see how the card works, but at least it does work.  Some of the smaller companies are giving out their code, but they're rare.  Most of the time, if we want it to work for *nix, we have to reverse engineer it in order to get a workable product.

It wasn't a big deal when Linux was still mainly a CLI OS.  Now that it's gaining popularity as a GUI based workstation drivers, open or closed, are becoming a big deal.

---

### Post by 23meg on 2005-11-01
In short, we're in need of open souce hardware in addition to open source software, but the big boys don't want to play. That's why projects such as XGL and Cairo + glitz are so important for the near future of the Linux based desktop.

---

### Post by az on 2005-11-01
[QUOTE=danron]
Ok, sorry for the rant but I just really want to know the reasons so I can forgive X for it's behaviour :)[/QUOTE]


Channel your energy into something like complaining (politely so that they take you seriously) to the manufacturers.  

It is hard to manage a concerted effort when there are so many parties involved:  Is it the chip maker's fault?  Is it the video card manufacturer's fault?  Is it the distributer (vendor) of the card?  It is WalMart?

---

