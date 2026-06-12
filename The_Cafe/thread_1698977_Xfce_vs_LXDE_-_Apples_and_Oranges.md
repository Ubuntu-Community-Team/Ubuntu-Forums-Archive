---
title: "Xfce vs LXDE - Apples and Oranges"
date: 2011-03-03
forum: The Cafe
---

### Post by toowoombalinux on 2011-03-03
G'day,
I have a few old Dell laptops - 256mbs 1Ghz 20gbs HD, and wanted to experiment with something a little more mature than just Puppy Linux - which works wonders on them. Formatted HD each time.

So I first tried Mint 9 LXDE, and here are the results... (formatted HD each time)
LiveCD boot time = 8 mins
Installation time = 55 mins
Bootup time = 72 secs
Abiword launch = 18 secs

Then I tried Xubuntu 8.04.1 and here are the results....
LiveCD boot time = 3.5 mins
Installation time = 37 mins
Bootup time = 49 secs
Abiword launch = 3 secs

Did not find out RAM usage as just looking at real-time results.
Why?
Could it be that the older Kernel is more suited to the older hardware.  I would have thought that LXDE being lighter would have been quicker even with some incompatibilities.

I will also try Lubuntu to see if it's quicker...

Cheers
Martin

---

### Post by whatthefunk on 2011-03-03
I reckon Lubuntu will be way quicker.

---

### Post by wilee-nilee on 2011-03-03
Try archbang, it is arch with openbox, idles on my computer at less the 100Mib.
[http://archbang.org/](http://archbang.org/)

---

### Post by ajgreeny on 2011-03-03
See my post 25 in thread [http://ubuntuforums.org/showthread.php?p=10516045#post10516045](http://ubuntuforums.org/showthread.php?p=10516045#post10516045) for some info on Lubuntu.

---

### Post by 3Miro on 2011-03-03
On my laptop I had Arch installed with LXDE and XFCE. LXDE worked better on an external monitor, it was faster and more responsive. On the native screen, there is virtually no difference and I prefer the extra option by XFCE.

One should be mindful of the way LXDE and XFCE are packaged. Often times distributions stuff those with Gnome applets and additional gnome things that end up slowing the system.

Other notes: Install time depends on the internet connection among other things (depending on how you installed it). *ubuntu servers may be faster than Gnome.

Abiword: if Abiwork uses a library that XFCE also uses, then that library would be loaded at boot time and Abiword would be faster to start. If this library is not loaded in LXDE, then it will be loaded when Abiword starts and hence the start would be slower.

If you want to compare the two environments, don't time things like that (it is unreliable data). Instead start using XFCE and LXDE and all of their features and then decide which one you like better.

---

### Post by kn0w-b1nary on 2011-03-03
I would recommend for minimalism and speed,

Tinycore, (look on youtube for videos on tinycore by a user called sneakylinux)
Kolibri OS, not usable in the long run, but with a 4.8 mb .iso, it's worth a fling.

EDIT: Kolibri OS only needs 8 mb of RAM.

---

### Post by johntaylor1887 on 2011-03-03
> **kn0w-b1nary said:**
> I would recommend for minimalism and speed,

Tinycore, (look on youtube for videos on tinycore by a user called sneakylinux)
Kolibri OS, not usable in the long run, but with a 4.8 mb .iso, it's worth a fling.

I agree with TinyCore Linux. It takes a bit of getting used to, but will run very fast on 256 ram or less.

---

### Post by koleoptero on 2011-03-03
Crunchbang linux openbox or xfce is what I used for a similar laptop and it just flies. Try it you won't be disappointed.

Plus it is based on debian so if you use ubuntu you'll know most of the commands, you won't have to learn some weird elvish language to do updates as a friend once told. :)

---

### Post by frankbooth on 2011-03-03
> **whatthefunk said:**
> I reckon Lubuntu will be way quicker.

Yeah, Lubuntu is WAY faster than Xubuntu.

---

### Post by Hur Dur on 2011-03-03
Just running a window manager would be beneficial. IceWM is a light, highly customizable one. Openbox, though heavier than IceWM, JWM, and Fluxbox, is also very customizable. FVWM is also a good one for extra eye candy with less resource usage than any desktop environment. Also, I recommend Arch for a system like that. A barebones GNOME install only uses about 56mb RAM on it. Using it with IceWM, you can easily achieve 24mb RAM at startup with X.

Also, this really isn't a fair comparison, as there are too many variables. Different distro, different services at start up.

---

### Post by toowoombalinux on 2011-03-03
> **3Miro said:**
> On my laptop I had Arch installed with LXDE and XFCE. LXDE worked better on an external monitor, it was faster and more responsive. On the native screen, there is virtually no difference and I prefer the extra option by XFCE.

One should be mindful of the way LXDE and XFCE are packaged. Often times distributions stuff those with Gnome applets and additional gnome things that end up slowing the system.

Other notes: Install time depends on the internet connection among other things (depending on how you installed it). *ubuntu servers may be faster than Gnome.

Abiword: if Abiwork uses a library that XFCE also uses, then that library would be loaded at boot time and Abiword would be faster to start. If this library is not loaded in LXDE, then it will be loaded when Abiword starts and hence the start would be slower.

If you want to compare the two environments, don't time things like that (it is unreliable data). Instead start using XFCE and LXDE and all of their features and then decide which one you like better.

G'day,
Thanks for the replies everyone - greatly illuminating.

I don't understand why timing is unreliable data (my timing is from a group average).  If a programme or OS is unresponsive then it doesn't matter how much RAM is used - it's how quick it runs - then the most empirical data for the average user is timing.  Now I could waffle on with the programmes I timed (and results always were in favour of Xubuntu), I just wanted to show a particular contrast.

I help introduce Linux to a broader community; do they care that LXDE uses less RAM or Xfce is faster?  I don't think so - if a programme gets working in a shorter time then that's what matters.

Eg: I use Puppy Linux both KDE and JWM for the past 4 years - JWM uses 35mbs and KDE uses about 120mbs - I have timed a number of programmes (excluding K progs) and have found the response times to be roughly similar.

Yes I luv my stopwatch!!!

Oh and the Laptop was not plugged into the internet when installing.

Cheers
Martin

PS. Crunchbang and Tiny Core are a little too geeky for the newbie-set which is my focus.
PPS. Puppy Linux rocks!!!

---

### Post by Austin25 on 2011-03-03
I have to say that although not quite a lightweight distro, Knoppix runs LXDE rather nicely.

---

### Post by BrokenKingpin on 2011-03-04
I found the Xubuntu to be a bit heavy just because they still keep a lot of Gnome stuff. If you do a barebones Ubuntu install and then install XFCE and SLIM login manger, you end up with a really quick system, but still quite user friendly.

---

