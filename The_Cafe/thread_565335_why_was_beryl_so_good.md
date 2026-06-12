---
title: "why was beryl so good?"
date: 2007-10-02
forum: The Cafe
---

### Post by skymera on 2007-10-02
wheni has  beryl, it was perfect, the windows were wobbly and could stretch.
and had a low CPU load.

but fusion now, its windows are bad, lots of useless plugins,
and also

it runs a constant 50% CPU usage!?
100% CPU 1 - 30% CPU 2

is it supose to be like that? or have i got a problem?

---

### Post by por100pre1 on 2007-10-02
I don't think you have a problem. Compiz-Fusion promises to be better than Beryl but is not ready yet.

---

### Post by skymera on 2007-10-03
i hope its bettere.
im not going to use if its copnsrantly using over 50% of my cpu

---

### Post by HokeyFry on 2007-10-03
how past is your CPU, cause i dont have that issue

---

### Post by bodhi.zazen on 2007-10-03
Moved as this is not a support request.

---

### Post by R-Dot-Yung on 2007-10-03
dude im on a crappy latitude Dell d600 with Compiz Fusion and the thing has no problems...

my only issues is my laptop overheats and then the system slows down immensly, but if i keep it cool than i have zero issues

something must b wrong, especially if u have a dual core

---

### Post by macogw on 2007-10-03
Compiz-Fusion is using 0% CPU and 1.6% mem for me.

---

### Post by Mazza558 on 2007-10-03
> **macogw said:**
> Compiz-Fusion is using 0% CPU and 1.6% mem for me.

Similar here, though slightly higher due to the intergrated card on my laptop. CF is a thing of beauty, and it runs very fast on my laptop (3x faster than Beryl).

---

### Post by skymera on 2007-10-03
i have a
2.0Ghz Dual Core processor
512MB GDDR3 overclocked video card

---

### Post by ~LoKe on 2007-10-03
Compiz Fusion is barely hitting my CPU anymore.

---

### Post by skymera on 2007-10-03
running constant 100% CPU 1?

and 30% CPU 2.

boooo

---

### Post by phen on 2007-10-03
use beryl until gutsy, then compiz-fusion is there out of the box, maybe your probs are gone then. maybe its just a config issue...

be patient for another 2 weeks :)

---

### Post by specs10 on 2007-10-03
I haven't had any cpu usage issues, but compiz-fusion seems to crash a lot more often than beryl ever did for me.  :/

---

### Post by macogw on 2007-10-03
> **Mazza558 said:**
> Similar here, though slightly higher due to the intergrated card on my laptop. CF is a thing of beauty, and it runs very fast on my laptop (3x faster than Beryl).

My video card is also integrated on my laptop.  It's an Intel i945.  It's definitely snappier than Beryl.

EDIT: I'm using Gutsy, and it's CF 0.6.0

---

### Post by starcraft.man on 2007-10-03
I don't have any CPU problems either and I'm running an older machine than yours. Try a reinstall or maybe a driver issue... 

My biggest beef with Fusion is that the current advanced configurator app (the extra one in repos) is inferior to the old Beryl-Manager, it's just painfully annoying going back and forward in menus to tweak things. That and the fuision tray icon didn't work when I installed it, not sure why. I think they need to focus on a bit more usability before they continue on their crusade for plugins/functionality.

---

### Post by master_kernel on 2007-10-03
Fusion is probably getting 1% on my dual-core Athlon 64. Beryl was good because of it's amazing support and bleeding-edge graphics.

---

### Post by floke on 2007-10-03
Try turning some stuff off - shadows and blur always blow it for me - apart from that I'm peachy!

---

### Post by Darklotus666 on 2007-10-03
compiz uses half of my cpu only when using the cube but the instant i stop goes to nothing,  but beryl did the same thing

---

### Post by asmoore82 on 2007-10-03
> **skymera said:**
> i have a
2.0Ghz Dual Core processor
**512MB GDDR3 overclocked video card**

Is that an ATI card?
If so, the only way you got compiz working with the proprietary driver was via XGL?
If so, there is the problem.

---

### Post by skymera on 2007-10-03
no its nVidia, i got the latestdriver through Envy.

so thats not a problem.

im gonna run it now and switch some stuffs off.

---

### Post by Mazza558 on 2007-10-03
> **asmoore82 said:**
> Is that an ATI card?
If so, the only way you got compiz working with the proprietary driver was via XGL?
If so, there is the problem.

Not true. I'm using the propietary drivers for my ATI card (see sig), running in Gutsy in an Xgl session. It's as smooth as it could be.

---

### Post by Depressed Man on 2007-10-03
I've seen XGL spike when I use the cube with the fish aquarium inside. Tis why I switched my desktop from cube to the desktop wall.

---

### Post by Iceni on 2007-10-03
Don't know, still using beryl. Its not broken so I don't want to fix it.

---

### Post by asmoore82 on 2007-10-03
> **Mazza558 said:**
> Not true. I'm using the propietary drivers for my ATI card (see sig), running in Gutsy in an Xgl session. It's as smooth as it could be.

do you have DRI support?
```
glxgears
```

---

### Post by Polygon on 2007-10-03
compiz-fusion does not work for me if i have the proprietary ati drivers installed... in fact in gutsy when i first installed it, compiz turned off. when i later removed the ati fglrx drivers and used the open source ones, compiz turned back on and it works fine

and compiz for me right now is using 0% cpu and about 6.3mb of memory

---

### Post by skymera on 2007-10-04
i cant use Amarok or Compiz at the same time.
they freeze system.

if i click next song, freeze, 5-10 secs.

i have all the correct drivers, shouldi  just look fora  new music player?

---

### Post by frodon on 2007-10-04
@skymera, read thoroughly the following links, i think you may need to tweak a little bit your xorg.conf depending of the nvidia drievrs you are using :
[http://forum.compiz-fusion.org/showthread.php?t=1682](http://forum.compiz-fusion.org/showthread.php?t=1682)
[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA)

---

### Post by skymera on 2007-10-04
NVIDIA driver version : 100.14.19

i have a look at thse lniks

---

### Post by macogw on 2007-10-04
> **Polygon said:**
> compiz-fusion does not work for me if i have the proprietary ati drivers installed... in fact in gutsy when i first installed it, compiz turned off. when i later removed the ati fglrx drivers and used the open source ones, compiz turned back on and it works fine

and compiz for me right now is using 0% cpu and about 6.3mb of memory

Older cards (radeon 9250 or earlier) can't use the fglrx drivers.

---

### Post by Polygon on 2007-10-04
> **macogw said:**
> Older cards (radeon 9250 or earlier) can't use the fglrx drivers.

i have a radeon 9800.

with fglrx installed i get 3d acceleration, but no compiz

with the open source drivers, i get compiz but no 3d

---

### Post by panther_sn on 2007-10-04
I have an Nvidia GeForce 6200 and CF uses 0 cpu and 96kb mem so no probs here, and my wifes dual core lappy is same except 108kb mem so I reallly can't figure out how ur pc is using soooo much CPU from CF

---

### Post by skymera on 2007-10-04
ok think i figured it.

Amarok!

when using amarok and CF my CPU rockets and sticks.
ive swapped to rhythm box now...but i miss amarok, it was good.

rhythmbox...seems...not as good.

anyone else got high cpu usage when amarok and cf?

---

### Post by starcraft.man on 2007-10-04
> **skymera said:**
> ok think i figured it.

Amarok!

when using amarok and CF my CPU rockets and sticks.
ive swapped to rhythm box now...but i miss amarok, it was good.

rhythmbox...seems...not as good.

anyone else got high cpu usage when amarok and cf?

Try Exaile or Listen (in repos), both good projects though not identical to Amarok. I used to recommend Banshee but it's been getting on my nerves lately... so try those two.

And no, I've never gotten high CPU usage from Amarok, only used it a few times though.

---

