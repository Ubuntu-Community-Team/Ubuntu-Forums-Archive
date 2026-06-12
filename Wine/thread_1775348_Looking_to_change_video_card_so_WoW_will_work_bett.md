---
title: "Looking to change video card so WoW will work better- help?"
date: 2011-06-04
forum: Wine
---

### Post by MissCrunk on 2011-06-04
I currently have an ATI Technologies Inc Radeon 350 [Radeon 9800 Pro] video card. WoW runs beautifully through Wine, EXCEPT for the unfortunate fact that I can't get above 9 fps. (I say WoW runs beautifully because I have low latency, the cinematics run flawlessly, the graphics don't blink or black out, and the client never crashes.) I did my research and found out that Linux and my video card don't like each other.

Long story short, I'm not very computer savvy, and I have NO idea what video card I should get. I heard Nvidia works really good with Linux, but again, I have no idea what I should get. My budget is small, and I have no problem running WoW on low settings, I just want the decent amount of FPS I was able to have while using Windows. ( I don't raid, I just PvP.) 

Im assuming that more information about my computer is needed in order to answer this question, but Im not sure what you'll need, so please tell me what info I need to post and how to get it and I'll do it asap.

Thank you so much!

---

### Post by cwwilson721 on 2011-06-04
As long as you have a PCIeX16 (either 1.0 or 2.0) slot available on your motherboard, your options open up considerably.

[Start here by looking at the Nvidia side]("http://www.tomshardware.com/reviews/best-graphics-card-game-performance-radeon-hd-6670,2935-7.html") (will give you a good idea what is 'better' than what):


The general rule of thumb on that chart is 3 'levels' mean real upgrade. If a new card is only 1 level above the current one, there is not a ton of difference. But 3 means a big difference.

To boil it down:

More cores, more memory bit width is best.
Ex: A 8400GS, while cheap, is HORRIBLE because of low cores and memory width.
My 9600GSO is about the least I would get: 48 cores, 192bit

There are some pretty good deals on gt 250's and 450 GTS out there.

Just remember, after you install the card in your system, you have to install the 'current' drivers from Admin > Additional Drivers (Even tho it says they are NOT activated in 11.04, they actually are)

Also, when you get into 'higher power' video cards, you also run into 'higher power' requirements. You need a power supply that can handle the new card. Not only in the amp rating on the 12v rail, but also that it has the connector(s) you need.

So, it might not just be a video card 'swap', but also a PSU swap. too.

---

### Post by Tweak42 on 2011-06-05
> **MissCrunk said:**
> I currently have an ATI Technologies Inc Radeon 350 [Radeon 9800 Pro] video card. WoW runs beautifully through Wine, EXCEPT for the unfortunate fact that I can't get above 9 fps. (I say WoW runs beautifully because I have low latency, the cinematics run flawlessly, the graphics don't blink or black out, and the client never crashes.) I did my research and found out that Linux and my video card don't like each other.


If your video chip is really a R350 Radeon 9800 Pro, then it's very likely a AGP video card.  AGP architecture predates PCI Express as the Radeon 9700/9800 series is over 8 years old.  You need to find out more about the rest of the hardware in the system before you can even consider upgrades.  There maybe more pitfalls such that it would be worth it to get a entirely new system.

FYI: I played Wow classic using a Radeon 9800 Pro, but upgraded around 2005 because it was to slow driving a 19" LCD.

---

### Post by cwwilson721 on 2011-06-05
There are some 9800 PCI-E cards, tho. But odds are, it's AGP

---

### Post by cascade9 on 2011-06-05
> **cwwilson721 said:**
> There are some 9800 PCI-E cards, tho. But odds are, it's AGP

I've never seen a 9800 PCIe. I dont think they made any. 

If the OP has an AGP system, abotu the only cards that would be worth looking at would be a 6600GT/6800GT, and maybe some of the newer AGP radeon HD cards. Anything else would be a step backward. 

A 6600GT should be that much faster than a 9800Pro, even if the 9800Pro had running closed source linux drivers (which it doesnt, and thats why WoW in WINE is so poor)  

Getting any of those cards could mean a power supply upgrade as well, like cwwilson721 suggested.

---

### Post by cwwilson721 on 2011-06-05
If I remember correctly, ATi put out a 4650 AGP card w/DDR2...One sec...

Yep. [Newegg has them, even]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814102851&nm_mc=OTC-Froogle&cm_mmc=OTC-Froogle-_-Video+Cards-_-Sapphire+Tech-_-14102851"). That card is about on par with the 7900 series Nvidia cards. (Much more power than ANY Nvidia AGP card.)

Even better, it's still supported by ATi/AMD (for now)

Look at the chart I posted the link to earlier for comparisons to other vidcards/chips.

---

### Post by Tweak42 on 2011-06-06
To help the OP find out more about their computer hardware, search the Ubuntu Software Center for "System Profiler and Benchmark".  

Key need to know info will be found under:
[LIST]
[*]Processor
[*]Total memory
[*]PCI devices - (Host bridge and VGA controller)
[*]DMI Board name and vendor
[/LIST]

If the board does support PCI Express, there should be a port somewhere listed in the PCI Devices.  Even better, if there is a vendor and board model under DMI, then google the specs for a full break down.

---

### Post by mips on 2011-06-07
1. What is your budget.
2. We need to confirm if you have an AGP or PCIe video card slot on your motherboard.

Give us your PC or motherboard Brand & model details and we can comfirm 2 above. I think the 9800 was only available in AGP but I know some of the 9x00 series cards did come out with PCIe so it's best we verify what interface you have. I do however suspect you have an AGP interface.

With AGP the latest nVidia cards you can run are the 7x00 series and for AMD/ATI you have the HD 4650 & 4670.

A nVidia 6600GT would not be much of an improvement over your current card, you will have to look at a 7600GT and above. With nVidia the second digit in the model number (7x00) dictates how powerfull the card is. If you can find one get a 7950GT AGP.

You can compare your card with others here [http://www.gpureview.com/show_cards.php?card1=34&card2=190](http://www.gpureview.com/show_cards.php?card1=34&card2=190)

---

### Post by Dlambert on 2011-06-07
Theres a 4670 AGP card, but Nvidia has better support and performance in Linux. Gts 450 for me, works amazing.

---

