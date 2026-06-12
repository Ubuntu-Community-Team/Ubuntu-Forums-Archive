---
title: "Are you experiencing Adobe Flash Player issues ?"
date: 2016-01-23
forum: The Cafe
---

### Post by 200Dave on 2016-01-23
Try installing Pepper Flash Player. Easy Breezy

[https://wiki.debian.org/PepperFlashPlayer/Installing](https://wiki.debian.org/PepperFlashPlayer/Installing)

---

### Post by oldos2er on 2016-01-23
Not an Ubuntu support request; moved to Cafe.

---

### Post by yoshii on 2016-01-23
what about support for Trusty?  That doesn't seem to be in the linked page... ?

---

### Post by ajgreeny on 2016-01-23
> **yoshi2 said:**
> what about support for Trusty?  That doesn't seem to be in the linked page... ?
You can already add all that's needed for trusty by enabling the canonical partner repos and installing adobe-flashplugin which gives you the latest flash version for chromium, 20.0.0.267; you can use the same flash version in firefox by enabling the nilarimogard-webupd8 repos at [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) and installing freshplayerplugin.

---

### Post by poorguy on 2016-01-23
what are the adobe flash player issues.

---

### Post by Christopher_Stayne on 2016-01-24
The only issue I have seen is where it doesnt seem to work under Chromium.  I installed pepper flash but have yet to see if it made any difference.

---

### Post by Mike_Walsh on 2016-01-24
I find it works perfectly under Chromium. I've even written a tutorial on the Puppy Linux Forums about using the most up-to-date PepperFlash with an older Chromium browser; it's very easy to swap the 'libpepflashplayer.so' module around.

[http://www.murga-linux.com/puppy/viewtopic.php?t=101275](http://www.murga-linux.com/puppy/viewtopic.php?t=101275)

Puppy's a wee bit different, of course.....but the underlying principle remains the same. It should be adaptable to Ubuntu, if you want to try it.


Mike. ;)

---

### Post by poorguy on 2016-01-25
Guess I have been lucky as I am not having any problems with chromium.
In firefox I no longer use adobe flash anything and no more firefox problems.
MPV player for firefox seems to take care of any flash needs.

[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

---

### Post by ajgreeny on 2016-01-25
I can not figure out why you are having the problem with flash, nor why you seem to need to install the pepperflash-plugin which I understood was no longer being developed.

For the record, I have just yesterday installed Lubuntu 14.04.3 on an old netbook with an Atom CPU, 1GB ram, and 160GB HDD, added Adobe-flashplugin from the partner repos, and freshplayerplugin from the nilarimogard repos.

I now have flash version 20.0.0.267 working well in both Firefox and Chromium according to [http://www.adobe.com/uk/software/flash/about/](http://www.adobe.com/uk/software/flash/about/)

---

### Post by night_sky2 on 2016-01-25
Good old' Adobe Flash 11.2 for Firefox works well for my needs. It's pretty stable and no issue.

I still receive security updates once in a while so no complaint there.

---

### Post by ajgreeny on 2016-01-26
> **night_sky2 said:**
> Good old' Adobe Flash 11.2 for Firefox works well for my needs. It's pretty stable and no issue.

I still receive security updates once in a while so no complaint there.
That would be fine except for the very few sites that insist on flash version above 15 (I think it was 15) and refuse to work with the 11.2 default version in Linux.

---

### Post by night_sky2 on 2016-01-26
> **ajgreeny said:**
> That would be fine except for the very few sites that insist on flash version above 15 (I think it was 15) and refuse to work with the 11.2 default version in Linux.
Yeah but I haven't encountered many of those websites. I don't bother with them anyway.

Adobe flash 11+ is still accepted pretty much everywhere. That is because Android is stuck on the 11xx branch as well.

---

### Post by monkeybrain20122 on 2016-01-27
> **night_sky2 said:**
> Yeah but I haven't encountered many of those websites. I don't bother with them anyway.

Adobe flash 11+ is still accepted pretty much everywhere. That is because Android is stuck on the 11xx branch as well.

But this guy is apparently having problems [http://ubuntuforums.org/showthread.php?t=2311381&p=13429722#post13429722](http://ubuntuforums.org/showthread.php?t=2311381&p=13429722#post13429722)

Personally I seldom need flash so I actually disable it in Firefox and use the mpv addon instead. It works for most sites I visit anyway.

---

### Post by night_sky2 on 2016-01-27
> **monkeybrain20122 said:**
> But this guy is apparently having problems [http://ubuntuforums.org/showthread.php?t=2311381&p=13429722#post13429722](http://ubuntuforums.org/showthread.php?t=2311381&p=13429722#post13429722)
You're right but as _ajgreeny_ pointed out above, there are very few of those websites causing trouble at this point. The issue is that they specifically require adobe flash 15+, which obviously won't work with the 11.2 plugin for Firefox on Linux. It all depends on your needs, to me, I can live with it (still accepted in the vast majority of flash sites) and switch to HTML5 wherever available.

---

