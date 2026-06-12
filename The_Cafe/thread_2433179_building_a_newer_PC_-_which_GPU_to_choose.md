---
title: "building a newer PC - which GPU to choose"
date: 2019-12-15
forum: The Cafe
---

### Post by mastablasta on 2019-12-15
my old frankenstein PC is having issues with freezing. not sure exactly what is wrong but i suspect it is the old GPU card. i can't get a replacement (AGP card), so i was thinking of building a new PC. i will be using a smaller frame - looks like Cooltek Coolcube Maxi is a good choice as it can use standard ATX PSU and i can fit 2 large HDD drives in it - just what i have. it also has room for the CPU cooler. 

i need help with the rest of the build meant for light gaming/video editing. i plan to pack it with 16GB RAM and use some new components from the old machine. but i can't decide on the GPU. options i came down with:


[LIST]
[*]Ryzen 5 2600 + nvidia 1050 ti,
[*]Ryzen 5 2600 + nvidia 1650 or
[*]Ryzen 5 2600+ any other AMD entry card -- which one?;
[*]or Radeon vega 11 (on ryzen 2400G).
[/LIST]

From what i read, AMD cards (550, 560, 570) need more power and their performance is still weaker than nvidia. i would like to keep the wattage and heat down as well as price. for some reason their (AMD) price is the same here as nvidia or higher. size is also a factor. 

current monitor is old with VGA cable and max resolution 1680x1050. might change it within next 2 years. depending on financial situation.

motherboard i was thinking Asus Prime B450M-A which i am still investigating, but it does seem it will work with linux. it's an older board. it supports 3xxx series of CPU but i see i get enough performance with older cheaper CPU model. however if anyone has another, better suggestion, i will listen.

OS will be Kubuntu (preferably LTS). i guess it will need a fresh install using GPT and secure boot or whatever is needed with the latest UEFI boards.

importantly  - all should be easy to install and use = plug and play vs. plug and pray and fix and... i don't have the patience any more. an option was also to get an older HP machine but they have really specific PSU with low wattage. so a 1050 card would first in them (maybe) but it will all be quite borderline.

---

### Post by CatKiller on 2019-12-15
> **mastablasta said:**
> From what i read, AMD cards (550, 560, 570) need more power and their performance is still weaker than nvidia. 

This isn't true in general. At a given price point both AMD and Nvidia have cards that perform about the same and have about the same performance-per-Watt. The confusion is because of the high end: AMD don't have anything to compete with something like the RTX 2080 Ti, which costs over £1000 and uses nearly 300 W. You aren't interested in the high end, though, so you've got plenty to choose from. 

Phoronix do regular benchmarks of Linux tasks, including Linux gaming, and they include power consumption in their results. [Here's one](https://www.phoronix.com/scan.php?page=article&item=amd-rx5500xt-linux&num=1) that covers the range that you're likely to be interested in. [Here's another](https://www.phoronix.com/scan.php?page=article&item=amd-ryzen5-3400g&num=1) that looks at integrated graphics. 

>  current monitor is old with VGA cable and max resolution 1680x1050. might change it within next 2 years. depending on financial situation. 

This is going to be an issue. Modern GPUs aren't going to have an analogue output, and converters don't pass through the EDID that will let the resolution be detected automatically. You're likely to have to manually fiddle with xorg.conf to get the right resolution. 

> OS will be Kubuntu (preferably LTS).

For a small form factor build that isn't primarily aimed at gaming, the Ryzen integrated graphics would be fine. However support for them wasn't available in 2018, so you're either going to have to forgo the LTS so that you can use the later software that came with the later releases, or manually add the later hardware enablement and Mesa stack to your 18.04 base, or wait till 20.04. The 3000 APUs are apparently easier to get working smoothly than the 2000 APUs, even on the newest graphics stack; their launch was quite rough. 

Otherwise, pick whichever card fits into your case, and financial and power budgets. From an 18.04 base you're going to need to use the graphics driver ppa if you choose anything Turing. Pascal works with the proprietary driver in the normal repositories, I think. I don't know that much about the AMD side for discrete graphics.

My 2700X / 2080 Ti build was entirely painless with Kubuntu 18.04, FWIW.

---

### Post by TheFu on 2019-12-15
Nothing more to add, new GPUs don't support VGA. You'll need a new monitor. Perhaps buying that first would be best?  Get HDMI, DP, and DVI-i inputs to avoid lots-o-issues.  More display port would be better.

I fought the EDID battle using an active DVI-i -to- VGA converter with an nVidia 1030 GPU on a Ryzen 2600.  These converters work at well-known resolutions - 1080 and 720. Don't expect 1050 to work under any situation.  The 1030 I got is fanless. All the higher cards had fans, which means they required more power, made more noise, made more heat, etc.  There are lots of fake GPUs out there. Buy from a reputable retailer.  Any recent generation nVidia with VGA support is a fake.  The 1030 doesn't have VGA, none of the 10xx does.

---

### Post by oldfred on 2019-12-15
I made a mistake when I built this system.
Monitor has VGA and DVI-D in and new motherboard had HDMI & Displayport out. oops.
I ended up using my old nVidia GT620. Later found that Intel Haswell video was slightly better than GT620 and found a cable that converted to DVI-D. 

I do not game so video from CPU is all I need anyway.

---

### Post by TheFu on 2019-12-15
I do legacy gaming on a ...
```
CPU:       Quad core Intel Core i5-8250U (-HT-MCP-) cache: 6144 KB 
Graphics:  Card: Intel UHD Graphics 620

```
And did the same on a Core i3-5015U previously.  Sim City, C&C, and most old games don't really care.

---

### Post by mastablasta on 2019-12-16
if this was for me, i would be OK with APU graphics. and for a bit of gaming the 1030 is strong enough and as mentioned has a fanless version available.

i heard about RX5500 but it will take a while before we see it here. and 1650 has some reduced prices here now (maybe beause SUPER is out there?!). RX570 is weaker (based on tests), while 580 is much more expensive and heats up.  the 1000 series is getting old and is not that much cheaper than 1650 at current price. i will be buying from reputable dealer. if something is wrong or if i don't like it they will exchange it or return the money at no cost.

I was actually planning on using DVI adapter to get the monitor working. however this got me thinking, i might need a new monitor sooner than expected. 

but what should i do with the old working one? can it be used as a monitor on laptop? usually laptops can easily output to VGA as many projectors have VGA ports. the also still come with VGA port on the side, so maybe i could use it for laptop. but i am not sure how this goes with newer ones which often have Display Port or HDMI. i hate to see things that are working well go to waste. i wouldn't be even thinking about new PC yet, if this old box was not freezing. it was more than good enough for the tasks we were doing on it. so the idea is to replace this one with a new laptop and use the parts for a new desktop for my son. he will buy it as he was saving money for it for a "gaming PC" for 3 years now. plus we could use something a bit stronger for some light video editing and cutting.

---

### Post by TheFu on 2019-12-16
I haven't seen a laptop with a VGA port in a few years.  Think pre-2015.  HDMI-to-VGA adaptors at HiDef definitions are pretty good. Again, that's 720p@60hz and 1080i@30hz or 1080p@60hz.  I've always had to exactly specify those resolutions to get projectors working.

---

### Post by CatKiller on 2019-12-16
> **mastablasta said:**
> but what should i do with the old working one? can it be used as a monitor on laptop?

It's not that it won't work, it's that it won't work without some fiddling and you were specifically trying to avoid fiddling. 

It's (probably) just a couple of lines in xorg.conf that we're talking about, but they're lines that you'd be less likely to need with digital signalling. Someone might be unfortunate and still need to do it with digital signals; manufacturers still cheap out on EDID if they're particularly crappy.

---

### Post by TheFu on 2019-12-16
> **CatKiller said:**
> It's not that it won't work, it's that it won't work without some fiddling and you were specifically trying to avoid fiddling. 

It's (probably) just a couple of lines in xorg.conf that we're talking about, but they're lines that you'd be less likely to need with digital signalling. Someone might be unfortunate and still need to do it with digital signals; manufacturers still cheap out on EDID if they're particularly crappy.

My experience with this:  Connected the laptop HDMI-out --> HDMI-to-VGA converter ($15), set the output to 1080p@60hz using lxrandr, and never have any issues.  There are terrible HDMI-to-VGA converters, but if you get one with high reviews, it should be fine. No need to do EDID stuff.  

When I had to do EDID and xorg.conf stuff, the DVI-i output was used --> DVI-i -to- VGA adaptor,  --> KVM switch with VGA only,  --> existing VGA connection to a 1200p monitor where I **wanted** 1200p resolution.  With 1080p resolution, everything "just worked".  I wanted 1200p resolution.
The DVI-i -to- VGA adaptor specifically claimed 1200p resolution support, but the EDID information it was telling the GPU was 1080p. The adaptor didn't pass through the EDID from the monitor.  
Was already using the HDMI-out to another monitor which is/was working fine.  No KVM-switch in that connection.

HDMI-to-VGA adaptors basically work at all the standard resolutions and refresh rates.

---

### Post by CatKiller on 2019-12-16
> **mastablasta said:**
> he will buy it as he was saving money for it for a "gaming PC" for 3 years now. plus we could use something a bit stronger for some light video editing and cutting.

Video editing is orthogonal to gaming; any potato with enough RAM can do video editing, and faster machines will do it faster. With sufficient RAM lots of cores is what will make video encoding faster, and having those cores as fast as possible. Ryzen is a great platform for that. 

Since it now apparently *is* a machine that's being built for gaming, you'll need to look at the games that you'll want to play on it. A machine that can play Overwatch well is not the same as a machine that can play Cyberpunk 2077 well. For performance gaming, lots of cores makes little difference; it's the strength of the GPU that will be the bottleneck first. Again, depending on the game: you can play as much Stardew Valley as you want with any GPU that you have.

It's worth recognising that if they've been saving for a gaming PC for three years then you don't want it to be bad at gaming. That means that you're going to have to land quite high up on the performance charts for the GPU. Many games that they'll want to play will also require Windows.

Edit to add: if they're comfortable with only using the games that will work on Linux, the Feral ports are only generally tested with Nvidia cards. AMD cards have got adequate performance in Vulkan *now*, but they didn't when Feral started using Vulkan for their ports.

---

### Post by CatKiller on 2019-12-16
> **TheFu said:**
> The adaptor didn't pass through the EDID from the monitor.  
Yep, that's the issue. Some will stay completely silent, and some will make something up. You've probably seen enough of my posts on the subject to know that getting the HorizSync and VertRefresh values for the monitor from whatever source is *usually* sufficient information to have everything otherwise work automatically.

---

### Post by CatKiller on 2019-12-16
> **mastablasta said:**
> i heard about RX5500 but it will take a while before we see it here. 

You probably realised, but in case you didn't: the purpose of that link wasn't specifically the introduction on the first page, but instead for all the *other pages* that have benchmarks of a whole bunch of different cards from both manufacturers from entry level to the higher mid-range.

1080p is a reasonable proxy for your current monitor, and is likely to be the resolution of the one you replace it with. In general you'll be trying to get a 60 fps minimum, and which card you pick will determine how many settings you'd need to turn down to get that.

---

### Post by mastablasta on 2019-12-17
> **TheFu said:**
> I haven't seen a laptop with a VGA port in a few years.  Think pre-2015.  HDMI-to-VGA adaptors at HiDef definitions are pretty good. Again, that's 720p@60hz and 1080i@30hz or 1080p@60hz.  I've always had to exactly specify those resolutions to get projectors working.

that is correct. i just checked the laptop i was thinking of getting: Dell Inspiron 3583 - it comes with i3–8145U/ 8GB RAM / SSD256GB/15,6FHD and ubuntu 18.04 preloaded. so we can know that Linux will work on it. it only has HDMI 1.4b output. i would prefer they stick 512 GB SSD drives in these laptops, but i guess in linux 256 GB is enough as well. we can keep static  data on external drive and backup is on server anyway. not sure how 256 Gb is considered enough in Win 10. i have about 380 GB taken at work PC and it has basically only essentials on it (ERP, Office, data from office)  along with 3 years of emails archived. and they put 256 GB drives in gaming machines these day. gaming! so windows is about 60 Gb and then restore points can push that up to 100 GB. games are 40-50 Gb big nowadays so that's 2 or 3 games you can add. even the PS4 has 1 TB drive in it.

> **CatKiller said:**
> Video editing is orthogonal to gaming; any potato with enough RAM can do video editing, and faster machines will do it faster. With sufficient RAM lots of cores is what will make video encoding faster, and having those cores as fast as possible. Ryzen is a great platform for that. 

Since it now apparently *is* a machine that's being built for gaming, you'll need to look at the games that you'll want to play on it. A machine that can play Overwatch well is not the same as a machine that can play Cyberpunk 2077 well. For performance gaming, lots of cores makes little difference; it's the strength of the GPU that will be the bottleneck first. Again, depending on the game: you can play as much Stardew Valley as you want with any GPU that you have.

It's worth recognising that if they've been saving for a gaming PC for three years then you don't want it to be bad at gaming. That means that you're going to have to land quite high up on the performance charts for the GPU. Many games that they'll want to play will also require Windows.

Edit to add: if they're comfortable with only using the games that will work on Linux, the Feral ports are only generally tested with Nvidia cards. AMD cards have got adequate performance in Vulkan *now*, but they didn't when Feral started using Vulkan for their ports.

well the idea is wife gets a new laptop, kid will use parts from current wife PC to get a descent machine. our current "gaming" machine is my 15 year old PC, which has a Single core AMD Athlon, 4GB ddr2 RAM and GT 730. it still has winXP on the other disk for COD modern warfare, Doom 3, Civ 3 and some other games that i didn't want to fiddle with in linux. we mostly play source based games (CS:GO, portal, l4d, HL2, HL...), some open source ones (q2 and q3 engine based) and many GOG games (far cry 1 & 2, F.E.A.R., Oblivion, ArxFatalis, UT2004). Some work on native ports (Jedi Academy, OpenMW...). so i am convinced that anything will be a huge improvement to this. the idea here is that they will be able to play at say low or medium setting the new games and old games at high/ultra setting. i can see now that 1650 will achieve this as well as AMD RX 570. However the issue here is that we have skewed prices. The RX570 4 GB is no longer available here. we have the 8 GB version but that one is 200 EUR (compared to nvidia's 1650 - 165 EUR). I saw the old prices for RX 570 4 Gb and they were also set at 160 EUR. our market is small and prices are often off here. this can be seen with basic good as well. for example orange juice is more expensive than in Austria which is about 40 mins drive from my town, while average salaries are about 50% lower.

anyway 1650 costed 240-260 EUR (depending on the brand) and they now reduced it down to 170 EUR, probably because SUPER version came out.

for AAA titles windows is necessary anyway. i think the kid can then start saving for new hard disk + windows 10 and they can install those later if they feel that would be necessary. Another option we also talked about is if they want to instead use a console. PS4 is being phased out now and you can get them for 200 EUR with a couple of good games. then they have other games on sale as well.

in any case they can't do a lot of gaming anyway. i limit them to 1 hour/day during weekend or vacations and max 30 min during the week if grades are good and homework is done. worked well so far. and it takes them a while before they can play through one game :twisted: 

if i was making this PC for my self it would get a ryzen 5 and 1030 (or similar) or just use the onboard GPU. it seems like these are good enough for most things. the games i play are mostly strategy games and old FPS (which still had some stories in them).

---

### Post by bernard010 on 2019-12-17
Ryzen Threadripper 2990WX 32-Core 3.0 GHz AMD X399 chipset
  Dual Quadro RTX 6000 24 GB
   128G DDR4 3200MHz
    960GB SSD + 6TB HDD
      360mm Liquid Cooler
         6 RGB Fans
           1000W 80 Plus Gold P.S.
GO FOR THE GUSTO GAMING AT THE NEXT LEVEL.

---

### Post by Autodave on 2019-12-23
Beware of the size of whatever GPU you decide on: make sure that it will actually fit in your case!!!!  My RTX 2070, for instance, is a HUGE card: very long and takes 2 slots.  In fact, it is so big that there is a built in reinforcement to the motherboard to prevent the weight of it from damaging the MB.

---

### Post by kurt18947 on 2019-12-23
> **CatKiller said:**
> 

<snip>
For a small form factor build that isn't primarily aimed at gaming, the Ryzen integrated graphics would be fine. However support for them wasn't available in 2018, so you're either going to have to forgo the LTS so that you can use the later software that came with the later releases, or manually add the later hardware enablement and Mesa stack to your 18.04 base, or wait till 20.04. The 3000 APUs are apparently easier to get working smoothly than the 2000 APUs, even on the newest graphics stack; their launch was quite rough. 

Otherwise, pick whichever card fits into your case, and financial and power budgets. From an 18.04 base you're going to need to use the graphics driver ppa if you choose anything Turing. Pascal works with the proprietary driver in the normal repositories, I think. I don't know that much about the AMD side for discrete graphics.

My 2700X / 2080 Ti build was entirely painless with Kubuntu 18.04, FWIW.

I'm playing with 18.04 & HWE now. I have an Asrock AS350M mobo & Ryzen 3 2200G APU. It didn't work at all with vanilla 18.04 using the integral GPU. I had an older AMD card so installed that, set the UEFI to use an external video card and it worked very well. I've recently wanted to experiment with dual monitors and the stand-alone AMD card will not support that. I installed the 18.04 HWE and it works - most of the time. Just a few minutes ago I got a pause of perhaps 30 seconds. I thought I had a hard lockup but the PC became responsive. I looked at DMESG and was greeted with many lines of red text. Here is the end of the output:
> [COLOR=#ff0000]VM_L2_PROTECTION_FAULT_STATUS:0x00000000
[42746.187937] amdgpu 0000:38:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:3 pasid:0, for process  pid 0 thread  pid 0)
[42746.187939] amdgpu 0000:38:00.0:   in page starting at address 0x000080010b7d0000 from 27
[42746.187940] amdgpu 0000:38:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
[42746.187947] amdgpu 0000:38:00.0: [gfxhub] VMC page fault (src_id:0 ring:24 vmid:3 pasid:0, for process  pid 0 thread  pid 0)
[42746.187949] amdgpu 0000:38:00.0:   in page starting at address 0x000080010b7d2000 from 27
[42746.187951] amdgpu 0000:38:00.0: VM_L2_PROTECTION_FAULT_STATUS:0x00000000
[42746.189700] [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring gfx timeout, but soft recovered[/COLOR]


I did try a 19.10 live USB and that seemed to work better. I may play with this some more over the holiday weekend. Right now though I'd probably install 19.10 and hope for a smooth upgrade to 20.04 if using an AMD APU processor.

---

### Post by bunny9000 on 2019-12-25
With Linux depends on the games your son wants to play. When I used to play video games it was easy. I'd find a game of the period that I liked or was upcoming and look at the recommended specs then build the pc around that and add a little more for a few more years use for future titles. I think 1920x1080 is still a common resolution.

Some triple A games work with Linux, but you'll have to do your homework to find out which ones otherwise the safe bet is windows. Nvidia was the stronger player for Linux driver wise.

Most of the games in the Linux library can run on pretty ancient hardware so for a Linux only gaming PC using only the games in the Linux library you don't need a strong PC.

That six core ryzen should be fine for games and video work, but graphics - Solid 60fps is always nice. Games need high cpu speed rather than lots of cores. Video rendering needs lots of cores and cares less about max cpu speed.

---

### Post by mastablasta on 2020-01-05
Thank you all for the help. took me a long time to put it all together. the issue was that motherboard instructions said to attached the mobo first, then add the CPU. but CPU had a cooler that needed bottom support to be attached, so i had to take it apart again (after scratching my head for some time)  and then reassemble it all. thank you for the monitor advice. i got a Samsung curved monitor on sale (reduced from 200 to 100 EUR). it came with a HDMI cable but the card wouldn't read it for some reason. since the chassis doesn't have any beeper, i thought i assembled something wrong. then i suspected the ram (since the ram was not on QVL, but the manufacturer said they supported the board...). finally i used the HDMI cable from my RaspberryPi and it worked. i got into UEFI bios, disabled fast boot and  boot from USB. all went smoothly form then on with Kubuntu 18.04.3. it all just worked (hardware seems to be fully compatible for now). drivers installed well. i tested it out a bit on CS:GO. The curved monitor... i am not convinced yet with it, though it does make you feel more "in the game". now i need to get some adapter for the old monitor. maybe later i will be bale to use two. but it all depends how the new table will with with all components.

I took many components based on price. they were on after x-mas sale. i realise the are a bit older tech being slowly phased out i guess. but the rig still provides massive improvement over any of my current setups which used a decade old tech.  anyway here is what i got:

[LIST]
[*]Ryzen 7 2700 WraithSpire
[*]Asus Prime B450M-A
[*]16 GB RAM (2 x 8 GB - G-SKILL Ripjaws V 16GB (F4-3200C16D-16GVKB)
[*]ASUS Dual GeForce GTX 1650, 4GB, GDDR5
[*]SAMSUNG monitor C24F390FHU
[/LIST]

i used the rest of components from the old PC and the upgrades i did there - about 2 or 3 years old 1 TB Seagate HDD drive and WD green used for storing pics. and the PSU was upgraded in the beginning of 2019. it's a 80 bronze 550W, i think LC power.

i would prefer to get AMD 5500 XT for the drivers sake, but they are not selling them here yet.

to me this PC is massive overkill, but my kid bought it and he was saving for 2 years for it. so i can kind of understand he wants the best he could get. plus he will share it with my wife i guess and both plan to do some video editing. :-k

To me one of the Ryzen 5 with the GPU on the CPU would be more than enough and it would save quite a bit of money. because one, as mentioned in posts above, you really need windows 10 to run latest games (so that means more money needed for the OS), two because new games are expensive so you need even more money for those (oldest games that pop up on sales will work with this kind of APU setup), three because i don't game as much and don't have the time for it. Linux does what i need which is why i switched to it. also AMD has good opensource drivers support, so that's a big plus.

as for me i will (for now) continue to use my old single core Athlon PC (dualboot XP and Kubuntu) and do some light gaming and internet browsing. lately i was installing some old games and i am surprised to see that installers often fail, but moving the installed game from Windows partition to Linux just makes it work. i had this issue with Hearts of iron 2, Company of heroes and Star Trek Elite force 2. so hopefully more older games pop up on GOG. at least their installer usually works well.

---

### Post by CatKiller on 2020-01-05
> **mastablasta said:**
> Thank you all for the help. took me a long time to put it all together. the issue was that motherboard instructions said to attached the mobo first, then add the CPU. but CPU had a cooler that needed bottom support to be attached, so i had to take it apart again (after scratching my head for some time)  and then reassemble it all. 

Yep, sounds familiar :) 

>  
[LIST]
[*]Ryzen 7 2700 WraithSpire
[*]Asus Prime B450M-A
[*]16 GB RAM (2 x 8 GB - G-SKILL Ripjaws V 16GB (F4-3200C16D-16GVKB)
[*]ASUS Dual GeForce GTX 1650, 4GB, GDDR5
[*]SAMSUNG monitor C24F390FHU
[/LIST]
 

That's a nice machine. It should play pretty much anything you throw at it for quite a while.

Of potential interest is that the monitor has a variable refresh rate, so you can keep the vsync to prevent tearing even if the framerate drops below the magic 60 fps. Nvidia have their own proprietary implementation (because nvidia) but they did add support for some monitors that use AMD's solution once variable refresh rates became part of the official display standards. I don't know if that's one of the supported monitors or not, and it's not something I've played with, but it's something that might be worth exploring.

---

### Post by mastablasta on 2020-01-05
this monitor supports AMD solution for sync. we will see how it goes later on with some more demanding games. otherwise to me 30 fps is good enough :) . i was actually checking and couldn't find a monitor that would declare proudly to support the nvidia solution. at least not at this shop and at price range below 150 EUR.

---

### Post by CatKiller on 2020-01-05
> **mastablasta said:**
> this monitor supports AMD solution for sync. we will see how it goes later on with some more demanding games. otherwise to me 30 fps is good enough :) . i was actually checking and couldn't find a monitor that would declare proudly to support the nvidia solution. at least not at this shop and at price range below 150 EUR.

The nvidia solution has an active hardware module that needs to be included in the monitor. That - and licensing, I'd imagine - make the G-Sync models more expensive than the FreeSync ones.

---

