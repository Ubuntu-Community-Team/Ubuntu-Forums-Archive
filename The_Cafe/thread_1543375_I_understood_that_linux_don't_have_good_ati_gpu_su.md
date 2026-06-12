---
title: "I understood that linux don't have good ati gpu support is it true?"
date: 2010-08-01
forum: The Cafe
---

### Post by aviramof on 2010-08-01
I have been told that Linux or ati drivers don't have good gpu support to the parallel technology of ati that is smiler to nvidia pure video is it true? 

And that is why when i see movies there via linux there are times when the picture jumps a bit and it's not entirely smooth throughout the entire movie? 

And if it's true is there any hope to fix it in maverick?

Thanks in advance.

---

### Post by cariboo on 2010-08-01
The closed source ATI drivers are produced by AMD, Canonical/Ubuntu has nothing to do with them except repackaging them, you may be better off asking you questions relating to drivers [here]("http://forums.amd.com/devforum/").

---

### Post by Dustin2128 on 2010-08-01
eh, it's not as good as nvidia but it's getting better. As long as you have a supported card, you should be fine. Open drivers are also improving.

---

### Post by slooksterpsv on 2010-08-01
The ATI drivers have worked great for me, I haven't really had any issues. I would recommend trying it out see how it fairs for you then choose from there.

I have a IGP HD 3200, worked great, IGP HD 4200, works great, and an ATI Radeon 4850 - works great as well.

---

### Post by MrNatewood on 2010-08-01
if you have a multi-core processor try using mplayer-mt:
[https://launchpad.net/~longinus00/+archive/mplayer-mt/](https://launchpad.net/~longinus00/+archive/mplayer-mt/)
You need to add the PPA through System->Administration->Software Sources
And then do an update.

---

### Post by Sophont on 2010-08-01
Depends on what you want from your graphics card.

2D acceleration (office, browsing, some effects) - no problem. Works great (in my experience - particular cards might have problems). Don't need the proprietary driver at all. In fact in my experience the open source driver is already better for this.

3D acceleration (mainly games, etc...) - here things become muddy. There is the proprietary driver. Most features. Kinda works. Not great. Legacy cards no longer supported. Doesn't come close to the NVidia proprietary driver.

The newish open source drivers have been quickly gaining features or 3G acceleration. Legacy cards are relatively well supported by now. New cards still catching up. You can't really play games modern games with the open source driver yet. I hope it will be good enough by 10.10. There's almost weekly progress reports on Phoronix that sound promising enough.

The reason for the fast improvement in the ATI/AMD area is that after AMD bought ATI they started releasing specs and actively help support writing the new open source drivers.

And that's why I opted for an ATI card after years of playing games via wine on a NVidia card. In the past and present NVidia was the only good choice for gaming on Linux. But this is changing fast and I believe by next year we'll have excellent 3D accelerated open source ATI drivers.

And NVidia - for all their fast hardware and well supported proprietary drivers - has serious heat issues.

---

### Post by Primefalcon on 2010-08-01
I have an x1300xt pro, not a new card but it runs great for me

---

### Post by forrestcupp on 2010-08-01
It's probably more fair to say that ATI doesn't have very good Linux support.

---

### Post by NightwishFan on 2010-08-01
The Intel Drivers run great for me, except for the performance lags behind Windows on some chips. However they are open source, support the kernel GEM code and Kernel Mode Setting. Some benchmarks report Linux having a huge advantage on newer Intel hardware.

Nvidia has the open source Nouveau driver, which is still working on 3D support. (Seems promising). It also has a well supported and high performing proprietary driver made by Nvidia themselves.

I have never used ATI, but I hear mixed result. It also has both an open and proprietary driver, but the open driver has 3d support.

Overall it is pretty good except some old archaic hardware I suppose. Generally 2d will always run pretty well. I barely use 3d, I am glad I have accelerated video though.

---

### Post by clhsharky on 2010-08-01
> Re: I understood that linux don't have good ati gpu support is it true?
No I don't find that to be true. 
Is windows support better yes.

> It's probably more fair to say that ATI doesn't have very good Linux support
I would say thats subjective. 

FGLRX and Radeon have improved tremendously this last year.
FGLRX may be behind the NV blob but both need stability.
Open Source Stack Radeon driver is ahead of other OSS driver available.

The latest and greatest Operating System on older hardware may not make a better computer.
Software moves on hardware doesn't.
 Quality hardware can give stable system and extend product life.
EOL(end of life) is inevitably, software and hardware. It seldom happens at same time.
After about 5 years personal computers have left there prime time. Hard ware may continue if quality was there. Drivers are mature and development will cease, hopefully maintainers will have enough interest for a few more years.

Get over it, enjoy.
Every thing comes to a end, everything.

Sharky

---

### Post by KdotJ on 2010-08-01
I'm using the open drivers for ATi on a ATi Radeon HD3200, they work great for me

---

### Post by forrestcupp on 2010-08-01
> **clhsharky said:**
> 
I would say thats subjective. 

FGLRX and Radeon have improved tremendously this last year.
FGLRX may be behind the NV blob but both need stability.
Open Source Stack Radeon driver is ahead of other OSS driver available.

I know what you're saying, but my point was that it's more ATI/AMD's fault than Linux's fault as is implied by the thread title.

---

### Post by 3rdalbum on 2010-08-02
Linux's support for GPUs is fine.

ATI's support for Linux leaves a lot to be desired.

Get rid of your ATI card and buy an Nvidia. You'll be happier.

---

### Post by aviramof on 2010-08-02
The fact is that with my Ati card i would better view movies in my windows 7 because in Ubuntu the picture jumps at times and also i have problems with activating dual view where as in windows 7/windows server 2008 i don't have this problem. 

Now perhaps the problem is caused because maverick is still in testing or because there is yet an official fglrx driver that support x.org 1.8 but still something need to be done about this problems.

---

### Post by Zorgoth on 2010-08-02
The drivers are getting better with newer cards, although for the very newest cards you still have to get the drivers from ATI's website rather than the "Hardware Drivers" tool, which means you have to reinstall them with each kernel upgrade.  I am using an ATI Mobility Radeon 5470 and while it is not quite as well supported as nVidia, it is very usable.  I have everything working except a couple features in wine games and (completely unimportantly since I don't care) the water effect in compiz.

---

### Post by clhsharky on 2010-08-02
I have never found a perfect computer, a perfect operating system, or a perfect app. So choice is perfect for me, of course your mileage may vary.

We all know comparing operating systems, is like comparing
apple to oranges

But users refuse to believe and resist(they want it there way).

Snow Leopard - Win7 - Lucid
I like to look at it this way

apple - oranges - bananas
Each fruit has different nourishment(need), and/or pleasure(taste ect.) 

Synopsis 

Now if jack likes oranges, and wants a banana to taste like a orange, Is it a banana?. Now Jack should just eat a orange and be happy, but will miss the vitamins & minerals of the banana.

Of course there are many scenarios for comparison, but you get the ideal.

Moral - You cant have it all, all of the time.

I for one am thankful that all the tools are available to get the job done.

Sharky

> Get rid of your ATI card and buy an Nvidia.
I also have 3 Nvidia cards, they didn't make me happier or sad.

I have more ATI cards than Nvidia, and use both all the time.
The main reason I have more ATI is I've had 2 Nvidias die and replaced them with ATI.

---

### Post by SunnyRabbiera on 2010-08-02
I think the future is good with ATI, sure right now the drivers are shaky but I think with the open drivers becoming very solid and the proprietary drivers slowly making progress there may be a day where ATI will rival NVIDIA in linux support.

---

### Post by lancest on 2010-08-02
Just got a MSI U230 (Radeon HD 3200 discrete Graphics), and the open source drivers for ATI are really great. I was surprised. 

Compiz works fine and the splash screen and tty's have perfect resolution- unlike with the proprietary ATI.

BTW No heat issues like on my notebook with Nvidia. 

Really happy that the FOSS drivers are coming on strong.

---

### Post by Spr0k3t on 2010-08-03
In the current state, ATI is going to only get better.  AMD knew the drivers for the ATI cards (on all platforms) was horrid at best even though the hardware was top notch.  Many things are starting to become of age with the open drivers.  I still use nvidia primarily for most systems.  If it's a laptop, I lean towards intel.

---

### Post by aviramof on 2010-08-03
What i am currently using is the fglrx driver from the x-swat ppa now compiz is working fine but as i said movies have jumps in them and i have problems with setting dual view.

if i were not to use fglrx but xorg/xserver or what ever i would not be able to reach high hd 
resolutions or all the available resolutions in display manager and i would not have catalyst
and maybe compiz would work less good so this is my big problem i guess that fglrx can be less good sometimes then the open drivers.

---

