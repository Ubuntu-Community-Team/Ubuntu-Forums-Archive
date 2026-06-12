---
title: "Anyone else have this problem?"
date: 2008-01-14
forum: The Cafe
---

### Post by sajro on 2008-01-14
How's this for random?

Middle-click in your Firefox (if you're using it on Ubuntu). Not on a link and not with that scrolling thing. If you have the same glitch I do, it goes to a random site doesn't it?

It's so weird. Sometimes it does others it doesn't. Today's culprit is igg.com. This is the strangest software bug I've ever encountered. 

Has anyone else had this happen to them or did I just royally screw up my Firefox?

---

### Post by bufsabre666 on 2008-01-14
mine opens the quick scroll thing, no random site

---

### Post by x0as on 2008-01-14
It goes to whatever text you've highlighted.  It's meant to do it.

---

### Post by jasay on 2008-01-14
From my experiments, it seems as though firefox is opening websites based on whatever you have in the highlight/middle click cache.

For instance, if I highlight "Ubuntu" and middle click on nothing, it brings me to [http://www.ubuntu.com/](http://www.ubuntu.com/).  "open" brings me to American Express?

Edit: Dang took too long.

---

### Post by santiagoward2000 on 2008-01-14
In my case, unless I click on a link, the middle button is doing nothing on Firefox :confused:

---

### Post by p_quarles on 2008-01-14
> **sajro said:**
> How's this for random?

Middle-click in your Firefox (if you're using it on Ubuntu). Not on a link and not with that scrolling thing. If you have the same glitch I do, it goes to a random site doesn't it?

It's so weird. Sometimes it does others it doesn't. Today's culprit is igg.com. This is the strangest software bug I've ever encountered. 

Has anyone else had this happen to them or did I just royally screw up my Firefox?
I've had the same thing happen on a few occasions, but only since I switched from Firefox to Swiftweasel. It's definitely strange, and I'd like to figure out why that's happening.

---

### Post by zipperback on 2008-01-14
> **sajro said:**
> 
Has anyone else had this happen to them or did I just royally screw up my Firefox?

Nothing happens when I do it.

What plugins and extensions have you loaded?

- zipperback
:popcorn:

---

### Post by init1 on 2008-01-14
It is rather unusual, but it's a feature not a bug. It takes you to whatever you have selected, so if you select a URL it will take you there when you middle click it. This is convenient for times where the URL has been displayed as plain text rather than a link. If nothing is selected, it will try using the contents of the clipboard instead.
> **zipperback said:**
> Nothing happens when I do it.

What plugins and extensions have you loaded?

- zipperback
:popcorn:
That's because you have nothing selected and nothing copied.

---

### Post by Praadur on 2008-01-14
I've heard of this.

I'd help you test with the latest build of Swiftweasel but unforunately I don't have a middle mouse button right now (touchpad).  What I can say though is that this is often caused by a bad extension or theme, most likely a theme more than anything from what I've read.

This can be problematic if the browser you're using utilises a non-default theme (like Swiftweasel unfortunately does, but I'll forgive it because it's still the best amd64 option) in its native state, or if it comes with extensions pre-installed.

Try installing another theme, and disabling extensions one at a time until you find the culprit.

-

Ah, if apparently this is a valid feature (as I've read above my post, I was typing this one whilst they were made) then it's definitely going to be either a theme, an extension, or possibly even a source patch.  I'm actually quite interested by this now, so if anyone does track down that which adds this feature, do post back.

---

### Post by sumguy231 on 2008-01-15
It is indeed a feature built into the browser, and you can change it:
1.) Go to 'about:config' in the location bar.
2.) Put 'middlemouse.contentLoadURL' in the filter.
3.) Double-click to turn to false.

If you want to turn on the autoscroll cursor, you can do that in the advanced preferences.

---

### Post by Praadur on 2008-01-15
Ooh, if it's in about:config then it actually is a new (and official) feature?  That seems... ah...  Would there be any practical uses for that?

---

### Post by sumguy231 on 2008-01-15
It's not actually new (and it is official), it's been the default in the Linux version for a long long time. I think the Ubuntu packages might normally override it, though.
It's supposed to be more consistent with classic Unix/X11 behavior, though that makes little sense on a modern desktop system like Ubuntu.

---

### Post by Praadur on 2008-01-15
Ah, that's certainly shed some light on the darkness, thanks for the information!

It's interesting though that some builds might not be overriding it for Linux desktops, as it seems like the middle mouse button could be used for other tasks on modern desktops, indeed.

It's also mildly entertaining that I never learned of this because I don't use the middle mouse-button anymore.  I just had to hook up my Logitech Trackman though to see, and it seems that I have this enabled by default too (Swiftweasel 3.0b2).

---

### Post by sumguy231 on 2008-01-15
As a note, you can emulate having a middle button in X.org. I don't recall how to do it, but it's enabled on my system and I don't remember enabling it so maybe it's on by default. Just try clicking both buttons at the same time to see if it is.

---

### Post by Praadur on 2008-01-15
I didn't seem to have that on by default, but I gather this is because over the months I've had to rebuild my xorg.conf a couple of times, and perhaps an item or two got lost along the way.

What I did find though was [this explanation on how to disable that functionality](http://ubuntuforums.org/showthread.php?t=452139).  I did the reverse and voila, I now have a middle mouse button... and it's actually fairly neat.  Thanks again.

---

