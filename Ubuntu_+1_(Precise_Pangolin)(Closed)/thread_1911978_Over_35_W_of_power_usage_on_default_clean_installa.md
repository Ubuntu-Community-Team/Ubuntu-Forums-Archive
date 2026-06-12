---
title: "Over 35 W of power usage on default clean installation."
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by donniezazen on 2012-01-19
Thought to give Precise a try.

[SIZE="4"][COLOR="red"]No Modifications and Clean Installation.[/COLOR][/SIZE]
[IMG]http://i.imgur.com/Mym0ul.png[/IMG]


[SIZE="4"][COLOR="Red"]Thinkfan, TLP, Disabled Nvidia Card, and Power Regression Fix from Phoronix.[/COLOR][/SIZE]
[IMG]http://i.imgur.com/xm0n4l.png[/IMG]


Wish it could be brought down to 8-10 W.

---

### Post by MacUntu on 2012-01-19
You can try those: [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

On a T510 (Intel Graphics HD 2000, 2/5 brightness) I can easily get a 9-10 W rate - ALPM helping the most. Using Unity 2D instead of Unity also saves one Watt for me (using Xubuntu spares almost another one, so that I theoretically could idle at 7.5 W, but I don't like Xubuntu that much ;)).

---

### Post by effenberg0x0 on 2012-01-19
I'm not familiar or usually concerned with energy issues as I have dropped using a Laptop for a couple months (and sadly will be back to it by Monday...). To which extent is it relevant in power consumption the fact that the two comparisons are running very different processes? I guess a lot. Also, one of the machines might be running 15 instances of glxgears, the other is updating and running a crazy sql query, etc.

Unless we get to see some test suite that loads from USB (HDDs might be moving sectors and we wouldn't know it - s.m.a.r.t), and runs the exact same test-designed processes, and only them, in the exact same order, and  for the exact same time, in at least two machines with the exact same hardware, exact same BIOS settings, same brand/model, performance of cooler/fans/heatsink (considering cfm, tdp, thermal paste, etc), all machines placed in the same room with strictly controlled temperature, 50% patched/ 50% not-patched, and we repeat this test like 50 or the n number of times needed to achieve a statistical relevance and plot the results, I don't believe we can do any precise measurement and everything is a guess.

---

### Post by xyzzyman on 2012-01-19
The latest 3.2 kernels from Ubuntu already have the ASPM fix backported from 3.3, so why do you have the fix listed on the second image but not on the first? What kernels are you using? (If you use kernels from the mainline site they don't have the ubuntu patches such as the aspm backport)

---

### Post by donniezazen on 2012-01-20
> **MacUntu said:**
> You can try those: [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

On a T510 (Intel Graphics HD 2000, 2/5 brightness) I can easily get a 9-10 W rate - ALPM helping the most. Using Unity 2D instead of Unity also saves one Watt for me (using Xubuntu spares almost another one, so that I theoretically could idle at 7.5 W, but I don't like Xubuntu that much ;)).

Thanks for the link. Ubuntu is my favorite Linux distro. I am not able to use it due to excessive heating. Xubuntu is also not very light distro. I have been running Arch with XFCE4. I would love to eventually come back to Ubuntu.

> **effenberg0x0 said:**
> I'm not familiar or usually concerned with energy issues as I have dropped using a Laptop for a couple months (and sadly will be back to it by Monday...). To which extent is it relevant in power consumption the fact that the two comparisons are running very different processes? I guess a lot. Also, one of the machines might be running 15 instances of glxgears, the other is updating and running a crazy sql query, etc.

Unless we get to see some test suite that loads from USB (HDDs might be moving sectors and we wouldn't know it - s.m.a.r.t), and runs the exact same test-designed processes, and only them, in the exact same order, and  for the exact same time, in at least two machines with the exact same hardware, exact same BIOS settings, same brand/model, performance of cooler/fans/heatsink (considering cfm, tdp, thermal paste, etc), all machines placed in the same room with strictly controlled temperature, 50% patched/ 50% not-patched, and we repeat this test like 50 or the n number of times needed to achieve a statistical relevance and plot the results, I don't believe we can do any precise measurement and everything is a guess.

It is not a guess. Checkout phoronix for graphs and control experiment. Chromium and Synaptics were the only two programs that were running in foreground.

> **xyzzyman said:**
> The latest 3.2 kernels from Ubuntu already have the ASPM fix backported from 3.3, so why do you have the fix listed on the second image but not on the first? What kernels are you using? (If you use kernels from the mainline site they don't have the ubuntu patches such as the aspm backport)

Linux donnie-laptop 3.2.0-9-generic #16-Ubuntu SMP Fri Jan 13 20:46:38 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I don't know if it already has a fix but adding following line knocked off 10 C.

```
pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
```

---

### Post by xyzzyman on 2012-01-20
> **donniezazen said:**
> Linux donnie-laptop 3.2.0-9-generic #16-Ubuntu SMP Fri Jan 13 20:46:38 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I don't know if it already has a fix but adding following line knocked off 10 C.

```
pcie_aspm=force i915.i915_enable_rc6=1 i915.i915_enable_fbc=1 i915.lvds_downclock=1
```

Yeah, that kernel has the ASMP fix already back ported into it. So pcie_aspm=force most likely isn't making any difference for you. The other options are just sandy-bridge fixes separate from the ASPM issue. If you had an i3/i5 I'd see it down to 8-10 but I don't think you're going to get that at this point on an i7.

What worries me is that you were running at 85degrees in that first pic. I have a core2 that idles at 38, and I can peak at 76 while compiling or encoding (I have been able to hit 80 with it on my laptop). I'm pretty sure the i7 should be similar.

EDIT: I see you already are looking at the temps. My bad. I'm tired and was just reading the voltage talk. My bad.

---

### Post by donniezazen on 2012-01-20
> **xyzzyman said:**
> Yeah, that kernel has the ASMP fix already back ported into it. So pcie_aspm=force most likely isn't making any difference for you. The other options are just sandy-bridge fixes separate from the ASPM issue. If you had an i3/i5 I'd see it down to 8-10 but I don't think you're going to get that at this point on an i7.

Well I can clear the whole kernel line and see if it goes up back to 80s.

---

### Post by xyzzyman on 2012-01-20
> **donniezazen said:**
> Well I can clear the whole kernel line and see if it goes up back to 80s.

Actually removing pcie_aspm=force would be helpful, as that's supposed to not be necessary anymore. If you're getting a 30-40 degree difference without it then a bug report needs to be filed. The i915 sandy bridge lines I think are still needed but I haven't followed those as much.

---

### Post by donniezazen on 2012-01-20
> **xyzzyman said:**
> Actually removing pcie_aspm=force would be helpful, as that's supposed to not be necessary anymore. If you're getting a 30-40 degree difference without it then a bug report needs to be filed. The i915 sandy bridge lines I think are still needed but I haven't followed those as much.

You are right removing pcie_aspm=force is not needed. Thanks.

The temp and power still hangs around 50-60 C and 10-20 W respectively.

I will check out the link posted above may be it will help me shove off some watts.

---

### Post by donniezazen on 2012-01-20
[COLOR="SeaGreen"]Why is screen consuming almost 10 Watts and PCI devices are at 100%? It seems to me powertop has some minor issues.[/COLOR]


[IMG]http://i.imgur.com/gSWWwl.png[/IMG]

---

### Post by xyzzyman on 2012-01-20
PCI devices showing 100% in powertop is a known issue I believe with no fix. Mine is the same way. If it's not a bug, all I can figure is it's 100% on or 0% when off... I could probably test that by disabling wireless I guess. The hd audio is a pain as even though in the kernel you can set a timeout to power off the audio card, from what i've gathered only one chipset actually supports it (intel hd audio is just the spec, and there's chips made by realtek and many others)

Mine doesn't show the watts used by the backlight, but only the percentage between 0% and 100% depending on the brightness of my display... Turning it to lowest brightnest via fn key shows it at 0% even though it's still clearly on.

---

