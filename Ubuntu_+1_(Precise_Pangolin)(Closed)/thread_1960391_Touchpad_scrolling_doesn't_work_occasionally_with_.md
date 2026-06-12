---
title: "Touchpad scrolling doesn't work occasionally with Nautilus"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by palimmo on 2012-04-17
Touchpad scrolling doesn't work occasionally with Nautilus.
I can scroll up-down just on the right side, but not in the center of the page or in other points.
In the same time it works normally in Firefox.
I'm not able to reproduce this bug. However I have noticed it just in these two last days.

Ubuntu 12.04 beta2 64bit
Packard Bell TJ65
[https://bugs.launchpad.net/ubuntu/+bug/983910](https://bugs.launchpad.net/ubuntu/+bug/983910)

---

### Post by mc4man on 2012-04-17
I had noticed the same in my previous install(s) updated 32/64 bit

Put in new installs a couple of days ago but haven't upgraded the xserver-xorg-input-synaptics package, currently using  - 
xserver-xorg-input-synaptics (1.5.99.902-0ubuntu3

Hasn't re-occurred yet but being a 'random' thing maybe too early to tell.
If desired you can downgrade with package from here, use 
dpkg -i on the deb
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu3/+build/3384000](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu3/+build/3384000)

---

### Post by palimmo on 2012-04-18
> **mc4man said:**
> I had noticed the same in my previous install(s) updated 32/64 bit

Put in new installs a couple of days ago but haven't upgraded the xserver-xorg-input-synaptics package, currently using  - 
xserver-xorg-input-synaptics (1.5.99.902-0ubuntu3

Hasn't re-occurred yet but being a 'random' thing maybe too early to tell.
If desired you can downgrade with package from here, use 
dpkg -i on the deb
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu3/+build/3384000](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu3/+build/3384000)

maybe you can subscribe the bug at the link I have previous posted...
and the developers will give it more attention...

---

### Post by the-oggy on 2012-04-18
Same here, subscribed to bug

---

### Post by Squonk07 on 2012-04-18
Put in my two cents at the bug as this affects me, too. I've been getting it sporadically now for a week or so, with no discernible pattern. A reboot solves it for a while, but then it comes right back.

---

### Post by mc4man on 2012-04-18
> **Squonk07 said:**
> Put in my two cents at the bug as this affects me, too. I've been getting it sporadically now for a week or so, with no discernible pattern. A reboot solves it for a while, but then it comes right back.
I haven't gotten this yet since putting in 2 new installs with the 04/14 image, now fully updated. (inc the xserver-synaptic package

When it has happened to you does it affect anything other than nautilus like gedit, ect?

---

### Post by Squonk07 on 2012-04-18
> **mc4man said:**
> I haven't gotten this yet since putting in 2 new installs with the 04/14 image, now fully updated. (inc the xserver-synaptic package

When it has happened to you does it affect anything other than nautilus like gedit, ect?
 
I've noticed it in Update Manager as well. I'll have to check if it affects other programs the next time it happens. I know it doesn't seem to affect Firefox as it often goes unnoticed until I open Nautilus and discover it's happened again.

---

### Post by mc4man on 2012-04-18
I just noticed that on the install I use the most - 04.14 image, 64 bit, I had locked the package, (xserver-xorg-input-synaptics)  @ 1.5.99.902-0ubuntu3
So I'll upgrade it & see what happens over the next day or so

If it does turn out to be involved then pending a fix or the behavior just stopping for some other reason I'll just return to the 0ubuntu3 version
None of the changes since 0ubuntu3 are of any value here

> xserver-xorg-input-synaptics (1.5.99.902-0ubuntu5) precise-proposed; urgency=low

  * Fix coasting speed on multitouch touchpads (LP: #930938)
    - Add patch 203_fix_coasting_speed.patch

 -- Chow Loong Jin <hyperair@debian.org>  Fri, 13 Apr 2012 16:14:04 +0800

xserver-xorg-input-synaptics (1.5.99.902-0ubuntu4) precise; urgency=low

  * Fix crash on Apple trackpads when touching with more than 10 fingers
    (LP: #974017)
    - Add temporary patch 202_touch_record_bounds_check.patch

 -- Chase Douglas <chase.douglas@ubuntu.com>  Mon, 09 Apr 2012 11:44:26 -0700

12.04 has presented a number of issues with run of the mill touchpads like I have here (Dell 1330m

---

### Post by Squonk07 on 2012-04-18
It just happened again, and it seems to affect almost all programs. Except, I've noticed that the programs with normal (non-slim) scrollbars (e.g. Firefox, Thunderbird, LibreOffice) seem to work properly. I also notice that there's a very small margin (about the width of a standard scrollbar) where trackpad scrolling still works with the slim bars.

Also, scrolling works properly in Wine programs. Also, a full reboot doesn't seem to be required. Just logging out and then back in again seems to fix it for a while.

EDIT: The overlay scrollbars don't seem to be the trouble, at least on the surface, as uninstalling them doesn't solve the problem. I've noticed the problem seems to happen more often when I've used Wine, though that might just be coincidence. Unfortunately, the older versions of the xserver-xorg-input-synaptics package seem to have already been purged from the repo (showpkg only shows the latest version), so I can't check to see if downgrading will help.

---

### Post by mc4man on 2012-04-18
> **Squonk07 said:**
> , the older versions of the xserver-xorg-input-synaptics package seem to have already been purged from the repo (showpkg only shows the latest version), so I can't check to see if downgrading will help.

here's the full list for precise
[https://launchpad.net/ubuntu/precise/+source/xserver-xorg-input-synaptics](https://launchpad.net/ubuntu/precise/+source/xserver-xorg-input-synaptics)

I'd try this one - click on your arch under "Builds"
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu3](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu3)

---

### Post by Squonk07 on 2012-04-18
> **mc4man said:**
> here's the full list for precise
[https://launchpad.net/ubuntu/precise/+source/xserver-xorg-input-synaptics](https://launchpad.net/ubuntu/precise/+source/xserver-xorg-input-synaptics)

I'd try this one - click on your arch under "Builds"
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu3](https://launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/1.5.99.902-0ubuntu3)

Thanks a bunch! So far, so good. I've got the older version locked so I don't have to worry about it getting upgraded accidentally, and I'll be watching to see what happens with that package in the future.

---

### Post by mc4man on 2012-04-18
> **Squonk07 said:**
> Thanks a bunch! So far, so good. I've got the older version locked so I don't have to worry about it getting upgraded accidentally, and I'll be watching to see what happens with that package in the future.

So if it stops over a day or so report back, that'll  at least be  some indication that the cause is in or related to the xserver-xorg-input-synaptics  upgrades of late.

---

### Post by Squonk07 on 2012-04-19
After about a day I haven't had the scrolling lock up once, so I think that's a pretty strong indication that the xserver-xorg-input-synaptics package is the culprit here. Now we need to figure out what changed that's causing this issue. I get the impression that there is some specific conflict somewhere because if it were a more general problem with the package I would expect a lot more activity in this thread.

---

### Post by mc4man on 2012-04-19
> **Squonk07 said:**
> After about a day I haven't had the scrolling lock up once, so I think that's a pretty strong indication that the xserver-xorg-input-synaptics package is the culprit here. Now we need to figure out what changed that's causing this issue. I get the impression that there is some specific conflict somewhere because if it were a more general problem with the package I would expect a lot more activity in this thread.

In post 8 I posted the changelog for the 2 packages after 1.5.99.902-0ubuntu3
In both cases the changes were just a single  patch to the current source
So assuming you are using 1.5.99.902-0ubuntu3, then go back to the link for all precise versions, download the next one & update (-0ubuntu4

Try that one for an extended time, if no occurances then update to -0ubuntu5 & see
(so far I haven't had it happen here yet but that may not be indicative.

Are you on 32 or 64 bit?

---

### Post by Squonk07 on 2012-04-19
64 bit here. I'll go ahead and update to the next version and see what happens.

---

### Post by Squonk07 on 2012-04-21
The next version up (ubuntu4, one version before the current one) worked without fault after day of testing. The current version still freezes up, so that seems to indicate that the bug is in the latest version.

---

### Post by mc4man on 2012-04-21
> **Squonk07 said:**
> The next version up (ubuntu4, one version before the current one) worked without fault after day of testing. The current version still freezes up, so that seems to indicate that the bug is in the latest version.

It's recently  been mentioned in the current report that "patch 203_fix_coasting_speed.patch" seems to be the cause for someone else

So for yourself, till or if fixed you may as well use the 0ubuntu4 version
If you have a LP account you could comment that the 203 patch causes also in the report

---

### Post by Squonk07 on 2012-04-21
Done. Hopefully the ball can get rolling on this now. I'm glad I was able to help, even if it was just installing and testing a few different versions of a package.

---

### Post by Squonk07 on 2012-04-25
Just to bring this thread back up from the depths one last time, it seems this issue has been solved in an upcoming update (it's currently in precise-proposed). I've been testing version 0ubuntu5.1 now for over a day and I haven't had the scrolling lock up once.

---

### Post by ubuntu27 on 2012-04-26
> **Squonk07 said:**
> Just to bring this thread back up from the depths one last time, it seems this issue has been solved in an upcoming update (it's currently in precise-proposed). I've been testing version 0ubuntu5.1 now for over a day and I haven't had the scrolling lock up once.

Thanks for the heads up! :popcorn: I was getting very worried about this issue.

EDIT: 

> **palimmo said:**
> Touchpad scrolling doesn't work occasionally with Nautilus.
I can scroll up-down just on the right side, but not in the center of the page or in other points.
...

[https://bugs.launchpad.net/ubuntu/+bug/983910](https://bugs.launchpad.net/ubuntu/+bug/983910)

The new URL for the bug report is:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/982771](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/982771)

The previous bug report has been marked as duplicate.

---

