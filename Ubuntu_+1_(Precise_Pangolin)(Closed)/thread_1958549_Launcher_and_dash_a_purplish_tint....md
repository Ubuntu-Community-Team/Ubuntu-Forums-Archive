---
title: "Launcher and dash a purplish tint..."
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by thebelial on 2012-04-14
I have my dash and launcher set to a specific color through ccsm. After a recent reboot, it ignores my ccsm settings and uses a purple tint. When I try to reset the settings in ccsm, it changes back to what I had until I either minimize ccsm, or just take focus off of it. Then it's right back to purple.

Is anyone else having this issue? I've tried login/out, reboots.

---

### Post by mc4man on 2012-04-14
[http://ubuntuforums.org/showthread.php?t=1958355](http://ubuntuforums.org/showthread.php?t=1958355)

---

### Post by thebelial on 2012-04-14
Thanks

---

### Post by VinDSL on 2012-04-17
> **mc4man said:**
> [http://ubuntuforums.org/showthread.php?t=1958355](http://ubuntuforums.org/showthread.php?t=1958355)
Thanks!

Added a "me too" & comment, in Launchpad.

> Me too...

In my case, I use a greenish wallpaper, and the "Launcher" and "Dash" take on an ugly greenish tint, once they are focused, regardless of which custom background color I choose.

Example: Let's say I choose "#000000" (black) as the custom background color, for the "Dash". When I boot, the background is black initially, but quickly changes to a greenish tint, once it focuses on the desktop.

No amount of tinkering with MyUnity, CCSM, Ubuntu-Tweak, et cetera, changes this.

**Edit**

BTW, has anyone come up with a workaround yet?

---

### Post by mc4man on 2012-04-17
> **VinDSL said:**
> Thanks!

Added a "me too" & comment, in Launchpad.



**Edit**

BTW, has anyone come up with a workaround yet?

Just to note - even if it held your settings you cannot use #000000 as an override, if you do so the panel will have blacked out icons.
That was something that occurred when they enabled this coloring deal & also is quite unfortunate
[https://bugs.launchpad.net/unity/+bug/924586](https://bugs.launchpad.net/unity/+bug/924586) 

note the date, this may not get fixed, I had used #000000 with a moderate opacity to slightly darken the dash & produce a sort of smoked glass launcher


As far as the ability to have the custom color setting hold there is no workaround other than to revert to the 5.8 unity which probably isn't a realistic option due to 5.10 having some significant fixes

However if they release as is there will be quite a number of complaints & rightly so - many Backgrounds produce a crappy looking launcher

---

### Post by VinDSL on 2012-04-17
> **mc4man said:**
> Just to note - even if it held your settings you cannot use #000000 as an override, if you do so the panel will have blacked out icons.
Indeed!  As it stands, if I select #000000, in CCSM, the icons turn black.

But, as soon as I close CCSM, they revert back to "olive drab green".

I suppose the results will vary, depending on the color of your desktop wallpaper.

---

### Post by mc4man on 2012-04-17
What I had found to create a subdued launcher in the absence of #000000 was to set a single rgb, for Ex. blue @ 1 g & r @ 0 then fool with the opacity. 
Unfortunately (to me), that creates blue non-favorite icons so then I'd switch the Backlight Mode to 'Backlight & Edge Ill.. toggles' 
That effectively removes coloring from the icons

(I certainly do get that many, maybe most, like colored icons - I don't
So hopefully at a min. the custom color ability comes back, the #000000 may be more problematic & never return.

Edit: you may be in better shape because it appears you replaced all the non-favorite icons anyway?

---

