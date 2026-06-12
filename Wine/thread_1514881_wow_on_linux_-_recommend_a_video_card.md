---
title: "wow on linux - recommend a video card?"
date: 2010-06-21
forum: Wine
---

### Post by matamoscas on 2010-06-21
I currently have a ati 4600, and it works fine.

My problem is that when i originally bought the card, I wanted a quiet card, so it has only a heatsink on it. That works ok normally, but when i actually game, the static cooling is not enough.

Thus, I need to buy a proper one with a fan.

My question to the pros is should I go for an ATI or Nvdia video card?

I am not terribly disappointed with my ATI card, and the driver functions.

But, from what i have read in the past, Nvidia is more friendly to linux? Is that still true?

Thanks in advance.

---

### Post by nemiux on 2010-06-21
I'm not sure about the idea are Nvidia cards better than ATI, but I'm using nvidia 8800 GT and had not a single problem. Normal cooling is enough, and it doesn't lag on ultimate graphics. Of course you could get a much newer one like 9600 GT with 1gb of video memory, but I just said what I'm experiencing right now :)

---

### Post by Breambutt on 2010-06-22
You could also approach the issue from this angle: your case doesn't have sufficient airflow for a passively cooled graphics card.

I also wouldn't put much value on the stock heatsinks on passively cooled cards, you might get away with just by buying something like [http://www.arctic-cooling.com/catalog/product_info.php?cPath=2_&mID=105&language=en](http://www.arctic-cooling.com/catalog/product_info.php?cPath=2_&mID=105&language=en) and a "turbo module" for that which is a pair of small attachable/detachable fans when passive doesn't cut it. I've got those on a 7900GT and a 9800GTX, but it's just an example. Both of the cards were fan-cooled and after installing those heatsinks (without fans) they ran about 15 celsius degrees lower on idle loads.

WoW isn't exactly the most power hungry game either, I think I ran it just fine with the 7900GT with settings maxed out, years ago. NVIDIA cards might still be a safer bet, but not necessarily worth buying a new card. The main "competition" between ATI and NVIDIA seems to be around the hardware decoding of HD video these days, but someone else might want to educate us on that matter since I've never actually owned an ATI card.

---

### Post by asdfoo on 2010-06-28
People tend to experience less problems with nvidia as they continue to have more stable drivers than ATI, which can be a bit of a gamble.

---

### Post by beastrace91 on 2010-06-28
> **asdfoo said:**
> People tend to experience less problems with nvidia as they continue to have more stable drivers than ATI, which can be a bit of a gamble.

+1 nVidia is the only real choice you have currently for gaming on Linux.

~Jeff

---

### Post by nusse on 2010-06-28
> **beastrace91 said:**
> +1 nVidia is the only real choice you have currently for gaming on Linux.

~Jeff

-1

I have a ATI card and the latest ATI catalyst drivers have come a long way ...

---

### Post by hikaricore on 2010-06-28
> **nusse said:**
> -1

I have a ATI card and the latest ATI catalyst drivers have come a long way ...

I'm not so sure brand new users are willing to take the chance.
Nvidia is tried and true and while ati might be catching up I'd never buy one of their cards without trying it first.

---

### Post by cwwilson721 on 2010-06-28
I'm well known on another forum for my Linux and 3d. 

Use any card you wish, as long as you understand:

[LIST=1]
[*]Nvidia is easy
[*]Ati has Open Source drivers available (Not as robust as the proprietary ones)
[*]Intel is OK if you want built-in performance
[/LIST]
As far as for WoW/wine, I use a NV9600GSO, and get 60FPS in Dalaran. The BIG limiting factor in WoW isn't the video (but it DOES play into it). CPU power and memory affect it alot too, as does your internet connection.

With all the above taken into consideration, I would get (Or upgrade to at a minimum):

[LIST]
[*]Nvidia 9600 GS or above (NOT a 210 or 220!), with at least 768MB DDRIII onboard (NO TURBOCACHE!!!!) SLI/XFire not neccesary (And have caused issues in WoW) And check to make sure your power supply can handle the new card (PCIx connector(s), amps on the +12V rails, etc). As you have found, passive doesn't cut it for 3d gaming. There are quiet fans out there. Research and Google are your friends
[*]4GB main memory.  Even though wine/WoW are 32bit, the more memory, the better
[*]Dual core CPU, but 4 core is better (Even though World of Warcraft does not use more than one core, the extra cores REALLY help).
[*]TURN OFF SHADOWS in Video Settings, and Anti-aliasing. Those two factors alone will kill your FPS in wine/WoW. All the other effects, set as you wish, but keep in mind that the farther to the right, the lower the FPS are. In 25man, I have mine at min, and my FPS is still usuable. I'd rather have lower eye-candy, and still zerg Festergut, than pretty and dead.
[/LIST]
Let me know how it goes.

---

### Post by hikaricore on 2010-06-29
Shadows have no effect on my fps what-so-ever.
AA is a given though.

---

### Post by Metrop021 on 2010-06-29
frankly pretty much any nvidia card from the last decade will run wow. the older ones might require you to play on pretty low settings but it'll still run smoothly. i've used an ancient nvidia 6000 series to play, and right now i use an nvidia 7300 le. both work fine

---

### Post by cwwilson721 on 2010-06-29
You can also haul 40,000 pounds of sand in a Yugo. But a semi would do it in one trip, and not break the vehicle.

Recommendations were asked, and I gave the best answer I could, as a long running WoW/wine/Linux enthusiast.

Yes, you CAN play WoW on a 6xxx Nvidia chip. But WHY? And he wants to up from his current Ati card. So my recommendation still stands

---

