---
title: "Whats your firefox startup time on ibex?"
date: 2008-12-10
forum: The Cafe
---

### Post by rajeev1204 on 2008-12-10
hi.

Firefox takes almost 7 to 10 seconds to start for me in intrepid.

Is that normal ? What are your stats.

System specs . AMD 4400 X2

1 GB RAM,7600 GT using 177.nvidia driver version.





regards

raj.

---

### Post by MikeTheC on 2008-12-10
About 4 seconds here.

AMD Athlon 3800+ (2.4 GHz)
2 GB RAM

---

### Post by easybake on 2008-12-10
10-11 seconds on a cold start.
~5 seconds normally

Acer Aspire one
Intel Atom 1.6ghz
1gb ram.

---

### Post by rudihawk on 2008-12-10
3-4 seconds?

Intel Core 2 Duo E6600 2.4Ghz
2GB RAM

---

### Post by speedwell68 on 2008-12-10
Mine isn't unduly long.  I see no point in timing these things, if it seemed like it was taking too long I might time it, but otherwise I'm not sad enough to care.

---

### Post by kerry_s on 2008-12-10
5 sec's after being loaded once.
450mhz 256mb ram

i use a 5 second loading message on mine so i know its actually loading.

```
iceweasel 2>/dev/null | xmessage "Loading....." -center  -timeout 5 -button , 
```

looks like this:

---

### Post by itsStephen on 2008-12-10
About 2 seconds

Athlon 64 LE-1620 2.4ghz and 2gb ram

---

### Post by Sealbhach on 2008-12-10
Slow, about 8 seconds using Firefox 3.1b3 but using preload, after the first slow startup it starts up quickly for the rest of the session.


.

---

### Post by ssam on 2008-12-10
install preload. that will make the cold starts almost as fast as the warm starts (it prefills the disk cache with useful files)

---

### Post by sdowney717 on 2008-12-10
hot start 2 seconds
running 2.4ghz intel single core with 1gb ram

cold start is 4 seconds, when not loading prior open tabs

---

### Post by binbash on 2008-12-10
1-2 seconds firefox 3.1b2

---

### Post by billgoldberg on 2008-12-10
> **rajeev1204 said:**
> hi.

Firefox takes almost 7 to 10 seconds to start for me in intrepid.

Is that normal ? What are your stats.

System specs . AMD 4400 X2

1 GB RAM,7600 GT using 177.nvidia driver version.





regards

raj.

On Ibex it started up in around 2-3 seconds.

I'm on Arch now and firefox (gran paradiso) starts up in under a second.

*(low end dual core, 784mb ram, 256mb ati radeon)*

---

### Post by speedwell68 on 2008-12-10
> **ssam said:**
> install preload. that will make the cold starts almost as fast as the warm starts (it prefills the disk cache with useful files)

Correct me if I am wrong, but doesn't 'preload' run with root privileges enabled, which is a really bad idea.  Like I said correct me if I am wrong.

---

### Post by ssam on 2008-12-10
> **speedwell68 said:**
> Correct me if I am wrong, but doesn't 'preload' run with root privileges enabled, which is a really bad idea.  Like I said correct me if I am wrong.

yes it does. i think it would add a lot of complication to have run per user.

it needs to keep track of which programs are run, and which files they are using. then it stores those stats in a file (which is only readable by root), then when you have free memory, it reads those files into ram so that they can be access instantly when needed.

you want it to be running all the time, so that it can preload all the bits gnome or kde needs while you are at the login screen. if you had it running once for each user, then they would all need to talk to each other to stop them stepping on each others toes.

i am not aware of any security problems with it in the past (and its been around for a few years).

the future of preload is to move it into the kernel so that it can be even smarter, but until thats ready preload is pretty good.

---

### Post by hessiess on 2008-12-10
about 20~ seconds(arch), I use a lot of addons. As a result I hardly ever close it.

---

### Post by xpod on 2008-12-10
2-3 seconds here on an AMD 64 X2 4000 with 2G of RAM and the onboard Nvidia 7 series GFX with 177 driver.

---

### Post by Arup on 2008-12-14
Cold start 2 seconds on my system, same for Opera, I have no plugins installed on FF.

---

### Post by dannytatom on 2008-12-14
Xubuntu 8.10 & Swiftfox it takes 7 seconds. :/

---

