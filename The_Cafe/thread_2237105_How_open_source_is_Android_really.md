---
title: "How open source is Android really?"
date: 2014-07-30
forum: The Cafe
---

### Post by mamamia88 on 2014-07-30
I mean sure there is some closed source code included with most Android phones but, how usable would the system be without it?   I don't really see the difference between say what Valve is doing with SteamOS and what google is doing with Android.   Google is a billion dollar company and has the most to gain from it's success of course it's going to have the most say in the path Android takes.  But, if somebody over at Cyanogenmod/Samsung/HTC codes something better or fixes a bug how often does it end up back in the android source tree?

---

### Post by 3rdalbum on 2014-07-31
There are two main binary-only pieces to a typical distribution of Android:

1. Hardware drivers and firmware
2. Google Play Services and many preinstalled apps

The first thing, Hardware drivers, is impossible to live without. You can't run Android on a phone or tablet without them, and they are closed source because the manufacturers of phone components do not make them open-source.

There's an effort to reverse-engineer these components so open-source drivers can be written, and maybe even open-source firmware. The effort is going very slowly, though. I don't have much hope for it, frankly.

The second thing, the Google Play Services and preinstalled apps, is entirely possible to live without. The Android Open Source Project ships a default gallery app, a default music app, a default dialler etc that are all open-source. Unfortunately they are not really maintained and not very special. For Google-certified devices, the manufacturer gains the ability to ship the better, closed-source equivalents along with Google Maps, Google Play Store etc.

A phone running AOSP is usable, but a bit dull. You also miss out on Google Play Services (closed-source) which is a requirement to run most Android apps these days. Many new Android features actually go into Google Play Services because it can be updated independently of the base OS. Of course, you'll miss out on any of those new features if you are running AOSP only.

---

### Post by vasa1 on 2014-07-31
[http://arstechnica.com/gadgets/2014/07/exploring-the-world-of-foss-android-can-a-smartphone-be-open-source/](http://arstechnica.com/gadgets/2014/07/exploring-the-world-of-foss-android-can-a-smartphone-be-open-source/)

---

### Post by grahammechanical on 2014-07-31
[https://source.android.com/](https://source.android.com/)

---

### Post by anachronism2 on 2014-07-31
So, if Android is open source, does that mean any given user may modify the source code on a PC, import to the phone, and use custom- built OS and apps, aside from the proprietary ones? Theoretically

---

### Post by PondPuppy on 2014-07-31
The open-source Android X86 project ports Android to, as you might guess, PC chipsets. I've run one of the earlier versions -- Ice Cream Sandwich, I think -- on a netbook. It's useful enough for light stuff on a small screen. Dunno about app store access, though. [http://www.android-x86.org/](http://www.android-x86.org/)

---

