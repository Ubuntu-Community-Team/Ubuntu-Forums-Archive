---
title: "Help me diagnose a hardware-problem"
date: 2006-06-19
forum: The Cafe
---

### Post by Sushi on 2006-06-19
OK, I'm having some problems with my computer (the one I'm typing this on). What happened is this:

My W2K became riddled with viruses, so I decided to re-install it. I also decided to do a fresh re-install of Ubuntu, since I felt that my dist-uograded Dapper was not working optimally. As I were installing the OS'es, I disconnected sme hard-drives (I have two identical hard-drives in the machine, one for Ubuntu, other for Windows. I wanted to make sure that I don't hose the wrong HD during the install, so I disconnected the other HD during installs). I tried installing Windows XP, but that one failed for reasons not connected to this problem. 

Anyway, as I were using Windows to do to post-install configs, I noticed that my vid-card complained that it's not receiving enough power (It's a GeForce FX5900, and it neds an esternal powercable). That was strange since there had been no problems before. Anyway, I noticed that there were some artifacts on the screen (vertical lines), and the screen got correupted on occasion. Linux seemed to work better.

After few days, the amount of problems increased. The system would sometimes fail to start. It powered on, but there was no image on the monitor, not even BIOS. I started t think that the problem might be the vid-card.

Luckily I had a backup vidcard: Ati Rage Pro. Crappy at 3D, but enough to give me working 2D. And sure enough, with the "new" vid-card, system seems to work. But it doesn't, really. I have static and strange flashing on he screen. I can use the system, but it's NOT pleasant. If I scroll a website around, move windows around or move files around in the HD, the amount of static shoots up. I get then so much static that I can't really use the system. After things quiet down, the amount of static is reduced so much that I can actually do something with the system. If I try putting the FX5900 back in to the machine, it does boot, but after about one minute, the system freezes. The strange thing is that the mouse-cursor does still move around in the screen, but everything else is frozen. Keyboard-input doesn't work at that point either.

Any ideas what might be causing this? I'm planning to live with this for so long that I can get a Conroe-system.

Specs of the machine:

Athlon64 3200+ (S754)
1GB RAM
GeForce FX5900 and/or Ati Rage Pro
Soundblaster Audigy
2x 160 SATA HD's
DVD+-RW

---

### Post by _simon_ on 2006-06-19
seems like an easy one this... I'd say you need a new PSU (power supply unit). I think your old one is failing.

---

### Post by John.Michael.Kane on 2006-06-19
Sushi can i ask what brand PSU you have in your machine?  looking at the spec's you listed you should not be drawing no more then 200 watts. also you say that even on a clean install with all 2kupdates/SP your still getting hardlocks, and freezes thats strange. before you change out your psu. can you run mem-test? if mem-test comes up clean. try your GeForce FX5900 with only 1 of your SATA HD's. if you still are having hard locks/frezzing then you will know your psu needs a change out.

---

### Post by Sushi on 2006-06-20
The PSU in the system is [Nexus NX-3500](http://www.silentpcreview.com/article131-page1.html) (350W). Hmmm, maybe I should try replacing it before I replace the entire system. I don't really NEED Conroe. I was planning to use my current system for 1-2 years more. So I'll give it a shot :). Although I have tried using the system with disconnected DVD-drive, and only one HD, and I still have problems.

mem-test is also a good idea.

---

### Post by Sushi on 2006-06-21
I replaced the PSU with a brand-new 500w PSU, and the problems went away :). Thanks for help you all :)!

---

### Post by John.Michael.Kane on 2006-06-21
Sushi what brand of psu is that 500w? and i'm glad the issues is fixed.

---

### Post by Sushi on 2006-06-21
[QUOTE=SD-Plissken]Sushi what brand of psu is that 500w? and i'm glad the issues is fixed.[/QUOTE]

Well, it's not fixed :(. The flashing on the screen is a lot less severe now, but it's still there. So clearly the replacement-PSU did help, but it didn't fix the problem entirely. Strange.

The new PSU is Antec Phantom.

---

### Post by John.Michael.Kane on 2006-06-21
Sushi try using only one of the sticks of memory, and let mem-test run overnight  . see if there's any errors or lock-up's

---

### Post by Sushi on 2006-06-22
[QUOTE=SD-Plissken]Sushi try using only one of the sticks of memory, and let mem-test run overnight  . see if there's any errors or lock-up's[/QUOTE]

I tried running mem-test (the one you can run inside Linux), and it didn't work. It tried to so something, and the HD was crunching away, and then I simply got a "killed".

---

