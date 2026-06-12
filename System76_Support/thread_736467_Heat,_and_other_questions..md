---
title: "Heat, and other questions."
date: 2008-03-26
forum: System76 Support
---

### Post by einnar on 2008-03-26
HEAT : How hot do these laptops get? Is it one of them that you can't hold on your lap for a while and work, or is the cooling pretty good on them?

MINT: Any problems with the ubuntu/76 drivers in Linux Mint?

VIDEO : What's the difference between the 8600M GS, 256MB 8600 GT, and 512MB 8600GT performance-wise? I'm not up on my nvidia cards, and the various sites on the web I tried to find answers in weren't real helpful.

MEMORY : If I put a 32bit system in, instead of 64-bit, will it still read 4GB of memory? I know there is a point that one reads more than the other, and can find that answer in windows easily enough, but would like it clarified for Linux.

GAMING : Just curious how well games like WoW play on the Serval. :)


Thanks in advance. Been going back and forth between Ubuntu and Mint for about 8 months now, and love it. I just need something more portable. :)

---

### Post by heartburnkid on 2008-03-27
On the video issue, take a look here: [http://www.tomshardware.com/2008/03/05/the_best_gaming_graphics/page8.html](http://www.tomshardware.com/2008/03/05/the_best_gaming_graphics/page8.html)

It's not very detailed, but it should give you an idea of the relative performance.

---

### Post by thomasaaron on 2008-03-27
> HEAT : How hot do these laptops get? Is it one of them that you can't hold on your lap for a while and work, or is the cooling pretty good on them?

I'm not really sure how to give you an objective answer on that one. I use my Gazelle on my lap all the time and it doesn't bother me. In my experience, when people ask that question, they are usually more sensitive to heat than I am. I think our current line-up runs pretty cool. But I'll let some customers weigh in on it.

> MINT: Any problems with the ubuntu/76 drivers in Linux Mint?

The System76 Driver does not run on Linux Mint. However, it is an open source Python app. So, if you want to have a look under the hood to see how we patch different things, you are free to do so.

> VIDEO : What's the difference between the 8600M GS, 256MB 8600 GT, and 512MB 8600GT performance-wise? I'm not up on my nvidia cards, and the various sites on the web I tried to find answers in weren't real helpful. The one with 512MB cache is able to cache more data for processing by the GPU than the 256MB version. Therefore it is faster.

> MEMORY : If I put a 32bit system in, instead of 64-bit, will it still read 4GB of memory? I know there is a point that one reads more than the other, and can find that answer in windows easily enough, but would like it clarified for Linux.

This is a largely misunderstood subject. Here is what I know of it. A 32-bit operating system CAN see 4GB of memory. The problem is, there are other components in the computer that take up some of that memory. So if you have 4GB of memory cards in the computer, the onboard memory-consuming devices get first dibs on the full 4GB. Generally, by the time the OS gets around to the Memory Cards, it only has about 3.2GB of potential left. So that is all it sees.

So, to get the full capability out of 4GB of memory cards, you must use a 64-bit OS.

> GAMING : Just curious how well games like WoW play on the Serval. 

It has more than enough muscle to burn through just about any game. Yet, I'm not a gamer and don't know much about what is involved and what people are playing on the Serval. So, ummm, 76ers! Help!

---

### Post by einnar on 2008-03-28
> **thomasaaron said:**
> I'm not really sure how to give you an objective answer on that one. I use my Gazelle on my lap all the time and it doesn't bother me. In my experience, when people ask that question, they are usually more sensitive to heat than I am. I think our current line-up runs pretty cool. But I'll let some customers weigh in on it.


Good to hear. I have a dell and an hp, and both get too warm to keep on my lap/knees. 

[QUOTE=thomasaaron]
The System76 Driver does not run on Linux Mint. However, it is an open source Python app. So, if you want to have a look under the hood to see how we patch different things, you are free to do so.
[/quote]

I'm not at all conversant with python, so I'll probably just stick with ubuntu, but thanks. :)  (Open source rocks, even if you don't understand it. hehe)

[QUOTE=thomasaaron]
 The one with 512MB cache is able to cache more data for processing by the GPU than the 256MB version. Therefore it is faster.
[/quote]

Thanks. I see by the chart that the 2 models are slightly different too, so that helps fill in the last blanks.

[QUOTE=thomasaaron]
This is a largely misunderstood subject. Here is what I know of it. A 32-bit operating system CAN see 4GB of memory. The problem is, there are other components in the computer that take up some of that memory. So if you have 4GB of memory cards in the computer, the onboard memory-consuming devices get first dibs on the full 4GB. Generally, by the time the OS gets around to the Memory Cards, it only has about 3.2GB of potential left. So that is all it sees.

So, to get the full capability out of 4GB of memory cards, you must use a 64-bit OS.
[/quote]

Makes sense to me. Thanks again. 

[QUOTE=thomasaaron]
It has more than enough muscle to burn through just about any game. Yet, I'm not a gamer and don't know much about what is involved and what people are playing on the Serval. So, ummm, 76ers! Help!
[/quote]


:popcorn:

---

### Post by einnar on 2008-03-28
*bump*

Anyone else with more info?

Thanks.

---

### Post by Pethegreat on 2008-03-30
I have a pangolin vaule, and I don't expirence any issues with heat. The cooling system design is nice. On my laptop they use heat pipes(copper tubes filled with a heat conducting gas) to conduct the heat from the processor and 8600gt to one fan the back. The bottom right corner gets warm when I run it for a time, but it is not uncomfortable. 

WOW should play fine. Wine will slow it down a tad, but computers today should have enough juice to make up for the performace loss due to wine.

---

### Post by compholio on 2008-03-30
It sounds like you have only a couple that you do not have satisfactory answers:

> **einnar said:**
> HEAT : How hot do these laptops get? Is it one of them that you can't hold on your lap for a while and work, or is the cooling pretty good on them?

I have a SERP3 (serval) and I've <only> managed to make it hot when running both Mathematica and MATLAB at the same time.

> **einnar said:**
> GAMING : Just curious how well games like WoW play on the Serval. :)


I don't play WoW, but I know you can play Supreme Commander on it :)  Wine supposedly plays WoW, so I imagine you'd be good.

---

### Post by Royal_Pwner on 2008-03-30
on the subject of linux mint:

I got 0 hardware detection whatsoever when I tried teh livecd. It may not be a good idea.

---

### Post by perce on 2008-03-31
I have an old Darter, so my information may not be of much interest for you. I usually go between 46C and 50C, except when I watch flash videos (youtube) and I use a webcam on skype. Then it can go up to 62C or a little more. In the case of th webcam it's definitely skype's fault because I don't have any temperature issues when I use it on aMSN. On Feisty I got almost 5C less, so I think there is a way to reduce the temperature a bit by working on the configuration, but It's out of my knowledge.

This is however the temperature of the CPU reported by ACPI, the external temperature never reaches an unpleasant level. Only sometimes, and after many hours, it become warm on the bottom left corner (I suspect something related to the wireless). A very nice feature is the opening of the fan on the side instead of on the bottom, so that I can safely put the laptop on the bed or on the couch without risk of overheating it.

---

### Post by einnar on 2008-03-31
Exactly the kind of help I was hoping to get! Thanks much.

I'm going to be in Southern Texas over the summer, and won't be in air conditioning. I'm told it can get to 100+ F, and didn't want to be working down there in the great outdoors in my truck with the thing in my lap with no AC in that kind of weather. (Much less have it get too hot from the temps, if it got hot to start with.)

I have no idea if our lodgings have AC or not, but knowing the company, they might not. I was hoping to game at night with it, but again, heat was a concern. Where the heat vent is, it shouldn't be an issue, and I suppose I can always put it up on a mesh stand with a fan beside it.

Thanks again!  :)

---

