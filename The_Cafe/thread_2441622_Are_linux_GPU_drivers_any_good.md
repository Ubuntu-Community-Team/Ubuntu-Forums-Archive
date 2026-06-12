---
title: "Are linux GPU drivers any good"
date: 2020-04-25
forum: The Cafe
---

### Post by Chelidze on 2020-04-25
Hi, there all (haven't posted here in a while or used linux for a long time)


So, I had a "discussion" on reddit and my opinion and this is what it was long time ago AMD open-gl drivers was a mess.
Well i've stated that no metter how you put it every companies gpu driver was inferior to windows counterpart gust because of market share it is pretty much unheard-of to invest that much in linux drivers.

So the other people stated that linux is a flying carpet and in the nix amd drivers are actually better than windows drivers.
Is this true are linux GPU drivers today so good that they are not only matching the windows but they are even outperforming it.

---

### Post by TheFu on 2020-04-25
it depends on what you want to accomplish.
intel drivers have been pretty great for years.  No fuss. Just work.
nvidia drivers have been hit or miss.  Look at the release notes for 20.04 and all the caveats about using nvidia proprietary drivers.  But if you go with the F/LOSS drivers, things (for certain values of "things") are better.
i don't have any AMD GPUs.

---

### Post by CatKiller on 2020-04-25
> **Chelidze said:**
> Well i've stated that no metter how you put it every companies gpu driver was inferior to windows counterpart gust because of market share it is pretty much unheard-of to invest that much in linux drivers.

You are incorrect. 

Nvidia's Linux driver is essentially exactly the same as their Windows driver; they have a shim to account for the differences in architecture between the Linux graphics stack and the Windows graphics stack, and they don't include the game-specific fudges that form the "Game Ready" stuff, but the code that does the actual work is identical.

AMD's and Intel's drivers are both open source. Both companies regularly improve each other's drivers because they are part of the same ecosystem. Both sets of drivers are very good. 

Software on Linux regularly outperforms the same software on Windows when it's been optimised for both, and often outperforms on Linux when the software's only been optimised for Windows.

---

### Post by Chelidze on 2020-04-25
> **TheFu said:**
> it depends on what you want to accomplish.
intel drivers have been pretty great for years.  No fuss. Just work.
nvidia drivers have been hit or miss.  Look at the release notes for 20.04 and all the caveats about using nvidia proprietary drivers.  But if you go with the F/LOSS drivers, things (for certain values of "things") are better.
i don't have any AMD GPUs.

Yes, i heard about intel drivers they are fantastic they say and even when i was using ubuntu i would get really good performance out of intel integrated cards, but their hardware was a mess i remember i used to try games under wine and it would rarely work and when i would ask around what what was the problem they would be like. Hardware man hardware that thing doesn't supports this and that :/
Don't know if the intel cards are any better now but they were quite crippled.

> **CatKiller said:**
> You are incorrect. 

Nvidia's Linux driver is essentially exactly the same as their Windows driver; they have a shim to account for the differences in architecture between the Linux graphics stack and the Windows graphics stack, and they don't include the game-specific fudges that form the "Game Ready" stuff, but the code that does the actual work is identical.

AMD's and Intel's drivers are both open source. Both companies regularly improve each other's drivers because they are part of the same ecosystem. Both sets of drivers are very good. 

Software on Linux regularly outperforms the same software on Windows when it's been optimised for both, and often outperforms on Linux when the software's only been optimised for Windows.

I remember two years ago i toked with mozilla engineer and i asked him why was firefox worked so bad under linux compared to windows, remember had really tough time making hardware acceleration work on 1050ti. 
He was like resources we can't allocate enough men power in linux version because of market share, we try our best but the reality isn't sunshine and lollipops.

I remember there was only one guy full time working on amd graphic drivers and did everything changed so much when we see linux graphic drives being this good.

Is there any statistic to this/ benchmarks can't find any good sources or articles about this crazy improvement that i missed out on

---

### Post by grahammechanical on 2020-04-25
> Is there any statistic to this/ benchmarks can't find any good sources  or articles about this crazy improvement that i missed out on 				

[https://www.phoronix.com/scan.php?page=home](https://www.phoronix.com/scan.php?page=home)

Regards

---

### Post by P-I H on 2020-04-25
Look at this benchmark
[https://www.phoronix.com/scan.php?page=article&item=win10-debian101-intel&num=2](https://www.phoronix.com/scan.php?page=article&item=win10-debian101-intel&num=2)

---

### Post by Chelidze on 2020-04-25
> **grahammechanical said:**
> [https://www.phoronix.com/scan.php?page=home](https://www.phoronix.com/scan.php?page=home)

Regards


> **P-I H said:**
> Look at this benchmark
[https://www.phoronix.com/scan.php?page=article&item=win10-debian101-intel&num=2](https://www.phoronix.com/scan.php?page=article&item=win10-debian101-intel&num=2)

Thanks

---

### Post by mastablasta on 2020-04-27
> **Chelidze said:**
> 
I remember two years ago...

two years ago is a "long" time in tech industry. i mean just look at the smart phones.

---

### Post by adamclarke96 on 2020-05-02
I'm using the Nvidia drivers for my GTX 660 and get the same FPS in minecraft as I do in windows 10. I know its not exactly a demanding game but it'll give an idea of performance compared to windows

---

