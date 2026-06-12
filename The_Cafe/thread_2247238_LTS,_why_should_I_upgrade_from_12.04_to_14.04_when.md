---
title: "LTS, why should I upgrade from 12.04 to 14.04 when 12.04 support is to 2017"
date: 2014-10-06
forum: The Cafe
---

### Post by Handssolow on 2014-10-06
The only reasons I've found to change are hardware driver support from jockey-gtk to a tab in synaptic and possibly a more modern version of Wine with 14.04. Currently my Toshiba Laptop with pentium M isn't showing 14.04 as an upgrade option. Quite what I'd do differently on any of my PCs with 14.04 that I can't do with 12.04 is unclear. That said, I'd want nothing to do with Unity on any of my PCs or having Amazon given priority on my Firefox searches etc.

---

### Post by JKyleOKC on 2014-10-06
The primary reason, for me anyway, to make the change is the fact that 12.04 is only six months away from EOL -- and when that time gets here, it won't get any more security updates.

I'm in the process of making that change now; I waited for 14.04.1 to have the best chance of most bad bugs having been fixed. I'm finding very little different so far as functionality, but I'm running Xubuntu with the XFCE window manager rather than full Gnome. It's not afflicted with excessive eye candy and is quite easy to configure. I do find that a few annoying quirks that persisted throughout the life of 12.04 have been cured, and haven't yet found anything creeping in to take their places annoying me.

So although I'm a firm believer that "if it ain't broke, don't fix it," the fact that EOL is rapidly approaching makes 12.04 broke, in my book...

---

### Post by Dennis N on 2014-10-06
> The primary reason, for me anyway, to make the change is the fact that 12.04 is only six months away from EOL -- and when that time gets here, it won't get any more security updates.

This page seems to say 12.04 LTS is supported into 2017.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Is it incorrect?

---

### Post by deadflowr on 2014-10-06
Xubuntu has a 3 year LTS
Normal Ubuntu is supported until 2017.

Kubuntu and Ubuntu have 5 year LTS for precise.
Xubuntu has 3 year LTS for precise
Lubuntu did not have one for precise.
Don't know about Ubuntu Studio or mythbuntu...
(But mythbuntu has it's own repo, so...)
And Ubuntu Gnome did not exist for precise.

And so, yes, there is no reason to upgrade to Regular Ubuntu 14.04, if nothing is wrong.
For now.

---

### Post by sammiev on 2014-10-06
> **Handssolow said:**
> The only reasons I've found to change are hardware driver support from jockey-gtk to a tab in synaptic and possibly a more modern version of Wine with 14.04. Currently my Toshiba Laptop with pentium M isn't showing 14.04 as an upgrade option. Quite what I'd do differently on any of my PCs with 14.04 that I can't do with 12.04 is unclear. That said, I'd want nothing to do with Unity on any of my PCs or having Amazon given priority on my Firefox searches etc.

If it's not broken and you are using the flavour that's still ongoing and are happy, then leave enough alone. If you need the latest and greatest, move up if your equipment supports it. ):P

---

### Post by grahammechanical on 2014-10-06
> [COLOR=#000000]Quite what I'd do differently on any of my PCs with 14.04 that I can't do with 12.04 is unclear. [/COLOR]

We could say that about upgrading to a newer version of any OS.

Linux has to keep up with newer hardware and Ubuntu has to keep up with Linux so as to be compliant with newer hardware. Ubuntu 12.04 has had its final hardware enablement stack upgrade. If you are on 12.04.0 or 12.04.1 or 12.04.5 then you will get kernel support up to April 2017. But the point releases of 12.04.2; 12.04.3 and 12.04.4 are no longer getting kernel support.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

As long as your present hardware keeps going you have no reason to upgrade to 14.04. But this time next year if you buy new hardware you may find that 12.04 will no longer be compliant with that newer hardware. It will not have the improvements that have been made to the Linux kernel in the meantime. And it will be a flavour of 14.04 that you will need.

Regards.

---

### Post by QIII on 2014-10-06
Amazon?

Old issue.  Dead horse.

---

### Post by robin7 on 2014-10-07
12.04 is not "broken." It's not even slightly damaged. Not even smudged, not a speck of dust. It's perfectly fine for the hardware it runs on.  When I upgraded to 14.04 I found that the new and "improved" version of Xubuntu was a lot slower, and it ran in fits and starts, at times just stalling and requiring several minutes to get it's bearings even after closing any unresponsive applications. Admittedly my computer is ancient - one step up from an abacus, probably, and it's amazing that it can run [Xubuntu]("http://xubuntu.org") Precise so well, and [LXLE]("http://lxle.net") even faster.  [What I learned]("http://wp.me/p51xQV-96") from my brief time on 14.04 was that I probably have about 3 years of useful life left to my old relic dinosaur (even with added RAM - I'm up to 1 GB now), and it has been a great run.

---

### Post by matt_symes on 2014-10-07
> **robin7 said:**
> [What I learned]("http://wp.me/p51xQV-96") from my brief time on 14.04 was that I probably have about 3 years of useful life left to my old relic dinosaur (even with added RAM - I'm up to 1 GB now), and it has been a great run.

I bet if you put something other than a flavour of Ubuntu on it you would get loads more usage.

Tiny core, Bodhi, Puppy and Slitaz (amongst many others) are all light and if your hardware is ancient, there is dsl. 

I have an old Dell Lattitude C510 with 256M RAM in my possession that was going to the dump and i can get a usable desktop on it.

---

### Post by Al1000 on 2014-10-07
I installed Kubuntu 12.04 on my old laptop, and through accepting all update packages (except the one that upgrades it to 14.04), it has updated the version number itself. The last time I checked it was at version 12.04.4, and I've just checked again and

```
lsb_release -a
```

...informs me it is now at 12.04.5

---

### Post by Al1000 on 2014-10-07
> **matt_symes said:**
> I bet if you put something other than a flavour of Ubuntu on it you would get loads more usage.

Tiny core, Bodhi, Puppy and Slitaz (amongst many others) are all light and if your hardware is ancient, there is dsl. 

I have an old Dell Lattitude C510 with 256M RAM in my possession that was going to the dump and i can get a usable desktop on it.

Puppy is excellent, but I find that it lacks many features that the 'full' Linux distros have.

I dual boot with Lucid Puppy 5.2.8.6 on my laptop. As by itself, it uses less than 80MB of RAM compared with the 290MB or so that Kubuntu 12.04 uses, Puppy is much better for resource intensive applications such as playing videos and downloading large files.

---

### Post by buzzingrobot on 2014-10-07
> **Handssolow said:**
> ... having Amazon given priority on my Firefox searches etc.

Hmmm?  Sure about that?

---

### Post by buzzingrobot on 2014-10-07
Driver availability and improvement are probably the most obvious benefits. Other kernel changes may be useful and may not have been backported to the 12.04 kernel.

Upstream has implemented improvements to freetype that I, at least, think are visible on screen in 14.04 versus 12.04. That alone would be reason enough for me to upgrade.

Unity seems to me smoother, faster and more polished in 14.04.

Access to more current package versions in 14.04 that could require PPA use in 12.04.

To each his or her own, as always.  If I didn't want the benefits of the freetype changes and the improved font rendering, and was running something like XFCE that has shown little if any development since 12.04's release, I'd likely stay with 12.04.

---

### Post by Al1000 on 2014-10-07
The only reason I stay with 12.04 on my laptop is because it's old. I use Kubuntu 14.04 on my desktop pc, but my laptop wouldn't even boot the 14.04 DVD. It doesn't even boot with Ubuntu 12.04, but for some reason (to do with the graphics) it runs Kubuntu 12.04 just fine, albeit a little slowly and without the '3D' desktop features.

---

### Post by robin7 on 2014-10-07
> **matt_symes said:**
> I bet if you put something other than a flavour of Ubuntu on it you would get loads more usage.

Tiny core, Bodhi, Puppy and Slitaz (amongst many others) are all light and if your hardware is ancient, there is dsl. 

I have an old Dell Lattitude C510 with 256M RAM in my possession that was going to the dump and i can get a usable desktop on it.

I have experimented with several excellent lightweight distros, from straight "bare-bones" Debian with Openbox, to AntiX, SalixOS (Slackware-based, very minimal Xfce desktop), Bodhi, a couple of PCLinuxOS mixtures (E17 and Xfce), MX-14, and now LXLE (12.04), which *on my computer* works the best of any and all of those listed.

**My experience absolutely runs in direct conflict with "conventional wisdom," **which even many of the most ardent Ubuntu fanboys have repeated in these and other forums: That "plain Debian" plus straight vanilla Xfce is a thousand times lighter and faster than even minimal Ubuntu + Xfce (much less Xubuntu!), and needs less RAM, less CPU power, etc.  I always assumed that was probably generally true, but when I tried several minimal non-Ubuntu systems, both Debian-based and otherwise on my own very modest hardware, they were *much* less nimble and speedy than any of the Ubuntu variants I tested except for 14.04.

I honestly would love to know why my experience - over three years now - has been [so completely opposite]("http://wp.me/p51xQV-9a") from the conventional wisdom that even Ubuntu experts regularly agree with.

---

### Post by buzzingrobot on 2014-10-07
> **robin7 said:**
> I have experimented with several excellent lightweight distros, from straight "bare-bones" Debian with Openbox, to AntiX, SalixOS (Slackware-based, very minimal Xfce desktop), Bodhi, a couple of PCLinuxOS mixtures (E17 and Xfce), MX-14, and now LXLE (12.04), which *on my computer* works the best of any and all of those listed.

**My experience absolutely runs in direct conflict with "conventional wisdom," **which even many of the most ardent Ubuntu fanboys have repeated in these and other forums: That "plain Debian" plus straight vanilla Xfce is a thousand times lighter and faster than even minimal Ubuntu + Xfce (much less Xubuntu!), and needs less RAM, less CPU power, etc.  I always assumed that was probably generally true, but when I tried several minimal non-Ubuntu systems, both Debian-based and otherwise on my own very modest hardware, they were *much* less nimble and speedy than any of the Ubuntu variants I tested except for 14.04.

I honestly would love to know why my experience - over three years now - has been [so completely opposite]("http://wp.me/p51xQV-9a") from the conventional wisdom that even Ubuntu experts regularly agree with.

No accepted definition for "lightness" exists, as far as I know. Impressions are subjective, based on an individual's particular configuration and the hardware it runs. Even when measurements of multiple environments are made on one machine, they can't predict performance on other machines with different hardware. (Identical kernels also need to be used for comparisons because different kernels have different bugs and different levels of support for different pieces of hardware.)

When a GUI is used, user impressions of speed are typically biased by how quickly that interface responds to mouse clicks and other actions, how fast the screen repaints, etc. That behavior may or may not reflect anything "real" going on elsewhere. (A lot of old machines have old and less capable video cards for which only old and less capable drivers are available. Put those cards and those drivers in an expensive tricked out modern rig and they would still be a drag on performance.)

---

### Post by matt_symes on 2014-10-07
> **robin7 said:**
> I honestly would love to know why my experience - over three years now - has been [so completely opposite]("http://wp.me/p51xQV-9a") from the conventional wisdom that even Ubuntu experts regularly agree with.

What is your hardware ? I suspect it's more usable than you think. If you run a lighter desktop and a standard desktop on average hardware you may not notice much difference.

However, there does comes a time for older hardware when the bigger  heavier distributions just don't cut it on older the hardware. This is  not just subjective as you can actually see response times slow down and  the machines become more sluggish when comparing different  distributions running on them due to things like slow CPU and memory  pressure forcing swapping out.

Many of the lighter desktops use lighter applications; lighter in both CPU usage and memory footprint. This does make a difference.

> **buzzingrobot said:**
> No accepted definition for "lightness" exists, as far as I know. Impressions are subjective, based on an individual's particular configuration and the hardware it runs.

I absolutely agree that there is no definition of "lightness" when it comes to installations. 

Besides anything else, peoples usage patterns differ drastically. 

I know people who will only have one or two applications running at any one time, one of then being a browser with only a couple of tabs open. 

My usage patterns are the opposite and the only way i can achieve that on this laptop, given its hardware constraints, is by running half of my programs as CLI applications.

The only usable yard stick we have are actual metrics.

---

### Post by MoebusNet on 2014-10-11
> **Handssolow said:**
> The only reasons I've found to change are hardware driver support from jockey-gtk to a tab in synaptic and possibly a more modern version of Wine with 14.04. Currently my Toshiba Laptop with pentium M isn't showing 14.04 as an upgrade option. Quite what I'd do differently on any of my PCs with 14.04 that I can't do with 12.04 is unclear. That said, I'd want nothing to do with Unity on any of my PCs or having Amazon given priority on my Firefox searches etc.

Please allow me to share my experience with 14.04 on my old Pentium-M notebook (2003 Dell Latitude D800 1.4Ghz, 2Gb RAM, NVidia GTX5200-M 64 Mb). I'm using Lubuntu 14.04.1 and other than being a bit slow to load is quite usable. The installation for 14.04 on a Pentium-M requires the *forcepae* boot option [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) but the installation for me was quite straightforward. The only issue you may have besides sufficient RAM may be your video card; I upgraded from an NVidia 4200 series to a 5200 series ($30 ebay) because NVidia dropped support for the older AGP bus card after 12.04.

That said, Ubuntu after 12.04 has some unresolved issues with Bluetooth if that is a consideration. 12.04 allows me to transfer photos phone>PC via Bluetooth; 13.04 and newer does not. Bluetooth audio streaming is also problematic. These issues have not been resolved for 14.10 beta at this time.

EDIT: Ubuntu 14.10 beta seems to have sorted out the Bluetooth audio streaming issues as of 11 October. File transfers are still broken via Bluetooth.

---

