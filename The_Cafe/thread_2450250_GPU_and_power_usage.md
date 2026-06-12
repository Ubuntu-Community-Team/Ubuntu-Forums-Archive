---
title: "GPU and power usage"
date: 2020-09-10
forum: The Cafe
---

### Post by mastablasta on 2020-09-10
I've been following the news a bit about high end cards as well as new APU chips from AMD and intel. ? i started thinking about it when i was checking for a replacement card (not needed yet, but just exploring what is out there) and when i read a comment "you might need a nuclear reactor to run latest RTX". a joke for sure, but still a lot of electricity needed just to have nicely moving models and textures in games.  i use a low end GT 730 which is also good enough for some light gaming and older games. 

when i check all these comparisons, reviews and news and then when i look at the prices the one thing that doesn't really make much sense to me is power usage of these dedicated chips. Especially if you look at the lower end. the APUs might be slower by only 30-40% yet the use a fraction of dedicated card power. what puzzles me is why the dedicated cards are not more energy efficient? why do they need so much power compared to APU. I would expect them to be in 15W maybe even 20W. not 30W or 47W and more.

in the past this made more sense, since the chips on APU were not nearly close to performance of dedicated cards. but it doesn't make that much sense anymore. i mean the Ryzen U chips  use less than 30 watts in total. only slightly better GPU card than the one included on CPU needs nearly twice the power. AMD is particularly wasteful if you look at the TDP of cards compared to nvidia. the intel is close to entry GPU chips as well with a lot less power needed. 

and look at the real performance in games - there is a difference sure, but not as much as the power difference. if you add to that that even with dedicated GPU you still need enough RAM it makes less and less sense. 

anyone else noticed this? or am i reading the power usage wrong?

---

### Post by CharlesA on 2020-09-10
They don't build the dedicated cards to sip power, especially with the amount of memory and cores each of them has.

For example, the GT 730 you have is rated at 38 Watts and has 1GB of memory with 384 Shading Units running at 900Mhz 
[https://www.techpowerup.com/gpu-specs/geforce-gt-730.c1988](https://www.techpowerup.com/gpu-specs/geforce-gt-730.c1988)

The GTX 1060 6GB card I have now is rated at 120W and has 6GB of memory with 1280 Shading Units running at 1506 MHz base or 1706MHz with boost.
[https://www.techpowerup.com/gpu-specs/geforce-gtx-1060-6-gb.c2862](https://www.techpowerup.com/gpu-specs/geforce-gtx-1060-6-gb.c2862)

The RXT 3070 7GB card I was thinking about getting is rated at 220W and has 8GB of memory with 5888 Shading Units running at 1500 MHz base or 1750 MHz with boost.
[https://www.techpowerup.com/gpu-specs/geforce-rtx-3070.c3674](https://www.techpowerup.com/gpu-specs/geforce-rtx-3070.c3674)

So basically, the newer GPUs have more cores, more memory, and faster core and CPU speeds, which increases power consumption as well as heat.

Comparing the GTX 1060 to the GT 730, the 1060 has 3 times as many Shading Units and an increased speed of about 600 MHz and 6 times the video memory.

---

### Post by Shibblet on 2020-09-10
You're not wrong.  The new GTX 3090 is supposed to require an 850w Power Supply in order to function at it's peak.  That doesn't mean that it is going to draw that much power all of the time, of course.  It does mean that it may need it to keep up the frame rates when the scene requires a lot to draw.

My biggest problem with high-powered graphics cards is that they keep getting more and more powerful... and it may not be necessary.  Software optimization could really change this trend.  If game/software designers were to really utilize some of the features provided by OpenGL/Vulkan (or even DirectX 9/10/11/12), that tie into hardware functions, could very much optimize your visuals and frame rates.

The best concept of this is "Mesh Simplification / Polygon Reduction."  This reduces the amount of polygons in the background, and increases them in the foreground for better detail up close, and less detail needed in the back.  For example:  A character "profile scene" focuses on the main characters face.  With Mesh Simplification, you can add more polys to the character in the foreground, for higher detail.  Also, the mountains in the background can have less polygons to reduce the number in the scene.  And the mountains could be blurred using a "Depth of Field," as a post processing effect, for even less poly use.

Most of the newer game engines have these processor features built in.  Unreal 4 and 5 utilize these very well.

---

### Post by poorguy on 2020-09-10
Wow how things have changed since I built a gaming tower for my **Flight Simulator X** back in my **Windows Vista **days.

Best I could afford back then still works great for **Flight Simulator X.**

[https://www.theregister.com/2008/02/04/review_amd_radeon_hd_3870_x2/](https://www.theregister.com/2008/02/04/review_amd_radeon_hd_3870_x2/)

[IMG]https://www.tweaktown.com/images/content/1/3/1326_11.jpg[/IMG]

---

### Post by mastablasta on 2020-09-11
yes if you compare card to car they do show improvement.

but if you compare APU to GPU card is where there is a big gap in power drawn and GPU performance gain. i ahven't even looked at mobile chips here (liek MX230 which i think is similar to GT730 or 1030)

my GT 730 has 2 GB ram. so that would mean the 1060 as example would have 3x memorry, 3x shading units and increased speed. what about if you compare it to GTX 1650? it has 75 W tdp and 4 GB ram. is the performance then about half of 1060? well anyway this power increase on cards seems kind of reasonable in most cases.

but the lower end GPU cards vs the APU chips and mobile discrete chips is where the difference is quite bit in power consumption. nvidia models on lower end have low power consumption but AMD's is through the roof if you ask me. quite strange since the vega series are descent chips and have low TDP.

i read about higher end, though i can't really afford them. actually i can afford, but it seems a bit pointless investment. you loose half the pice in maybe less than a year. the power consumption is a bit too big for me. maybe as an on sale "older model". still the performance differences are really hard for me to see. you need all other accompanying hardware to maybe be able to notice it. it's kind of like having the latest 8K TV, but most programs don't even have HD :) and on top of that my eyesight is so bad i usually can't really see the difference between regular and HD.

the small differences measured in few FPS are not noticeable to me. i doubt many people notice these differences. when they do these so called real tests they should do them in a way that people are set in front of the screen and play same game with same settings. all screens are same model and all PC have same components. and they don't know which card they are using. then ask to grade the experience as well as say which chip they thought they were using. i really wonder what the result would be. oh and there should also be a control. maybe a lower end medium range card.

by the way, it became really difficult to shop for a GPU card these days :)

---

### Post by Shibblet on 2020-09-14
Does anyone remember the 3DFx Voodoo 6?  The one that required an external power unit?

---

### Post by mastablasta on 2020-09-15
"it's generating too much heat. "put more fans on it." :)

i used to have fanless cards for quite some time. and if i remember correctly most were fanless. even the good ones.

---

### Post by TheFu on 2020-09-15
I only buy fanless GPUs. Have been for a very long time. The last GPU with a fan was using AGP.
I don't game. Most of my systems would be happy with a $5 PCI GPU.

Someone paying $350-$2500 for a GPU, care less about power consumption than performance. BTW, nVidia does many GPUs for over $2500 that you can buy.

Vote with your money, cash, choices.

---

### Post by poorguy on 2020-09-15
> **TheFu said:**
> I only buy fanless GPUs. Have been for a very long time.
Most of the graphics cards I purchase these days is because the fan quit working. 
I can purchase most of those non working graphics cards for $10.00 or less usually.
I remove the old non working fan or fans and sometimes the shroud and zip tie 80mm fans to the heatsink.
Somewhat unorthodox way of repair although works well and I'm cheap.

> **TheFu said:**
> 
I don't game. Most of my systems would be happy with a $5 PCI GPU.
I'm not a gamer although I like Flight Simulators and need real graphics cards.

---

### Post by mastablasta on 2020-09-16
APU chips are quite good these days. sure not as good as latest GPU, but still if you look at the power consumed... i mean they ran Crysis on Ryzen 4000 and took the fan off the CPU. that says a lot.

why are fans for GPU so expensive anyway? these fans should cost 2, 3 EUR, maybe 5 if they are custom made. wholesale price of normal fans is usually a couple of cents. with speed controller maybe 1-2 EUR.

---

### Post by poorguy on 2020-09-16
> **mastablasta said:**
> APU chips are quite good these days. sure not as good as latest GPU, but still if you look at the power consumed... i mean they ran Crysis on Ryzen 4000 and took the fan off the CPU. that says a lot.

I've got computers with processor graphics and yes they are quite good.

> **mastablasta said:**
> 
why are fans for GPU so expensive anyway? these fans should cost 2, 3 EUR, maybe 5 if they are custom made. wholesale price of normal fans is usually a couple of cents. with speed controller maybe 1-2 EUR.

The only reason I can think of is they know users paid a lot for their graphics card and will pay whatever the cost of the new replacement fan when needed what other reason would there be.

---

