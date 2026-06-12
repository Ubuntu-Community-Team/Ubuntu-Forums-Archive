---
title: "Can I build a rig with an ARM processor?"
date: 2009-09-18
forum: The Cafe
---

### Post by blueturtl on 2009-09-18
I saw the [previous thread on the new Dual Core Cortex-A9]("http://ubuntuforums.org/showthread.php?t=1268586&highlight=cortex+a9") which supposedly outperforms the Intel Atom and it got me interested. I realized that since I'm a Linux user now nothing is really keeping me on x86 (which is rather dated anyway) so if I were to build a new computer, it could well be based on ARM.

Since Linux already supports ARM, all that I'd really need to do is come up with a motherboard compatible with this chip and then build around it.

Does anyone know if such things exist? I know the chip is intended for embedded devices and netbooks, but I'm not really a fan of that concept and would much prefer to build a rig on my own.

A quick Google didn't turn up anything in the way of components, just articles such as [this one]("http://www.tweaktown.com/news/13153/arm_shows_off_dual_core_cortex_a9_running_at_2ghz/index.html") that make it seem like there's something wrong with the chip since Windows can't run on it. :o (The chip is fine people, Microsoft needs to make Windows run on it, not the other way around!).

---

### Post by hessiess on 2009-09-18
Thears the Beagleboard but that's ARM A8 based.

---

### Post by blueturtl on 2009-09-18
Just wow. Running a fully fledged computer on a couple of watts.

Even the [A8-based Beagleboard]("http://en.wikipedia.org/wiki/Beagle_Board") can apparently decode 720P video. The dual-core A9 would surely be sufficient for any desktop application.

My current PentiumIII rig has trouble with HD-video and just the CPU is specced for ~30W!

---

### Post by hessiess on 2009-09-18
> **blueturtl said:**
> Just wow. Running a fully fledged computer on a couple of watts.

Even the [A8-based Beagleboard]("http://en.wikipedia.org/wiki/Beagle_Board") can apparently decode 720P video. The dual-core A9 would surely be sufficient for any desktop application.

My current PentiumIII rig has trouble with HD-video and just the CPU is specced for ~30W!

The A8 has a DSP, basically a hardware audio/video decoder chip which does most of the work.

---

### Post by 3rdalbum on 2009-09-18
> **blueturtl said:**
> I realized that since I'm a Linux user now nothing is really keeping me on x86

Flash Player?

Skype?

Google Earth?

Wine?

Mainstream Linux distributions?

Good 3D graphics performance?

Excellent CPU performance?

Basically any proprietary Linux software?

If you can live without those, then and only then can you live with a non-x86 platform.

---

### Post by hessiess on 2009-09-18
> **3rdalbum said:**
> Flash Player?
Skype?

Google Earth?

Wine?

For the most part theare are open source native equivalents to most wine stuff and Skype/Google earth will come over as ARM gets more popular.  

> 
Mainstream Linux distributions?

Good 3D graphics performance?

Excellent CPU performance?


As the platform becomes more popular, more distros will start to support it. And theare is no reason why it wouldn't be possible to hook up a good 3D graphics card to an ARM chip, its just mainly focused on the low power hand held device market currently. That will change if the ARM netbooks take off.

X86 IS NOT an effecent architecture, a good RISC processor like ARM will always beat a CISC design in enegy efficiency for the same amount of performance, especially with an architecture as old and bloated as X86 is.

And absolute performance is basically irrelevant as modern computers are HUGLY overpowered for what they are used for and run idle almost all the time.

---

### Post by hobo14 on 2009-09-19
> **3rdalbum said:**
> 
...

Good 3D graphics performance?

...


??  Your good 3D graphics performance is because of your x86 architecture?
I don't think so.

---

### Post by 3rdalbum on 2009-09-19
> **hobo14 said:**
> ??  Your good 3D graphics performance is because of your x86 architecture?
I don't think so.

No, it's because of the drivers that ATI and Nvidia have compiled for x86.

I'm not saying that ARM doesn't have the capability to run desktop graphics cards, or that it's impossible to port Flash, Skype and Google Earth. I'm not even saying that it's impossible to build an ARM processor with very high overall performance. I'm just saying that it doesn't exist right here and now, and that maybe those applications and drivers might be keeping Blueturtl on x86 for a while yet.

Remember, some Linux users don't realise that other processor architectures can't run precompiled x86 binaries. Take a look in the Apple Users forum and see how many people advise PPC users to "sudo apt-get install flashplugin-nonfree".

---

### Post by blueturtl on 2009-09-19
> **3rdalbum said:**
> Flash Player?

Skype?

Google Earth?

Wine?

Mainstream Linux distributions?

Good 3D graphics performance?

Excellent CPU performance?

Basically any proprietary Linux software?

If you can live without those, then and only then can you live with a non-x86 platform.

Skype, Google Earth, Wine: don't use those.

Mainstream Linux distributions.. I looked at the Debian download page and there is an ARM build, so I'd be basically running all the same software as Ubuntu users.

Good 3D performance I've last had when I was using a 3Dfx. :D Not so much 
an issue for me on the desktop, since without games there's really not much need for it. If I could hook up some form of ATI with an open-source driver to the rig I'm sure I could even run Compiz if I wanted to.

Not sure what you mean by excellent CPU performance. I'm pretty sure the Intel Atom can trump my 1 GHz Pentium while running at a fraction of the power and if the ARM is faster than the Atom, then I'm sure my needs would be well met.

Don't run any propriatory Linux software.

> The A8 has a DSP, basically a hardware audio/video decoder chip which does most of the work.

Thank you for pointing that out. No I really don't need that much power, I'd be content if it plays regular AVI/DivX really. I don't even have a monitor capable of displaying HD content. :)

I thought the Beagleboard was an interesting concept, but truthfully I'd rather want to be able to use some of the components more commonly available to us PC users. Essentially a standard ATX or Micro-ATX motherboard, but just supporting the ARM chip. But I guess those aren't going to become reality, after all the desktop market is all about Windows.

---

### Post by hessiess on 2009-09-19
> **3rdalbum said:**
> No, it's because of the drivers that ATI and Nvidia have compiled for x86.

No, actually its because of the extra hardware processors which are spasifically designed for rendering polygons, the dirvers just create a softwere interface. Eaven if you could run the drivers on ARM it wouldn't help becouse there is no way of physically connecting the GPU to a ARM CPU currently, which may change if the ARM netbooks take off.

---

### Post by Paqman on 2009-09-19
> **3rdalbum said:**
> 
Mainstream Linux distributions?


Ubuntu is pretty mainstream.

---

### Post by Xbehave on 2009-09-19
> **hessiess said:**
> No, actually its because of the extra hardware processors which are spasifically designed for rendering polygons, the dirvers just create a softwere interface. Eaven if you could run the drivers on ARM it wouldn't help becouse there is no way of physically connecting the GPU to a ARM CPU currently, which may change if the ARM netbooks take off.

[http://www.eurekatech.com/products/arm/ep454.htm](http://www.eurekatech.com/products/arm/ep454.htm) ARM-PCI bridges

The problem with ARM is probably cost & power, it will cost you more to build an ARM system as few parts are produced for the market (most are sold in bulk to phone/netbook/etc companies) and your not going to get amazing performance (especially as without special chips you'll be won't be looking at mainstream cards), however if you don't need 3d gaming/compiz then its not an issue.

---

