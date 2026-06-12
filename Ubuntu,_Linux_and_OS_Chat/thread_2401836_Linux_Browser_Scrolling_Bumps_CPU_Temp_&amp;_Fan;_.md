---
title: "Linux Browser Scrolling Bumps CPU Temp &amp; Fan; Windows Does Not. Why?"
date: 2018-09-23
forum: Ubuntu, Linux and OS Chat
---

### Post by lostmoonofsaturn on 2018-09-23
Scrolling in a Linux browser bumps CPU temperatures by several degrees and audibly spins up the CPU fans. It's annoying.

I see this consistently on several Linux browsers, on a range of distributions.

It does not happen in Windows 10 using the same browsers on the same hardware.

Toggling each Linux browser's hardware acceleration option makes no difference.

So...  Is this down to something like less effective power utilization in Linux, driver issues, etc? Are there browser configuration settings that can affect this behavior?

---

### Post by ajgreeny on 2018-09-23
What hardware are you using?

Browsers can use quite a chunk of computer resources depending on how many tabs are open and what each tab is showing, for example flash adverts, which is about the only thing using flash, in these days of html5, can mean a lot of cpu resulting in heating and fans running hard.

Tell us more and we might have some better ideas.

---

### Post by lostmoonofsaturn on 2018-09-23
> **ajgreeny said:**
> What hardware are you using?



One system is an AMD Ryzen 2700x, 1080ti, 32-gig RAM, 27-inch 2560x1440 Asus Gsync display.

The other is an Intel i7-8680k, Vega 64, 32-gig RAM, 27-inch 2560x1440 Freesync display.

So, they are not hardware constrained.

Subjectively, Chrome seems marginally better than Firefox. 

I also notice slight differences between windows managers, i.e., Mutter vs Kwin vs Muffin vs xfwm4, etc. (Kwin on the Nvidia has other display aberrations that require fixes that Mutter/Muffin do not: setting refresh to 144 mHz and/or using the "Force Composition Pipeline" option, neither of which are needed elsewhere, even in xfwm4.)

---

### Post by ajgreeny on 2018-09-23
Wow! That's some hardware!

OK, as you say, you are not limited by low spec hardware, but I wonder if the opposite is the case, ie, your hardware is a bit too new and recent to be fully supported by the usual kernel, etc etc, of whichever Ubuntu version you're using.

Which version of Ubuntu is this, what graphics and driver, and which kernel is it using?

---

### Post by lostmoonofsaturn on 2018-09-24
It's 18.04.1 with a mainline 4.18.8 kernel and the 396.43 Nvidia driver. (I've set the BIOS in both machines to the default state, without manually playing with fan speeds, to keep a baseline.)

For the Vega 64 I stay with the open source driver, and use a 4.18 kernel because the stock 18.04.1 kernel doesn't contain the patch that correctly handles the fans on the Vega 64: They should stay idle below a GPU temp of 60C but they run continuously pre-4.18. This isn't Ubuntu-specific. (It's the CPU fan that spins up, not the GPU fans.  Those stay idle, both cards.

The behavior is the same under Nouveau and on the AMD card. 

I also use Fedora, have installed several other distros using different desktop environments/window managers (e.g., happens on Openbox with no compositor running) to check this, and it's the same behavior on all.

I also see this when I do something like an "apt update" or a "dnf --refresh update" on Fedora or anything else that creates/refreshes a cache. It does not happen if I disable a browser's Javascript, but, of course, the browser essentially becomes dysfunctional at that point.

So my guess is it's related to how the kernel manages memory and temperature control, and perhaps the Javascript implementations used in Linux browsers.

---

