---
title: "Opinion of CrossOver?"
date: 2009-10-21
forum: Wine
---

### Post by ngrieb on 2009-10-21
Hi,
I was looking to buy CrossOver for Linux gaming, but I wanted to first get people's opinions of it.

Is it worth it? Does it really do that much better than WINE? Any complaints?

---

### Post by edin9 on 2009-10-21
> **ngrieb said:**
> Hi,
I was looking to buy CrossOver for Linux gaming, but I wanted to first get people's opinions of it.

Is it worth it? Does it really do that much better than WINE? Any complaints?

You can get a free 7-day trial of Crossover Games [here]("http://www.codeweavers.com/products/cxgames/download_trial/"). 

WINE is better IMO.

---

### Post by Ms_Angel_D on 2009-10-21
I purchased crossover games, for some things it is better, also they do have a list of software/games which they guarantee will work, if you have any issues with the software/games you do get support for it.

I have been happy with crossover and have used it for quite a few different games. Your mileage may very depending on the apps/games your trying to run.

---

### Post by beastrace91 on 2009-10-21
Worth every penny (and some of those pennies get donated back to the Wine project sooo)

Check the link in my sig for my full review of the product ;)

~Jeff

---

### Post by u235sentinel on 2009-10-22
Been using it since the lame duck challenge last year.  7.2 was pretty good and 8 is great!

I used to run everything under WINE but honestly it sometimes took a lot of work to get things working cleanly.  Crossover games and office has been great.  Even though I got it for free through the challenge, I'm looking at purchasing it for a couple computers at home.

I've been switching my kids games from their windows partition to Ubuntu the last few months.  What doesn't work I've warned them will be replaced with something similar that runs either natively or through crossover games.

I recommend it!

---

### Post by ngrieb on 2009-10-22
I attempted to run the demo, but immediately became frustrated with it when trying to install the HL2: Game of the Year pack. It has multiple CD's, and after searching for hours, I found no way to eject CD one and load CD2 (wine eject, is much easier). 

If anyone knows how to do this let me know please... I only have 6 more days...

Also another game (Dark Messiah) I originally had working under WINE stopped working under WINE 1.1.31, and this game seems to have the same problem under Crossover (luckily got this installed cause it was a DVD). Is there a compatibility issue if both are installed? 

So far I'm not too impressed, but perhaps someone can help me along :confused:

---

### Post by beastrace91 on 2009-10-23
Download them via Steam? Or try running ```
wine eject
``` to force the disc to eject. Or if that doesn't work install the game through plain Wine and then copy the install over to you Codeweavers.

What issues is Dark Messiah giving you? I have that installed and it runs pretty flawlessly for me.

~Jeff

---

### Post by ngrieb on 2009-10-23
[LEFT](1) wine eject didn't work for Crossover, I did give it a try
(2) and on WINE 1.1.31 Dark Messiah gives me an error prompt reading:

dxdllreg.exe has encountered problems...sounds like Direct X? Could it be that the install comes with Direct X and it did/didn't install?

As far as I know WINE runs a DirectX pipe to OpenGL or something odd like that, so I suppose it doesn't need to be installed??? How would I get rid of any DirectX installs then if that is the case?

(3) If the game exists in WINE, how do I get Crossover to recognize it?

I'm running 8.10 with a Radeon X1650 Pro btw.

Thanks a lot. 
[/LEFT]

---

### Post by edin9 on 2009-10-23
> **ngrieb said:**
> [LEFT](1) wine eject didn't work for Crossover, I did give it a try
(2) and on WINE 1.1.31 Dark Messiah gives me an error prompt reading:

dxdllreg.exe has encountered problems...sounds like Direct X? Could it be that the install comes with Direct X and it did/didn't install?

As far as I know WINE runs a DirectX pipe to OpenGL or something odd like that, so I suppose it doesn't need to be installed??? How would I get rid of any DirectX installs then if that is the case?

(3) If the game exists in WINE, how do I get Crossover to recognize it?

I'm running 8.10 with a Radeon X1650 Pro btw.

Thanks a lot. 
[/LEFT]


If you're running an ATi card with WINE forget it. You've got more chance of finding the holy grail than getting it to work properly.

---

### Post by beastrace91 on 2009-10-23
> **edin9 said:**
> If you're running an ATi card with WINE forget it. You've got more chance of finding the holy grail than getting it to work properly.

Odds are that is the source of your issues (game play wise) the ATI drivers are horrid.

To get your Files from a Wine install to Codeweavers just copy the Steam folder from your ~/.wine/drive_c/Program\ Files to ~/.cxgames/winxp/drive_c/Program\ Files (Make sure you have Steam installed in the winxp bottle first)

Also remember you can file for support for ANY game. And for ones that are "officially support" you are guaranteed a response. Remember to do this - a large part of what you are paying for with Codeweavers is not just the software but the support that comes with it as well (and they have great support staff)

~Jeff

---

### Post by ngrieb on 2009-10-23
"You've got more chance of finding the holy grail than getting it to work properly."

LMAO... holy grail. I had a 6800XT but it fried itself for some reason. My computer is really old, so I needed a cheap card to last me about  2 years till I get a new awesome Linux machine. COD2 should install, I have read, but for some reason doesn't. And that's about all I have tried to put on WINE, other than FIrefox.

With that said, I have HL2 working quite flawlessly, and CSS only dies because I'm using the Windows wireless networking driver for my hardly supported Atheros wireless card.

---

### Post by edin9 on 2009-10-23
> **ngrieb said:**
> &quot;You've got more chance of finding the holy grail than getting it to work properly.&quot;

LMAO... holy grail. I had a 6800XT but it fried itself for some reason. My computer is really old, so I needed a cheap card to last me about  2 years till I get a new awesome Linux machine. COD2 I read should install, I have read, but for some reason doesn't. And that's about all I have tried to put on WINE, other than FIrefox.

With that said, I have HL2 working quite flawlessly, and CSS only dies because I'm using the Windows wireless networking driver for my hardly supported Atheros wireless card.

Yeah you may get one or two games that work, but I'm talking about consistency. I used to have that exact card on 8.10 and believe me, you will hit so many problems you will begin to hate ATi in no time. Since I switched to nVIDIA, the only problems I've ever faced with WINE are it's own limitations. Save yourself a lot of time and trouble and switch to a cheap nVIDIA card. You really, really won't regret it.

---

### Post by ngrieb on 2009-10-23
I understand, but my issues are with the software it seems, because I can't even start the game to see my poorly preforming graphics card :) . 

BTW I dual boot with Windows 7 RC (really to play COD2) and Dark Messiah runs very poorly on it (for my old fart computer at least).

---

### Post by MadnessRed on 2009-10-25
> **edin9 said:**
> If you're running an ATi card with WINE forget it. You've got more chance of finding the holy grail than getting it to work properly.

I have an ATi 3200 on my laptop and 3850 on my desktop. Can play Jedi Knight and all the source games fine. Most my other games don't seem to work on wine.

I installed my graphics driver using the cchtml.com tutorials.

However I have a question?
If the ATi driver is soo bad, what is better for my desktop.
ATi HD3850 512mb or nVidia GeForce 6300LE.

Also when I boot into windows :/. What nVidia card will give me a similar performance to my 3850, I am currently looking at an 8800. Needs to be DX10 though.

---

### Post by edin9 on 2009-10-25
> **MadnessRed said:**
> I have an ATi 3200 on my laptop and 3850 on my desktop. Can play Jedi Knight and all the source games fine. Most my other games don't seem to work on wine.

I installed my graphics driver using the cchtml.com tutorials.

However I have a question?
If the ATi driver is soo bad, what is better for my desktop.
ATi HD3850 512mb or nVidia GeForce 6300LE.

Also when I boot into windows :/. What nVidia card will give me a similar performance to my 3850, I am currently looking at an 8800. Needs to be DX10 though.

I can't speak for an ATi card like yours that is still actively supported. I have heard that the latest Catalyst's are much better than they used to be. I was making that statement about Catalyst 9.3 which pre-HD2000 cards have to use if they want any kind of ok 3D acceleration, as the opensource Radeon drivers aren't there yet. If I had to choose between an HD3850 or a GeForce 6300LE, I would go for the HD3850 for the simple reason that is a much more powerful card. However if you were seriously considering at an 8800 then you won't be disappointed, those cards pack a lot of punch, especially in SLi.

---

### Post by beastrace91 on 2009-10-26
Performance wise the ATI-3850 is a stronger card than the nVidia 6300LE.

How ever on Linux depending on the drivers this may or may not hold true.

Typically a good rule of thumb the ATI 2000 series equates well to the nVidia 8000 series (so 3000 would equate to the 9000). Right now the nVidia card on the market with one of the best performance:cost ratios would be the 260 - its a solid card at a decent price (last I checked)

~Jeff

---

### Post by MadnessRed on 2009-10-26
> **beastrace91 said:**
> Performance wise the ATI-3850 is a stronger card than the nVidia 6300LE.

How ever on Linux depending on the drivers this may or may not hold true.

Typically a good rule of thumb the ATI 2000 series equates well to the nVidia 8000 series (so 3000 would equate to the 9000). Right now the nVidia card on the market with one of the best performance:cost ratios would be the 260 - its a solid card at a decent price (last I checked)

~Jeff

ok, ill look into it. Many thanks for the advice

---

### Post by Sages on 2009-11-19
i have tryed crossover games an found that is really wasnt any better then wine.. yes it was a better front end but over all wine was the winer. 
I also bought a cedega membership and it was the worse thing i wasted my cash on! wow played slower in it and i tryed everything to get it working well and when i went to the forum, the last post was 2005 like... wow they do well eh.

KEEP WINE! hell linux is freedom! why pay to work games and such?!

---

### Post by jrusso2 on 2009-11-20
> **Ms_Angel_D said:**
> I purchased crossover games, for some things it is better, also they do have a list of software/games which they guarantee will work, if you have any issues with the software/games you do get support for it.

I have been happy with crossover and have used it for quite a few different games. Your mileage may very depending on the apps/games your trying to run.

It really isn't a guarantee.  They have a email forum where you post questions and they try to give you suggestions but they do give up pretty easily and put it out of site.

---

### Post by beastrace91 on 2009-11-20
> **Sages said:**
> i have tryed crossover games an found that is really wasnt any better then wine.. yes it was a better front end but over all wine was the winer. 
I also bought a cedega membership and it was the worse thing i wasted my cash on! wow played slower in it and i tryed everything to get it working well and when i went to the forum, the last post was 2005 like... wow they do well eh.

KEEP WINE! hell linux is freedom! why pay to work games and such?!

I think this is more than a little misguided. Link in my sig gives a solid overview of what both CXGames and Cedega offer.

~Jeff

---

### Post by Ms_Angel_D on 2009-11-20
> **jrusso2 said:**
> It really isn't a guarantee.  They have a email forum where you post questions and they try to give you suggestions but they do give up pretty easily and put it out of site.

Well they just released a new version of Crossover to fix bugs which customers had reported, when you pay for the software you get better attention paid to the problems you report.

---

### Post by jrusso2 on 2009-11-20
I have it like I said you get some attention but guarantee's no.

They gave up on my issue two years ago and I have not heard anything else about it since.  Guess it went to the developers.

---

### Post by u235sentinel on 2009-11-20
> **jrusso2 said:**
> I have it like I said you get some attention but guarantee's no.

They gave up on my issue two years ago and I have not heard anything else about it since.  Guess it went to the developers.

I have yet to see guarantee's for any software product.  Even Micro$oft limits their guarantee to the purchase price of the product according to their EULA's.

---

