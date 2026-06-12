---
title: "Themes messed up..."
date: 2012-03-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by exploder on 2012-03-10
Anyone else notice that some menus items will only highlight one time? When I click on items that will not highlight they still work and do turn orange when I click on then. My system has been like this all week and was wondering if anyone has a bug report on this?

---

### Post by dino99 on 2012-03-10
some details please, is it with unity 2D/3D ?

---

### Post by exploder on 2012-03-10
It's both Unity 3D and 2D. Also, the new scrollbars are not usable.

---

### Post by tista on 2012-03-10
@exploder,

I imagine if you used ricotz/testing ppa?
If so, it might be caused gtk 3.3.18/19 bugs...

Same issue +1 for me.

---

### Post by exploder on 2012-03-10
I have not used any ppa repos.

---

### Post by screaminj3sus on 2012-03-10
I have this issue too, known bug with gtk in precise:
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949414](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949414)

Should be fixed by beta 2.

Here's the bug report for the scrollbar bug (this effects me too)
[https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/951121](https://bugs.launchpad.net/ubuntu/+source/overlay-scrollbar/+bug/951121)

They both seem to be issues eith the recent gtk updates.

---

### Post by dino99 on 2012-03-10
> **exploder said:**
> I have not used any ppa repos.

then close all your apps, then try:

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by mc4man on 2012-03-10
Possibly this ?
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949029](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949029)

I see none of that here, all menus work fine (nvidia), though whenever gtk+3 upgrades something somewhere always seems to break..
If you can I'd try the current live image in a live session & see how that works

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-10
Yes, I've noticed this on my installation. But I'm not sure which version of Unity I'm using. There is a thread on this forum and a bug report on Launchpad for the scrollbar bug, but not for menu highlighting.

---

### Post by screaminj3sus on 2012-03-10
> **&#1058 said:**
> Yes, I've noticed this on my installation. But I'm not sure which version of Unity I'm using. There is a thread on this forum and a bug report on Launchpad for the scrollbar bug, but not for menu highlighting.

Here's the menu highlighting bug:
[https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949414](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/949414)

---

### Post by exploder on 2012-03-10
mc4man, that is the bug I am seeing. Thanks!

---

### Post by mc4man on 2012-03-10
> **exploder said:**
> mc4man, that is the bug I am seeing. Thanks!

Even though that bug was reported first it's likely the same as the one linked by screaminj3sus in post 6
If so then that would be the bug to watch now, has current attention

---

### Post by exploder on 2012-03-10
I tried todays daily build on my main computer and the menus work alright using a mouse instead of a touchpad. There are some entries that I have to hover the mouse over to get all the text to show up though.

On a side note I was surprised to see plymouth working with the nvidea graphics on my main computer, it displays huge but it is displaying using the proprietary drivers. Startupmanager is not currently showing in the repos or I would try and get plymouth to display better.

Anyway, the bug has a priority of "High" and I am sure it will get resolved before beta 2 arrives.

---

### Post by mc4man on 2012-03-10
> **exploder said:**
> I tried todays daily build on my main computer and the menus work alright using a mouse instead of a touchpad. There are some entries that I have to hover the mouse over to get all the text to show up though.
.

That may be this bug which shows fixed released but I don't believe has actually yet been released. If not should be in the next upgrade of compiz plugins*

[https://bugs.launchpad.net/compiz-core/+bug/931473](https://bugs.launchpad.net/compiz-core/+bug/931473)

I built the plugin here a while back & the problem is gone, it was, at least then, in the workarounds plugin 
(when fixed you'll see this option in ccsm > workarounds which should stay enabled

---

