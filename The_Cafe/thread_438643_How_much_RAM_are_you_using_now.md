---
title: "How much RAM are you using now?"
date: 2007-05-09
forum: The Cafe
---

### Post by Sunnz on 2007-05-09
The Linux vs. Vista thread has been discuss about RAM lately: [http://ubuntuforums.org/showthread.php?p=2622667#post2622667](http://ubuntuforums.org/showthread.php?p=2622667#post2622667)

I guess they just used top(?) to see how much RAM are they using?

Applying the same "scale" they are using, I guess my OS X Laptop now is using 864M of RAM at this moment?

```
MemRegions: num =  5824, resident =  236M + 17.5M private,  110M shared
PhysMem:   216M wired,  386M active,  262M inactive,  **864M used,  159M free**
```It is the RAM usage of my system "right now", not a reboot with least software loaded to boast up (or boast down?) how much RAM I have really using.

I'll put up the RAM usage again when I get to reboot into Kubuntu.
EDIT: Just rebooted, my Kubuntu (+Compiz) is using 533MiB on the very same MacBook:
```
Mem:   1004088k total,  ** 545848k used,   458240k free,    **36692k buffers
Swap:   499992k total,        0k used,   499992k free,   242836k cached
```However it is a new install (just installed last week.) and it is a fresh reboot...

P.S. my laptop has 1GiB of RAM, and is shared with graphics hardware, if that makes any difference...

---

### Post by deadlydeathcone on 2007-05-10
Top is a pretty poor way to monitor memory usage system wide, as itcounts buffers as used memory, which is really only a technically correct to monitor memory usage.

A much better command is ```
free -m
```
 
Mine looks like this:
```
             total       used       free     shared    buffers     cached
Mem:           947        916         31          0         37        421
**-/+ buffers/cache:        457        490**
Swap:         1160         39       1121

```

What you really want to pay attention to is the part I bolded, as it takes cached memory out of the equation. The reason for this is that on Macs and Linux cached memory is used to dump commonly used, non-essential data to ram so that it doesn't have to pull it off the hard disk when it's needed, which gives a bit of a performance boost, and as it's optional shouldn't be counted. In addition it can be cleared in a hurry if another process has better use for the memory used. On a similar note Vista also has a similar feature, but I have no idea how it works and am frankly terrified of it. :guitar:

Hope that helped.

---

### Post by savagenator on 2007-05-10
well, i have 3gb. With vista about 1gb is used up off the bat. After about a days worth of playing around, ubuntu with beryl uses about 1gb

right now its 
```
             total       used       free     shared    buffers     cached
Mem:          3019       2801        217          0        104       2071
-/+ buffers/cache:        626       2392
Swap:            0          0          0
```

---

### Post by obviouslyshane on 2007-05-10
mine looks like this :) but I'm doing several things... listening to music, posting on here, and ripping cds.

```
 
             total       used       free     shared    buffers     cached
Mem:          2026       1389        636          0         86       1040
-/+ buffers/cache:        263       1763
Swap:         5930          0       5930

```

Vista used about a gig doing nothing, kubuntu used about 600 megs doing nothing, and ubuntu with desktop effects, doing nothing uses around 200 megs...

---

### Post by JNowka on 2007-05-10
```

             total       used       free     shared    buffers     cached
Mem:          2018        598       1419          0         30        298
-/+ buffers/cache:        270       1747
Swap:         3851          0       3851


```After 3 hours of my laptop running.  Surfing net, using VMware for a while, and working on some apps I have in development.

---

### Post by maniacmusician on 2007-05-10
```

             total       used       free     shared    buffers     cached
Mem:          2026       1966         59          0         88       1288
-/+ buffers/cache:        589       1436
Swap:         3145          0       3145

```

That's with 4 firefox windows open (if you count all my tabs, that's 27 pages open) , Konversation, Amarok, Gaim, Kopete, Konqueror, Kaffeine and Beryl running. That's pretty good.

edit: that's after about 10 hours of uptime.

---

### Post by waxapple on 2007-05-10
```
             total       used       free     shared    buffers     cached
Mem:          1010        994         15          0         22        430
-/+ buffers/cache:        541        469
Swap:         1223        470        753

```

Laptop with 1gb RAM

Azureus, Beryl, aMSN and Firefox running.
after about 1 day uptime

---

### Post by DarkN00b on 2007-05-10
768 MB - swap is never used. :)

```
             total       used       free     shared    buffers     cached
Mem:        742088     725432      16656          0      41388     359860
-/+ buffers/cache:     324184     417904
Swap:      1646620          0    1646620

```

---

### Post by ~LoKe on 2007-05-10
```
             total       used       free     shared    buffers     cached
Mem:          1010        717        293          0         17        381
-/+ buffers/cache:        317        693
Swap:          502          0        501
```

---

### Post by Mateo on 2007-05-10
```
             total       used       free     shared    buffers     cached
Mem:          1011        997         14          0          5        715
-/+ buffers/cache:        275        736
Swap:            0          0          0
```

2 instances of firefox open, 2 gnome-terminals, bluefish, and rtorrent running in the background.

---

### Post by crimesaucer on 2007-05-10
My Conky says:

61% of 495 MiB of RAM

and 1% of my 1.85 GiB SWAP

```
 free -m
             total       used       free     shared    buffers     cached
Mem:           495        452         42          0         22        119
-/+ buffers/cache:        310        184
Swap:         1898         37       1860

```

---

### Post by argie on 2007-05-10
```
             total       used       free     shared    buffers     cached
Mem:           233        219         13          0          1         45
-/+ buffers/cache:        172         60
Swap:          713        141        572

```
System's quite responsive. I wonder what all that swap is.

---

### Post by crimesaucer on 2007-05-10
> **Mateo said:**
> ```
             total       used       free     shared    buffers     cached
Mem:          1011        997         14          0          5        715
-/+ buffers/cache:        275        736
Swap:            0          0          0
```

2 instances of firefox open, 2 gnome-terminals, bluefish, and rtorrent running in the background.

Do you not need a Linux SWAP file? I'm still new to Linux, so I'm not sure if this is a dumb question.

---

### Post by Tundro Walker on 2007-05-10
Man, I wish I would have read your inquiry before voting.  I have 1gb of RAM on my computer, but I'm only using about 400-500mb of it when running normal stuff, like Firefox.

Of course, I have vm.swappiness turned down to 0, though, so my swap file isn't used much at all, while my RAM keeps getting loaded up until it has to ferret stuff off.  So, there may be ~100mb excess crap in there.

---

### Post by maniacmusician on 2007-05-10
> **crimesaucer said:**
> Do you not need a Linux SWAP file? I'm still new to Linux, so I'm not sure if this is a dumb question.
Swap is optional...it's not required, but it is usually beneficial to your system. Even if you don't need it, it usually doesn't do much harm to have it enabled. I've never seen my swap being used at all (unless I'm using one of my older computers, of course)

---

### Post by tbroderick on 2007-05-10
-/+ buffers/cache:        172        300


Stupid Firefox.

---

### Post by crimesaucer on 2007-05-10
For the most part my swap doesn't get used much, but I have noticed it used a few times, so I'm glad I installed it.

---

### Post by maniacmusician on 2007-05-10
> **crimesaucer said:**
> For the most part my swap doesn't get used much, but I have noticed it used a few times, so I'm glad I installed it.
It can be quite handy. Technically though, you **have** to install it. Ubuntu doesn't let you forego that step. A swap partition is required when installing the OS. But, after you install it, there are ways to turn swap off.

---

### Post by jkblacker on 2007-05-10
```
             total       used       free     shared    buffers     cached
Mem:           503        458         44          0         62        161
-/+ buffers/cache:        234        269
Swap:         1035        163        872

```

Now I don't think that's too bad for a laptop nearly 2yrs old and only 512MB RAM; it's firefox and Beryl and a terminal. Even surfing and listening to music and chatting on gaim only takes it to just over 50%.

---

### Post by Fitzy_oz on 2007-05-10
total       used       free     shared    buffers     cached
Mem:          1011        964         47          0         33        706
-/+ buffers/cache:        223        787
Swap:          839         33        806

---

### Post by Quillz on 2007-05-10
I use 1 GB in both my desktop and laptop. Works fine for me, I don't need much more at the moment.

---

### Post by v8YKxgHe on 2007-05-10
I currently have 4GB, however being on a 32bit OS I can only use just over 3gb.

---

### Post by PartisanEntity on 2007-05-10
Currently running Firefox, Evolution, Gaim, Skype:

```
             total       used       free     shared    buffers     cached
Mem:          2027        653       1373          0         94        286
-/+ buffers/cache:        273       1754
Swap:         2839          0       2839
```

---

### Post by TheTruth34 on 2007-05-10
running firefox, evolution mail, folding@home
```
             total       used       free     shared    buffers     cached
Mem:          1011        961         50          0        159        497
-/+ buffers/cache:        303        708
Swap:         2957         58       2898
```

---

### Post by use a name on 2007-05-10
633 MB, with a few resource-hogs running.

---

### Post by silkstone on 2007-05-10
With Firefox and a couple of gdesklets running...

```
             total       used       free     shared    buffers     cached
Mem:          1510        587        923          0         32        333
-/+ buffers/cache:        221       1289
Swap:         3725          0       3725

```

---

### Post by B. Gates on 2007-05-10
Um... eh... I'm running Vista at the moment and I can't quite answer the question, since my monitor isn't wide enough to fit in all the digits of this memory usage meter here.

---

### Post by Sunnz on 2007-05-10
Heh he Mr. Gates, didn't your development team implement this thing called "word wrap" on Vista? ;)

---

### Post by justaguynpc on 2007-05-10
FireFox, Synaptic, Beryl and Terminal:

 total       used       free     shared    buffers     cached
Mem:          2026        815       1210          0         74        332
-/+ buffers/cache:        408       1617
Swap:          956          0        956
justaguy@feisty:~$

---

### Post by Spr0k3t on 2007-05-10
Oops... I didn't read the first post and took the poll, it's not defined enough in the voting explanation.  So, with that said, I'm using approximately 800MB total on a 3GB system.  I'll have to check when I get back home.

---

### Post by reacocard on 2007-05-10
```
             total       used       free     shared    buffers     cached
Mem:           995        960         34          0        145        185
-/+ buffers/cache:        628        366
Swap:         1200          0       1199

```

This is after about 3-4 days of continual operation, with beryl. Xorg leaks memory on my system, I think. It's using almost 100MB right now. :shock:

---

