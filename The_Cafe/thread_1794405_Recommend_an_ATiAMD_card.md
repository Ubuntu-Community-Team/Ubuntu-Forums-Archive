---
title: "Recommend an ATi/AMD card?"
date: 2011-07-01
forum: The Cafe
---

### Post by Dustin2128 on 2011-07-01
I'm thinking of going AMD in my next build so I can give my 9600 GT to my little brother, and because I've recently wanted to get a recent AMD/ATi card so I can mess with the open drivers and see what's possible with a real card with open source drivers. I play a handful of games (Fallout 3, Oblivion, World of Warcraft and morrowind) in wine, but I do a good deal of graphics card intensive stuff. I'd like something targeted towards mid-high end with full OpenGL 4 support and enough power to make my laptop owning friends cry. Basically this: Is the 5/67xx series good enough or should I go for the 5/68xx+ range? Oh, one more thing, I'd like support for more than 2 monitors whether it's through linking to on board ATi graphics or just the sheer capability of the card itself.

Oh, and I know it looks like I'm spamming the cafe, but I intended the firefox thread to die days ago and the nuclear thread went viral.

---

### Post by kaldor on 2011-07-01
Oh cool, I was gonna start a thread like this myself.

I was PC shopping today. The salesman at the store happened to be a Linux (Debian) user and let me use a Natty liveUSB on whichever PC I wanted. To my sadness, all of the PCs with an AMD card didn't want to boot. As soon as the desktop began to load, flickering and then a hard lockup with just a mouse cursor on a black screen with some text.

On topic though, I wouldn't recommend an AMD card if you use Linux for graphics-intensive stuff. The open source drivers are fine, but lack for gaming. The proprietary drivers are apparently quite flaky.

---

### Post by cariboo on 2011-07-01
It took the ATI devs 4-5 years to create stable drivers for XP, which is a static platform. With Xorg being a moving target, I don't hold a lot of hope that they will ever create proprietory drivers that actual are stable.

Hopefully the devs working on the open source drivers do a better job, until then, I'll continue using nvidia graphics adapters.

---

### Post by kaldor on 2011-07-01
> **cariboo907 said:**
> I'll continue using nvidia graphics adapters.

Apparently, NVIDIA [_will not be supporting wayland_]("http://www.phoronix.com/scan.php?page=news_item&px=ODc2Mg") :(

Dunno if it's true, though.

---

### Post by el_koraco on 2011-07-01
I wouldn't bother.

---

### Post by Dustin2128 on 2011-07-01
Well, I do have good experiences with an on board ATi radeon 1150. Full compositing, a few relatively graphics intensive games all with open drivers. Really the thing I want is the ability to use 3+ monitors without 2 video cards- but I don't know if you can do SLI with an on board video card.

---

### Post by kaldor on 2011-07-01
> **Dustin2128 said:**
> Well, I do have good experiences with an on board ATi radeon 1150. Full compositing, a few relatively graphics intensive games all with open drivers. Really the thing I want is the ability to use 3+ monitors without 2 video cards- but I don't know if you can do SLI with an on board video card.

How is WINE gaming with the free (default) drivers?

---

### Post by Dustin2128 on 2011-07-01
> **kaldor said:**
> How is WINE gaming with the free (default) drivers?

Haven't tried wine gaming, just urban terror and warsow.

---

### Post by Bandit on 2011-07-01
Dust, I read what you was looking for. But I want recommend something I havent tested. I have a Radeon 4670 and 4850 that both work very well, but may not offer the features your looking for. However if you want a awesome video card at a reasonable price, I am using a MSI Cyclone nv460GTX. Its *FAST...* and also runs cool. Currently 31ºC. Also screams in 3D games.

---

### Post by Drenriza on 2011-07-01
the name ATI is the "old" AMD GPU division. Today ATI is called AMD, to clear a lot of confusion that people had with ATI/AMD.

I have not tried AMD GPU on a linux system. But the card themselves are a good product. So based on card performance and $. I would definitely recommend a AMD GPU.

---

### Post by kaldor on 2011-07-02
Maybe we should start a list of AMD cards that will work smoothly without any tweaking.

---

### Post by beew on 2011-07-02
> **Drenriza said:**
> 
I have not tried AMD GPU on a linux system. But the card themselves are a good product. So based on card performance and $. I would definitely recommend a AMD GPU.

So if I understand you correctly  you are making a recommendation without the most important piece of information, namely Linux support??? 

If you haven't  tried it on Linux what do you base the assertion that it has good performance on? Windows?

---

### Post by el_koraco on 2011-07-02
> **Drenriza said:**
> I have not tried AMD GPU on a linux system. 

Enough said.

---

### Post by Bandit on 2011-07-02
> **Drenriza said:**
> the name ATI is the "old" AMD GPU division. Today ATI is called AMD, to clear a lot of confusion that people had with ATI/AMD.

I have not tried AMD GPU on a linux system. But the card themselves are a good product. So based on card performance and $. I would definitely recommend a AMD GPU.
They switched between the 5000 series and 6000 series to the new name. Still same hardware and same company thats been making the chips for a few years now since they bought ATI out. No since on being picky..

---

### Post by unixlinuxos on 2011-07-02
it better if you use a nvidia 460 gtx or higher but i reccomend ati radeon 6850 and up they dominate 3d graphics :)

---

### Post by JDShu on 2011-07-02
> **Dustin2128 said:**
> I'm thinking of going AMD in my next build so I can give my 9600 GT to my little brother, and because I've recently wanted to get a recent AMD/ATi card so I can mess with the open drivers and see what's possible with a real card with open source drivers. I play a handful of games (Fallout 3, Oblivion, World of Warcraft and morrowind) in wine, but I do a good deal of graphics card intensive stuff. I'd like something targeted towards mid-high end with full OpenGL 4 support and enough power to make my laptop owning friends cry. Basically this: Is the 5/67xx series good enough or should I go for the 5/68xx+ range? Oh, one more thing, I'd like support for more than 2 monitors whether it's through linking to on board ATi graphics or just the sheer capability of the card itself.

Oh, and I know it looks like I'm spamming the cafe, but I intended the firefox thread to die days ago and the nuclear thread went viral.

- oss drivers have the best multi-monitor suppport out of all the linux graphics options (in my experience, and not through linking - I just use the DVI and VGA outputs).
- oss drivers don't have OGL 4 (yet).
- oss drivers are quite lacking for gaming performance
- catalyst has multimonitor support but is not as smooth as the oss drivers in my experience
- catalyst runs games fine
- switching  between oss and catalyst is essentially impossible, if you want to mess with both I suggest dual booting

I can say that seeing the oss drivers evolve is a lot of fun and it's impressive how quickly they're improving. They're also the most stable option imo. Catalyst just works for me, but I'm not willing to guarantee it since I've heard stories.

---

### Post by Drenriza on 2011-07-03
> **Bandit said:**
> They switched between the 5000 series and 6000 series to the new name. Still same hardware and same company thats been making the chips for a few years now since they bought ATI out. No since on being picky..

I never said it still wasn't the same company. They just changed name from ATI to AMD on both the CPU and GPU divisions

---

### Post by Drenriza on 2011-07-03
> **beew said:**
> 
If you haven't  tried it on Linux what do you base the assertion that it has good performance on? Windows?

You don't need a OS like Windows, Linux, Mac OS X to make a test of the hardware calculation capacity, durability, stability and so on.

---

