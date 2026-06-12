---
title: "Firefox 3.5, 3.6 bug - Anyone else affected?"
date: 2010-04-08
forum: Ubuntuzilla
---

### Post by Umang on 2010-04-08
I reported LP:502367 a while back, but there's been no response (and nobody has confirmed it). Could some visit [http://www.adobe.com/](http://www.adobe.com/), try to hover over the menu and see if the menu is hidden under the flash content?

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/502367](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/502367)

Bug on Launchpad:> This is a regression from lp:49613. Using Firefox 3.5, on [http://www.adobe.com/](http://www.adobe.com/), when I hover over "Solutions", the menu is partially covered by the flash object.

This was fixed in Firefox 3.0, however I am still facing this issue in Firefox 3.5. Bug 49613 claims this was fixed for Firefox 3.

I'm using Firefox 3.5.6 (3.5.6+nobinonly-0ubuntu0.9.10.1) on Ubuntu Karmic Koala 9.10 and Shockwave Flash 10.0 r42.
It still affects me on Firefox 3.6.

---

### Post by nanotube on 2010-04-09
hi umang
just posted a response to your lp bug. 
sorry to say, but everything looks fine on my ff 3.6.3.

---

### Post by Umang on 2010-04-09
That's odd. Do you have any idea on how I can try to fix the problem or what might be causing it? I've got FF 3.6.3 and Flash 10.0 r45.

---

### Post by sgosnell on 2010-04-09
Your resolution may be messed up.  You may be zoomed in too much or something.  That's about all I can come up with.  It looks fine to me.

---

### Post by Umang on 2010-04-09
I did a Ctrl+plus+plus then Ctrl+0 (Reset zoom) and the menu is still hidden by the flash.

EDIT: Safe mode doesn't help either.

---

### Post by sgosnell on 2010-04-09
Perhaps a problem with the flash player?  Like I said, the page looks fine to me.

---

### Post by cradom on 2010-04-09
3.5.8 here and aside from the first item in the Store menu not showing all else is fine.
(It's actually there, just the white background not showing)

---

### Post by Umang on 2010-04-10
I'll try reinstalling the flash player later today, but here's the screenshot (just in case): [http://launchpadlibrarian.net/43634388/Screenshot.png](http://launchpadlibrarian.net/43634388/Screenshot.png)

---

### Post by sgosnell on 2010-04-10
On my machine, the menu is shown on top of the flash, and I can see it all, no problem.  I'm not sure what is causing that on yours, but I have seen something like that in previous versions of Firefox, 2.x IIRC, where the menus were transparent.  I don't recall the cause or the fix, though, it's been a very long time.  It had something to do with my playing around with the settings, but I can't recall exactly what I had done.  You might try removing and reinstalling Firefox, but you'll have to make sure you remove the .mozilla folder under /home, and that will remove all your settings, so you may not want to do something that drastic.  You may be able to fix it through a setting, but I'm not sure where to start, because I don't know what you've done.

---

### Post by Umang on 2010-04-10
Creating a new profile (using `firefox -P`) didn't help. I'll try reinstalling both firefox and the flashplugin and see what happens.

---

### Post by Umang on 2010-04-12
`sudo apt-get install firefox-mozilla-build flashplugin-installer --reinstall` didn't help either. I guess it's most probably something I've changed somewhere. So I will just wait for Lucid, I think.

---

