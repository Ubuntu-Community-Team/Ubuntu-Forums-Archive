---
title: "Where's my dual chanel?"
date: 2005-07-14
forum: The Cafe
---

### Post by sonny on 2005-07-14
Hi... I'm posting this for two resons:
1.- Disappointment
2.- Guidance

Last week I bought 2 Ram memory of 512 at 400 hz, to use it in dual-chanel with Ubuntu (YES my mobo supports the dual-channel I've check this twice), but now that I've been playing a long with this, I don't feel any drastic change in my OS performace, why? I thought it would be like a rocket, but it doesn't it loads at practiaclly the same time, programs run as fast as they used to when I had 256 mb in ram, averything is the same. Why? Do I have to do some tweak to get the best performance for the dual-channel? I'm kind of sad, dissapointed, heart-broken, etc. What is the matter with my OS? 

I do notice the change while I'm playing BUT it's not the dual chanel is just the extra ram, cuz I get the same (at least no visible change) performace if I run with the 512 and the 256 in the ram slots.  One more BIG issue, when I use the monitor performance it only detects 988 mb...   :? ???

Need some thoughts from you guys.

---

### Post by gil-galad on 2005-07-14
Dual channel memory has nothing to do with the OS.  If its on then it works the same on any OS.  And its not magic, its just a little boost in memory performance.  Don't expect too much :)

---

### Post by Rule on 2005-07-14
if you want dual channel make sure there the EXACT sticks of ram from the same compay. some ram manufactures sell them [http://www.ncix.com/products/index.php?sku=9821&vpn=VS1GBKIT400&manufacture=CORSAIR](http://www.ncix.com/products/index.php?sku=9821&vpn=VS1GBKIT400&manufacture=CORSAIR)

---

### Post by sonny on 2005-07-14
[QUOTE=Rule]if you want dual channel make sure there the EXACT sticks of ram from the same compay. some ram manufactures sell them [http://www.ncix.com/products/index.php?sku=9821&vpn=VS1GBKIT400&manufacture=CORSAIR](http://www.ncix.com/products/index.php?sku=9821&vpn=VS1GBKIT400&manufacture=CORSAIR)[/QUOTE]
They are... I bought them as twin memories. And when I turn on my pc, there's the memory check wich is 1048--- kb and then it says: Memory runs in dual channel. Meaning that the mobo takes them as dual channel.

[QUOTE=gil-galad]Dual channel memory has nothing to do with the OS. If its on then it works the same on any OS. And its not magic, its just a little boost in memory performance. Don't expect too much [/QUOTE]
Well, if there's not a boost in the performance why are they publishing as such? How good is it for me to have a dual channel memory?  ](*,) 

And what about the memory monitor only showing 988???

---

### Post by Rule on 2005-07-14
the performace increase isn't totaly noticeable ubless you do a lot of stuff at one time.

Dual channel is only good if you do stuff like video editing and 3D animation. It can improve games too. also if you run a server there good too.

if you want a big boot get a dual CPU.


your never going to see exactly 1024 of ram. I can't really remember the reason but i'm sure someone here will know.

---

### Post by poofyhairguy on 2005-07-14
[QUOTE=sonny]
Well, if there's not a boost in the performance why are they publishing as such? How good is it for me to have a dual channel memory?  ](*,) 
[/QUOTE]


OK. But its not a big leap. The big leap comes with dual core CPUs...thats adding power. With the faster RAM you maybe add 10%...unnoticable on the desktop.

At least with that extra ram gnome will be happy. As far as it not reporting it all, I think it doesn't report the core libs...

---

### Post by sonny on 2005-07-14
Ok... so as I'm getting you so far... the dual channel memory is going to be a kick ass IF I have a dual CPU??? am I right??

So I was expecting something impossible.  :cry: 

Well... at least I have a lot of memory to run apps. And as far as video editing, I'm going to do a little, my father wants some of the old home videos (my childhood, and my sister's) to be move to dvd, so I think I'm getting to it by the end of the year.

Thanks a lot guys.

---

### Post by endy on 2005-07-14
Just to throw some more ideas into the pot...

AFAIK dual core CPUs again wont just give you twice the power, you need a properly coded app to take advantage of the extra core or have two seperate programs running, each one using a different core.

As with any new technology on the PC, it's never quite as simple as the marketing people make out. The same goes for dual channel memory, you will likely only see an improvement in the more heavy duty apps or games. Boot times, firefox loadings etc probably wont be affected too much.

---

### Post by jerome bettis on 2005-07-15
[QUOTE=endy]AFAIK dual core CPUs again wont just give you twice the power, you need a properly coded app to take advantage of the extra core or have two seperate programs running, each one using a different core.[/quote]

yeah that's pretty much right.  almost every program has parts that must be run sequentially, and only some parts can be parallelized.  so throwing N more processors into the mix doesn't make a program N times as fast because certain parts of it have to be executed by just one cpu.

and if you're not using your swap very much (mine is empty 95% of the time with 512mb) throwing more ram at it won't help much either because it already has all it needs.  however faster ram will make a difference.  

on chip cache (size, and managment) is more important than that and is often overlooked.  also disk and bus speed are probably the most important things to having a fast system because they are the biggest bottlenecks.  but intel's marketing has made everyone just look at cpu clock speed which in reality doesn't mean shit in the grand scheme of things - especially considering a 'faster' cpu typically takes more cycles to execute the same instruction.  intel = speed demon (fast clock, lots of cycles per instruction), amd = brainiac (slower clock, less cycles per inst.).

original poster, post up your system specs and specifically when does your system not perform well and maybe we can help.

---

