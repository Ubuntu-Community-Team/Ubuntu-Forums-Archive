---
title: "NVIDIA Graphics Cards - dying out?"
date: 2010-07-27
forum: The Cafe
---

### Post by JustinR on 2010-07-27
Hey everybody,

I've been noticing through out these past few months that a lot of laptops (particularly Dell and HP) don't have nVidia graphics cards anymore just ATI - and if you really want an nVidia you have to get the highest of high-end laptops to find one (like Dell's Alienware m17X or HP's Pavillion dv8t series) I'm not sure about other major manufactures, but I see this as a pretty big down because nVidia offers great, although proprietary, linux drivers for there cards, while ATI is barely catching up.

Its pretty annoying actually, especially having to lookup an ATI card to see if it's compatible with Ubuntu.

Sooo, anybody know why nVidia cards seem to be disappearing?

---

### Post by betrunkenaffe on 2010-07-27
price.

---

### Post by JustinR on 2010-07-27
> **betrunkenaffe said:**
> price.

Can they really be that expensive?? I always though nVidia was the greatest but too expensive to be put back into mainstream computers (especially laptops)?

---

### Post by AllRadioisDead on 2010-07-27
Not sure, it's a shame.
After moving to Ubuntu, I sold my old HD4850 and upgraded to a GTS250.
I've never looked back, and I've never had a problem with it.

---

### Post by betrunkenaffe on 2010-07-27
If you are trying to provide a graphics card (other than intel) in a computer but keep the cost down for a midrange, 40+ bucks can be a big difference.

Nvidia will be back in the midrange laptops eventually.

---

### Post by 3rdalbum on 2010-07-27
Nvidia and ATI were pretty close in the last generation of graphics cards. For this current generation (ATI 5000 series and Nvidia 400 series), ATI's cards are faster, cheaper, more energy efficient and run cooler.

That doesn't mean that Nvidia is "dying out", only that they've got a lot of work ahead of them to produce some GPUs as good as ATI's in time for this current generation, or to try and catch up to next generation's products.

Unfortunately for Linux users it is extremely limiting - you can either have a graphics card that runs cool but has buggy drivers and extremely locked-up potential; or you can have a space heater installed in your PC.

---

### Post by aeiah on 2010-07-27
id just go with intel or the ION platform for now

---

### Post by Lucifer The Dark on 2010-07-27
Laptops are a developmental dead-end, nVidia are aiming for high end desktop machines instead, now that CUDA is being adopted by the 3D crowd you'll see ATI die off instead.

---

### Post by McRat on 2010-07-27
My laptop has nVidia 230m with CUDA, it was made in Feb.  HP dv8.  It's a POS though.  It benchmarks pretty high for a notebook, with 6.4 Win7 rating when it's not doing foul deeds or just shutting down.

Not sure if Windows is reporting it right, but it appears to use 3 GB of RAM off the motherboard.  That's a bit silly.  Not even workstation cards uses 4 GB (3+1)

I also built a cheap clone that had ATI integrated 4290 graphics in it, and WOW.  That rips too for a built in video.

---

### Post by Redache on 2010-07-27
> Laptops are a developmental dead-end, nVidia are aiming for high end desktop machines instead, now that CUDA is being adopted by the 3D crowd you'll see ATI die off instead.


Laptops are not a development dead-end, there's always room for more power efficient GPU's.  ATI also have OpenCL and Nvidia may end up licensing CUDA to other manufacturers(doubtful though it may be). Look at the GTX460, that proves that Nvidia still care about the mainstream since it's the place where every company makes the most money. They'd have to be stupid to focus on the high end.

I have an HD4870 and it works perfectly with the FOSS Radeon HD drivers so I wouldn't discount ATI just yet. I would rather have good Open Source Drivers over amazing Proprietary drivers any day.

The reason Nvidia aren't found in a lot of these laptops is partly due to the license for Nforce essentially being killed by Intel for the core i line and the aging/high cost of a lot of Nvidia's Discreet mobile GPU's. ATI are just cheaper and more power efficient in this space. Nvidia will catch up at some point, it's just the solution they have for power efficient graphics in the core i space is pretty expensive (google Nvidia Optimus if you want to know more).

---

### Post by cascade9 on 2010-07-27
> **3rdalbum said:**
> Nvidia and ATI were pretty close in the last generation of graphics cards. For this current generation (ATI 5000 series and Nvidia 400 series), ATI's cards are faster, cheaper, more energy efficient and run cooler.

That doesn't mean that Nvidia is "dying out", only that they've got a lot of work ahead of them to produce some GPUs as good as ATI's in time for this current generation, or to try and catch up to next generation's products.

+1. 

> **3rdalbum said:**
> Unfortunately for Linux users it is extremely limiting - you can either have a graphics card that runs cool but has buggy drivers and extremely locked-up potential; or you can have a space heater installed in your PC.

Or, you can just use a 'low end' nVida card (GT210, 220, 240). They are a bit more power hungy than the equivalent ATI cards, but its liveable. At least you get VDPAU, which works, not XvBA which is a 'work in progress' (and that is being nice). 

Just a pity that MXM (laptop/small form factor desktop) video expansion slots are still uncommon, as without that you have about 0 chance of changing the GPU in a laptop. 

> **Lucifer The Dark said:**
> Laptops are a developmental dead-end, nVidia are aiming for high end desktop machines instead, now that CUDA is being adopted by the 3D crowd you'll see ATI die off instead.

ATI is dead...:lolflag: That is so 1999, and about 6 times since then.

---

### Post by philinux on 2010-07-27
> **JustinR said:**
> Hey everybody,

I've been noticing through out these past few months that a lot of laptops (particularly Dell and HP) don't have nVidia graphics cards anymore just ATI - and if you really want an nVidia you have to get the highest of high-end laptops to find one (like Dell's Alienware m17X or HP's Pavillion dv8t series) I'm not sure about other major manufactures, but I see this as a pretty big down because nVidia offers great, although proprietary, linux drivers for there cards, while ATI is barely catching up.

Its pretty annoying actually, especially having to lookup an ATI card to see if it's compatible with Ubuntu.

Sooo, anybody know why nVidia cards seem to be disappearing?

Yes and they're usually integrated, especially laptops. Either ATI or INTEL.

---

### Post by LowSky on 2010-07-27
I'm suprised no has mention the real reason Nvidia isn't seen in any lowend computers. AMD makes ATI and Intel makes their own grahics chips too. Nvidia has been priced out of the lowend laptop and desktop market because cheaper onboard models currently exist. Its stimple supply and demand, how can you see a laptop for $40 more if it doesn't have any advantage (and your not Apple)?

---

### Post by endotherm on 2010-07-27
I just bought a netbook with an ion in it, because I didn't want to deal with a Intel GMA. 
I generally prefer nvidia to ati, but i will say, the ATI devs have really cleaned up the driver install and lucid finally has an restricted driver that actually works with my cards (HD3870/HD4000)

---

### Post by forrestcupp on 2010-07-27
> **LowSky said:**
> I'm suprised no has mention the real reason Nvidia isn't seen in any lowend computers. AMD makes ATI and Intel makes their own grahics chips too.That's exactly right.  You really started to see the change when AMD bought ATI.  Anything with an AMD CPU will have ATI, and anything with an Intel CPU will have an Intel GPU.

Of course you can still spend a few thousand dollars to get a gaming laptop with an nvidia chip.  But honestly, gaming is gravitating more toward the console, so why spend that much on a laptop?

> **cascade9 said:**
> 
Just a pity that MXM (laptop/small form factor desktop) video expansion slots are still uncommon, as without that you have about 0 chance of changing the GPU in a laptop.Exactly.  MXM should have been standard long ago.  How many people still use those PC card expansion slots?  MXM would actually be useful.

---

### Post by Grifulkin on 2010-07-27
> **ihermit said:**
> Not sure, it's a shame.
After moving to Ubuntu, I sold my old HD4850 and upgraded to a GTS250.
I've never looked back, and I've never had a problem with it.

That's not an upgrade, that's a downgrade.  Trust me I know I have a GTS250, I should have bought the ATI card, oh well I was dumb.

---

### Post by LowSky on 2010-07-27
> **forrestcupp said:**
> 
Of course you can still spend a few thousand dollars to get a gaming laptop with an nvidia chip.  But honestly, gaming is gravitating more toward the console, so why spend that much on a laptop?


Don't tell the fans of StarCraft 2!

I will say my ATI 4550 worked great in my Linux machine until I replaced it with an Nvidia GTX 460.

---

### Post by kaldor on 2010-07-27
I see loads of Nvidia machines still around. My HP and Mac included.

For the sake of Linux and FOSS, I hope Nvidia continues to be abundant or else we'll have to resort to making ATI work.

---

### Post by betrunkenaffe on 2010-07-27
The year Linux owns the desktop is the year desktop gaming dies.

---

### Post by endotherm on 2010-07-27
> **betrunkenaffe said:**
> The year Linux owns the desktop is the year desktop gaming dies.
I've actually been hearing the opposite for the last couple months. at the end of last year the bloggers were predicting the end of PC gaming, but indicators are pointing the other way now. saw somthing on /. just last week about how developers are railing against the limitations of the console.

---

### Post by forrestcupp on 2010-07-29
> **LowSky said:**
> Don't tell the fans of StarCraft 2!There will always be a market for certain types of PC games that are better to play on a PC than on a console.

> **betrunkenaffe said:**
> The year Linux owns the desktop is the year desktop gaming dies.I think it's probably the other way around.  The year Linux owns the desktop is the year desktop gaming is finally resurrected from the dead. ;)

---

### Post by 3rdalbum on 2010-07-29
> **cascade9 said:**
> Or, you can just use a 'low end' nVida card (GT210, 220, 240). They are a bit more power hungy than the equivalent ATI cards, but its liveable. At least you get VDPAU, which works, not XvBA which is a 'work in progress' (and that is being nice). 

True. My GTX260 doesn't heat up the room too much, even though it's a massive long graphics card with two freakin' PCI-E power points.

BTW in case anyone is having trouble finding the abovementioned cards: They're actually GT210, GTX220 and GTX240.

---

### Post by Lucradia on 2010-07-29
> **betrunkenaffe said:**
> price.

nvidia opted for power over price. ATI wanted price over power.

nvidia is fine as it is, and it's not going anywhere. Plus, Adobe partnered with nvidia to do flash acceleration with 10.1.

---

### Post by cascade9 on 2010-07-30
> **3rdalbum said:**
> BTW in case anyone is having trouble finding the abovementioned cards: They're actually GT210, GTX220 and GTX240.

Close, but slightly wrong....GTX is only used on the 260 and higher cards. 

The actual models are GT210, GT220, GT240. There is a GTS240, but its OEM only. 

[http://www.nvidia.com/object/geforce_family.html](http://www.nvidia.com/object/geforce_family.html)

---

### Post by papibe on 2010-07-30
I would say that Graphics Cards as we know them are indeed changing.

IMHO the ability to decode video and play HD content has become a required feature for a computer. Thus most new budget PCs and laptops have good to great video decode acceleration. Mostly they support DXVA2 on Vista and Win7.

I happen to had a brand new i3 powered laptop (~$600) for a couple of days, and it didn't even sweat to play full 1080p-h264 videos.

BTW, anybody knows how is the state of the linux intel driver?
Is there a Intel equivalent of vdpau? 

Regards.

---

