---
title: "24' LCD monitor"
date: 2009-07-13
forum: The Cafe
---

### Post by iampriteshdesai on 2009-07-13
Yesterday I got a 24' LCD monitor BenQ2412HD. I have Vista. I hiked up the Display resolution to 1920x1080 the highest available. But after this whenever I played videos full screen, the display went blank and reappears with the message &#8220;DVI input&#8221;. After installing the drivers for the monitor this happened frequently even when the video wasn't on. I uninstalled the drivers, and the problem is limited to videos again. So I logged into Ubuntu and here the resolution is 1520x720 and I haven't faced this issue. So I lowered the Vista resolution to 1024x756. I haven't faced this problem.
But the picture is obviously of low level. The user guide says the ideal resolution is 1920x 1080.
Also in Ubuntu if I use 16:9 the screen gets skewed! But 16:10 works fine.

My graphics card is nVidia Fx5500. 256 MB
I have RAM 1GB.
Plz help me! I want to enjoy HD on it.

---

### Post by Icehuck on 2009-07-13
I'm going to take a wild guess here and say, that card is pretty old and doesn't support that resolution.


According to [Nvidia]("http://www.nvidia.com/page/pg_20040109440047.html")

> DVI support for compatibility with next generation flat panel displays with resolutions up to and including 1600×1200

Which basically means you will need a new card to get the resolution you want.

---

### Post by iampriteshdesai on 2009-07-13
is there anyway out of this? except buying a new one?

---

### Post by Icehuck on 2009-07-13
> **iampriteshdesai said:**
> is there anyway out of this? except buying a new one?

Your going to have to buy a new card.

---

### Post by iampriteshdesai on 2009-07-13
> **Icehuck said:**
> Your going to have to buy a new card.
In the mean while can I set it to some res which has 16:9

---

### Post by MikeTheC on 2009-07-13
Isn't that a rather low resolution for a display that huge?

---

### Post by LowSky on 2009-07-13
720 is HD... according to this you should get HD out of the card
[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)

> # Dual RAMDACs (up to 400 MHz) for display resolutions up to and including 2048×1536 @ 85Hz
# Integrated NTSC/PAL TV encoder support resolutions up to 1024×768 without the need for panning with built-in Macrovision copy protection
# DVD and HDTV-ready MPEG-2 decoding up to 1920×1080i resolutions


try going to nvidia-settings and fixing the resolution.. 

open a terminal and type ```
gksu nvidia-settings
``` dont forget to save the setting to the Xorg folder and reboot to make sure

also make sure you drivers in Vista are updated correctly


things to also consider, HD video on older technology sucks, for a good viewing experince you need a processor that is over 2Ghz or with 2 or more cores. 1Gb of RAM is also very low, HD files are huge and need space for caching 2GB or more is really not optional.

this is coming form experience building HTPC's, don't expect miracles out of older computer equipment for high definition media.

---

### Post by iampriteshdesai on 2009-07-13
> **MikeTheC said:**
> Isn't that a rather low resolution for a display that huge?
yes, 1520x720, is quite low, but that is the best I can get in Ubuntu

---

### Post by iampriteshdesai on 2009-07-13
> **LowSky said:**
> 720 is HD... according to this you should get HD out of the card
[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)




try going to nvidia-settings and fixing the resolution.. 

open a terminal and type ```
gksu nvidia-settings
``` dont forget to save the setting to the Xorg folder and reboot to make sure

also make sure you drivers in Vista are updated correctly


things to also consider, HD video on older technology sucks, for a good viewing experince you need a processor that is over 2Ghz or with 2 or more cores. 1Gb of RAM is also very low, HD files are huge and need space for caching 2GB or more is really not optional.

this is coming form experience building HTPC's, don't expect miracles out of older computer equipment for high definition media.
Funny.. few yrs ago this would have been a killer PC :P
anyways, are you sure that this is a Graphics card issue? I would hate it if there was something wrong with my LCD..
I will reinstall Vista today to check my theory.
I just saw a Youtube video... Google Chrome "What is a browser" video :)
It is very funny..
I hope that the matter gets solved..
will update things today evening.
thanhyou.

---

### Post by The Toxic Mite on 2009-07-13
24' is pretty excessive IMHO (not if you plan on using it for a mini-cinema though :p)

---

### Post by iampriteshdesai on 2009-07-13
> **The Toxic Mite said:**
> 24' is pretty excessive IMHO (not if you plan on using it for a mini-cinema though :p)
Ofcourse I use it to watch Cinema... Trust me it is awesome!
I used to hate those black bars above and beneath the screen.

---

### Post by Hells_Dark on 2009-07-13
> **The Toxic Mite said:**
> 24' is pretty excessive IMHO (not if you plan on using it for a mini-cinema though :p)

I strongly disagree. It's not that big and really confortable.
I have one for more than one year, I'll never buy a smaller one anymore.
Maybe a 22 or 23 but…

---

### Post by iampriteshdesai on 2009-07-13
> **Hells_Dark said:**
> I strongly disagree. It's not that big and really confortable.
I have one for more than one year, I'll never buy a smaller one anymore.
Maybe a 22 or 23 but…
Do you have any ideas to make good use of the screen real estate? If the only thing you are using is a browser, theen it gets boring... but Great otherwise... I hope my blank screen problem stops and I get to enjoy things!

---

### Post by .Maleficus. on 2009-07-13
> **iampriteshdesai said:**
> Ofcourse I use it to watch Cinema... Trust me it is awesome!
I used to hate those black bars above and beneath the screen.
I think he was commenting on 24**'** meaning 24 feet, not 24 inches ;).

And like the others said, you'll need a new graphics card to handle that resolution.  You can pick up a 9500GT for around $75 on Newegg or an HD4650 for about $50 (USD).  Either would be a fine choice.

---

### Post by iampriteshdesai on 2009-07-13
> **LowSky said:**
> 720 is HD... according to this you should get HD out of the card
[http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html)




try going to nvidia-settings and fixing the resolution.. 

open a terminal and type ```
gksu nvidia-settings
``` dont forget to save the setting to the Xorg folder and reboot to make sure

also make sure you drivers in Vista are updated correctly


things to also consider, HD video on older technology sucks, for a good viewing experince you need a processor that is over 2Ghz or with 2 or more cores. 1Gb of RAM is also very low, HD files are huge and need space for caching 2GB or more is really not optional.

this is coming form experience building HTPC's, don't expect miracles out of older computer equipment for high definition media.
Will reinstall Vista and Ubuntu now... hope to give details in few hrs... fingers crossed... hope things work this time round!

---

### Post by iampriteshdesai on 2009-07-13
> **.Maleficus. said:**
> I think he was commenting on 24**'** meaning 24 feet, not 24 inches ;).

And like the others said, you'll need a new graphics card to handle that resolution.  You can pick up a 9500GT for around $75 on Newegg or an HD4650 for about $50 (USD).  Either would be a fine choice.
You sure, that my current Graphics card won't be able to handle it??
Evenrything was fine till FIFA 2008 :(
I just got this new monitor.. will have to wait to get a new Graphics card.

---

### Post by iampriteshdesai on 2009-07-13
> **.Maleficus. said:**
> I think he was commenting on 24**'** meaning 24 feet, not 24 inches ;).

And like the others said, you'll need a new graphics card to handle that resolution.  You can pick up a 9500GT for around $75 on Newegg or an HD4650 for about $50 (USD).  Either would be a fine choice.
Rest assured, I have a 14 inch monitor... 
God! I'd start a cinema hall if I get a 24 ft :)

---

### Post by pwnst*r on 2009-07-13
i have a 24" HP and i love it.  basically if you can afford a 24", you can afford a low end but new gfx card.

have fun.

---

### Post by Grenage on 2009-07-13
> "I used to hate those black bars above and beneath the screen"

You're still going to get them in some films :)

---

### Post by pwnst*r on 2009-07-13
indeed, get used to it and read up on [ratios]("http://en.wikipedia.org/wiki/Aspect_ratio_(image)").

---

### Post by The Toxic Mite on 2009-07-13
> **.Maleficus. said:**
> **I think he was commenting on 24' meaning 24 feet, not 24 inches ;).**

And like the others said, you'll need a new graphics card to handle that resolution.  You can pick up a 9500GT for around $75 on Newegg or an HD4650 for about $50 (USD).  Either would be a fine choice.

Damnit! #-o I knew I would get " and ' mixed up! :lolflag:

EDIT: But the OP used **'** to mean inches :-k

---

