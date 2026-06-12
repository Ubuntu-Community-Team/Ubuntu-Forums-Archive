---
title: "New to the idea of converting tablets to Ubuntu/Linux. Some info please"
date: 2017-02-09
forum: Ubuntu Phone and Tablet
---

### Post by juntjoo2 on 2017-02-09
I've been using my old Acer netbook for general office use, MS office via WINE, printing/scanning etc but it died on me so shopping around old computers on eBay to my delight I've discovered the possibility of installing Linux on mobile devices which greatly opens up possibilities for my general desktop setup. Apparently now the line between desktop and mobile hardware has become fuzzy and we can greatly customize our setups which is awesome. So I think I'm going to forego fixing my old laptop and go with a 'modular' setup with a nice light touch screen tablet and whatever peripherals I need, ie keyboard, speakers, mouse, etc. I just need to know the rules. Can any ol' tablet be converted or are there hardware driver conflicts to be wary of or can I pretty much grab any of the many tablets off my local Walmart shelf and put Ubuntu(or whatever Linux would be best suited) on it? Thanks!

---

### Post by dtarrant on 2017-02-09
Interesting question. I have experience of using ubuntu on desktops, laptops, netbooks and most recently, on a tablet. The important thing to understand is that desktop applications don't play nicely with touchscreens. The app control widgets are generally too tiny to enable accurate manipulation with your finger. You need apps that are optimised for touchscreen use. If you can install ubuntu desktop on a tablet, you could attach a mouse and keyboard and that should give you the control you need.

i have a BQ Aquaris M10 tablet running ubuntu touch. This has a suite of touch optimised apps which you can drive with your finger. It also has a suite of ubuntu desktop apps which you can drive with a bluetooth touchpad keyboard. I think it's pretty cool. Ubuntu pitches it as "convergence".

Ubuntu Touch runs on a limited number of smartphones. I've read that some folk have tried installing it on Nexus 7 hardware, but I'm not sure if that approach is supported with OTA updates.

Hope this is a useful introduction. Try to find a BQ Aquaris M10 Ubuntu Edition on ebay. Some people will have decided that it's too quirky and decided to move it on. In my opinion the recent OTA-15 is a big improvement. I'm writing this with my finger on my ubuntu touch tablet.

Good luck and let us know how you get on.

---

### Post by dtarrant on 2017-02-09
Information regarding supported hardware can be found here:

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

---

### Post by juntjoo2 on 2017-02-10
Thank you. After further research I've learned that you're taking about this "ARM" version of Linux which is limited to certain apps while I'm trying to find a full Linux solution which so far appears only possible with the"X86" desktop architecture so I'd be limited to those types of tablets which so far I haven't found any that have o capabilities. Yes I want it all lol. But I was hoping to take one of the GSM tablets to use as a phone AND my main computer. Still looking into it...

---

### Post by krusty8 on 2017-02-11
I think the ubuntu repositories are mostly available for arm architecture as well. So that is not the biggest problem.

The challenge that you will experience is that Ubuntu Touch runs with Mir as a display server, while 99% of the "normal" linux applications require X. It is possible to run X applications on Mir with Libertine / XMir, but it has some limits. If you look for videos and do some general internet research for Aquaris M10, Ubuntu Touch, Libertine, you'll see. 

In addition, as dtarrant pointed out, keep in mind that most X applications aren't really optimised for touch.

Lastly, Canonical is right now embarking on a bigger architectural change from how they previously built the system for their ubuntu touch devices (vivid&click) and how they plan to do it in the future (xenial&snap). It's not clear which devices will get such a system in the future. M10 might be lucky, but it's not sure.

---

