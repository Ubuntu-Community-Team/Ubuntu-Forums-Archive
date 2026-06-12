---
title: "Wayland, X, efficiency and system requirements"
date: 2011-05-14
forum: The Cafe
---

### Post by Oxwivi on 2011-05-14
As discussed in [this section of the Wikipedia article on X Window System]("http://en.wikipedia.org/wiki/X_Window_System#Client.E2.80.93server_separation"), the seperation of client and server incurs an overhead. Will the usage of Wayland protocol eliminate, or at least reduce, this overhead? Can this reduce load on the system and possibly make applications running with Wayland protocol less hardware-intensive than X?

---

### Post by 3Miro on 2011-05-14
I would think that the Xorg latency is hardly measurable on a modern computer.

When Wayland first comes out, everybody would be running Xorg on top of Wayland for compatibility reasons. Eventually we may see purely Wayland applications, however, by that time Wayland itself will morph onto who knows what.

Speed is very much dependent on the implementation and there will be different implementations of the Wayland protocol.

---

### Post by Oxwivi on 2011-05-14
I'm more interested in teh system load issue than speed. Would hate not being able to use newer Ubuntu...

---

### Post by Oxwivi on 2011-05-14
I know that initially X would run on top of Wayland, but what comes after when mostly everything runs using Wayland natively? I am hopeful that with eliminating the middleman X processes, there will be less load on the system, thus equating into better performance and less system requirement.

---

### Post by Lucradia on 2011-05-14
> **Oxwivi said:**
> I know that initially X would run on top of Wayland, but what comes after when mostly everything runs using Wayland natively? I am hopeful that with eliminating the middleman X processes, there will be less load on the system, thus equating into better performance and less system requirement.

That will take more than two years to port everything to Wayland. Wine being one of the ones that would take the longest, but probably would benefit the most. OpenGL is another thing that will take a while.

---

### Post by nerdopolis on 2011-05-14
AFAIK there is a driver in wine called X11.drv that they use for putting Wine on X11, which can be replaced. 

(they tried to make a quartz.drv for MacOS X's default graphics system instead of using Xquartz... but does not seem developed since 2008. It even seems possible to switch the between quartz.drv and x11.drv by changing a Wine registry setting, instead of a total recompile...)

So it seems that Wine should not have to change or rewrite *TOO* much, AFAIK they just need to write a Wayland.drv, depending on how complex the driver is...

---

### Post by phrostbyte on 2011-05-14
There is GTK+ and Qt ports to Wayland, so it will be possible to use Wayland instead of X.org quite rapidly. But, Wayland is far from usable or complete.

---

### Post by toupeiro on 2011-05-14
There's also the giant pink elephant in the room named "videocard/driver support."

---

### Post by jerenept on 2011-05-14
> **toupeiro said:**
> There's also the giant pink elephant in the room named "videocard/driver support."

coughnvidiacoughcough

---

### Post by Oxwivi on 2011-05-14
Eh, I don't game much (19 this May 27th, but still using Pentium 4), I'm happy with Intel.

---

### Post by toupeiro on 2011-05-14
> **jerenept said:**
> coughnvidiacoughcough

lol, nvidia has bigger fish to fry.  even the wayland devs know this which is why they ONLY support the open source driver.  Your mileage is going to vary TREMENDOUSLY..


<-- Running NVidia, playing with wayland, having all sorts of compatibility issues...

cut and pasted directly from the wayland build docs:

"nVidia: Requires Nouveau (open source driver). DRM output requires a kernel built from the Nouveau git repository, details below. Cards probably work back to Riva TNT (1998). The latest series of chips, NVC0 / Fermi, released March 2010, requires loading external firmware for Nouveau, which is not documented."

---

### Post by screaminj3sus on 2011-05-14
> **toupeiro said:**
> There's also the giant pink elephant in the room named "videocard/driver support."
Yeah I have a feeling the x compatability layer on top of wayland will be around for quote a long time lol.

Hopefully the open source drivers (Nouveau, Radeon, Intel) get ported to wayland relatively quickly. But the binary blobs will be trouble. Nvidia flat out said they won't support it, and who knows what amd will do. They have been supportive of open source lately, but even if they do decide to support wayland with catalyst we can be assured it will take forever lol.

---

### Post by toupeiro on 2011-05-14
> **screaminj3sus said:**
> Yeah I have a feeling the x compatability layer on top of wayland will be around for quote a long time lol.

Hopefully the open source drivers (Nouveau, Radeon, Intel) get ported to wayland relatively quickly. But the binary blobs will be trouble. Nvidia flat out said they won't support it, and who knows what amd will do. They have been supportive of open source lately, but even if they do decide to support wayland with catalyst we can be assured it will take forever lol.

Tell me about it..  I've asked colleages I have that work for NVidia about this very topic.  Support for this is generally quickly responded to when I've asked: no.  However, some people are still convinced that it will be distro ready in 5 years.  If you even try to mention that they (Mark and Canonical) have the blinders on, they (the acolytes of Mark and Canonical) throw more blog dribble cool-aid at you as if it was the definitive source of all that will happen.  It takes a lot more to sail a ship than a captain.

---

### Post by Hyporeal on 2011-05-14
> **toupeiro said:**
> There's also the giant pink elephant in the room named "videocard/driver support."

But pink elephants are imaginary. Likewise, the driver situation is largely an imagined problem. If Wayland does what it claims to then there will be drivers. It's way too early to panic.

> **screaminj3sus said:**
> Nvidia flat out said they won't support it

It's amazing how quickly things get exaggerated and distorted. Did they swear in blood never to support Wayland, to the end of time?

---

### Post by toupeiro on 2011-05-14
> **Hyporeal said:**
> But pink elephants are imaginary. Likewise, the driver situation is largely an imagined problem. If Wayland does what it claims to then there will be drivers. It's way too early to panic.



It's amazing how quickly things get exaggerated and distorted. Did they swear in blood never to support Wayland, to the end of time?

Its equally amazing how just as quickly a company will tell someone "no" and they'll assume it means 20 other things...

If you said the issue is an imagined issue, your head is thoroughly in the clouds ... or the sand, take your pick.  Wayland has to run on SOMETHING, and the most fundamental of these somethings is hardware, which requires proper drivers to fully leverage, which the open source drivers are nowhere close to being able to deliver.  If the hardware vendors are not getting behind it, maybe it's too early to panic, but it's definitely too early to even remotely start to consider a distribution timeline.  **_It.is.not.supported._**  Until its embraced by at LEAST the major GPU developers of the world, its smoke and glass.

---

### Post by screaminj3sus on 2011-05-14
> **Hyporeal said:**
> But pink elephants are imaginary. Likewise, the driver situation is largely an imagined problem. If Wayland does what it claims to then there will be drivers. It's way too early to panic.



It's amazing how quickly things get exaggerated and distorted. Did they swear in blood never to support Wayland, to the end of time?

No, but they did say "we won't support wayland" which is about as blunt as you can get.

---

### Post by Hyporeal on 2011-05-14
> **toupeiro said:**
> If you said the issue is an imagined issue, your head is thoroughly in the clouds ... or the sand, take your pick.  Wayland has to run on SOMETHING, and the most fundamental of these somethings is hardware, which requires proper drivers to fully leverage, which the open source drivers are nowhere close to being able to deliver.  If the hardware vendors are not getting behind it, maybe it's too early to panic, but it's definitely too early to even remotely start to consider a distribution timeline.  **_It.is.not.supported._**  Until its embraced by at LEAST the major GPU developers of the world, its smoke and glass.

I guess you'll consider it smoke and glass for a while longer then. I'll continue to have a less gloomy perspective.

> **screaminj3sus said:**
> No, but they did say "we won't support wayland" which is about as blunt as you can get.

This is getting ridiculous. Give me a citation for that alleged quotation. A quick search for it yields only your post.

---

### Post by screaminj3sus on 2011-05-14
Don't know what you were searching for but I googled and found this within seconds.

[http://www.phoronix.com/scan.php?page=news_item&px=ODc2Mg](http://www.phoronix.com/scan.php?page=news_item&px=ODc2Mg)
[http://www.omgubuntu.co.uk/2010/11/nvidia-have-no-plans-to-support-wayland/](http://www.omgubuntu.co.uk/2010/11/nvidia-have-no-plans-to-support-wayland/)
[http://www.nvnews.net/vbulletin/showpost.php?p=2343452&postcount=11](http://www.nvnews.net/vbulletin/showpost.php?p=2343452&postcount=11)

"NVIDIA's Aaron Plattner has publicly stated, "We have no plans to support Wayland."

---

### Post by Paqman on 2011-05-14
> **screaminj3sus said:**
> No, but they did say "we won't support wayland" which is about as blunt as you can get.

IIRC they said "we have no plans to support it", which is not the same thing. Wayland isn't far enough along for them to devote time and resources to it. If I was in they're position, I wouldn't support it yet either.

---

### Post by jerenept on 2011-05-14
> **Hyporeal said:**
> I guess you'll consider it smoke and glass for a while longer then. I'll continue to have a less gloomy perspective.



This is getting ridiculous. Give me a citation for that alleged quotation. A quick search for it yields only your post.

[Phoronix]("http://www.phoronix.com/scan.php?page=news_item&px=ODc2Mg")
[OMGUbuntu]("http://www.omgubuntu.co.uk/2010/11/nvidia-have-no-plans-to-support-wayland/")
[NVIDIA Forums]("http://www.nvnews.net/vbulletin/showthread.php?p=2343452#post2343452")

Where have you been searching?

EDIT:screaminjesus beat me.

---

### Post by Hyporeal on 2011-05-16
> **screaminj3sus said:**
> No, but they did say "we won't support wayland" which is about as blunt as you can get.

> **screaminj3sus said:**
> "NVIDIA's Aaron Plattner has publicly stated, "We have no plans to support Wayland."

It seems that you were lying about the "we won't support Wayland" bit. I really don't appreciate being lied to. It's a shame that you think you have to misquote other people in order to make your point.

---

### Post by PhillyPhil on 2011-05-16
> **toupeiro said:**
> Its equally amazing how just as quickly a company will tell someone "no" and they'll assume it means 20 other things...
They haven't actually said 'no', just 'currently no plans'... 
 >   If the hardware vendors are not getting behind it, maybe it's too early to panic, but it's definitely too early to even remotely start to consider a distribution timeline.  **_It.is.not.supported._**  Until its embraced by at LEAST the major GPU developers of the world, its smoke and glass. No, it's not supported now, but that's not really an issue seeing as Canonical isn't using it now... 

One thing is certain: X won't last forever.

---

### Post by aaaantoine on 2011-05-16
I think the proprietary driver developers will put in an effort to make their offerings work with the modern Linux graphics stack (and maybe even contribute useful code changes to parts of the open source stack) when they find that the platform they're currently developing for is no longer supported by major distros.

Nvidia says they won't support Wayland now.  But when **everything** in the stack -- top to bottom -- is working against them, they are going to have to think about what is more expensive: maintaining their version of the old stack until kingdom come, or building a driver to work with the new stack.

---

