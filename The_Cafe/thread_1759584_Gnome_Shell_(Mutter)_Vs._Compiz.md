---
title: "Gnome Shell (Mutter) Vs. Compiz"
date: 2011-05-15
forum: The Cafe
---

### Post by screaminj3sus on 2011-05-15
I have noticed after trying Unity and Gnome 3 on a few machines, that mutter seems far faster and more stable than compiz.

I've used natty on both ati and intel video cards (ati hd2600 with fglrx and oss driver, intel Iron Lake), both of them have a few annoying visual bugs. The minimze animation is sometimes a little laggy, the minimize animation has some visual glitches near the top left if you minimized a mazimized window, and the fade out animation on app indicators has an annoying white flicker. 

Mutter handles window resizing far better. I can't even enable "normal" window resizing mode in compiz or its horrifically slow, gnome shell its totally fine. Generally it doesn't seem very "smooth" compared to gnome shell or aero. I don't think I've seen even one visual "quirk" yet with mutter, compiz is full of them.

Gnome shell also handles thumbnails for minimized windows fine, unlike compiz.

I've seen a lot of people say how compiz is so much better and how there was no reason for gnome to switch away from it, but I couldn't disagree more. Gnome shell seems far less buggy and much smoother. I think the complains about it being slow are based on old pre-release versions of mutter. I remember trying it quite a while ago and it was indeed slow as hell, but it has improved* a lot.*

---

### Post by 3Miro on 2011-05-15
There is no reason for compiz to be lagging in windows resizing. You may be hitting some specific bug. Install CCSM and try playing with the compiz settings, see if you can get better performance (with some Workaround or compatibility).

Compiz has never been part of Gnome, may distributions used compiz by default because Metacity was fast, but very lacking on features. On the same note, Compiz doesn't fully integrate with Gnome and hence it cannot show thumbnails of minimized windows. AFIK only Kwin does that.

The main issue of Gnome moving away from "compiz" is not compiz, but the standard. Compiz, Metacity, Kwin, Xfwm4, OpenBox ... all of them work on the same standard and they can easily replace on another on the fly (i.e. I used Gnome + OpenBox and I know some people that used KDE + Metacity).

---

### Post by murderslastcrow on 2011-05-15
Well, at first I thought it was a bit crazy to arbitrarily use a window manager that isn't replaceable in the Shell environment (as to allow Compiz to be used as a compositor). But after studying Clutter a bit and understanding their decision for choosing it, it just makes a whole lot of sense from a developer's perspective, and the majority of users like eye candy, but aren't so picky that they need compiz or bust. Gnome 3 doesn't really target Compiz users, just as it doesn't target applet users or Gnome DO users. But it does target people who like compositing, useful indicators, and integrated searching. So essentially, the devil is in the details if you're addicted to all the traditional software that's built up around Gnome 2 (the same issues happened when moving from KDE 3 to 4, but it was, for the most part, necessary).

I love Unity because it's an odd amalgam of technologies that have been crucial to Ubuntu giving Gnome 2 a nicer face, but integrated in such a way that the maturity of many of the elements shows very obviously (notifications and Compiz, for instance). Unity is the first DE to actually take Compiz into account as the default compositor/window manager, so I think it has a long and lustrous life ahead of it.

In most cases, Mutter and Compiz will perform around the same, but Clutter tends to do better in a lot of cases just because of how it's built, its recency, and all the help they get from Intel. I mean, that's a huge part of Gnome 3 is just how partners were involved to make it a great release. It's kind of hard for typical Ubuntu users to see what happens when they can't easily try the software (Linux really is so gift-wrapped, these days).

---

### Post by Jesus_Valdez on 2011-05-15
Reddit?

---

### Post by murderslastcrow on 2011-05-15
Oh, by the way, I'm on the open driver for an ATi HD 3450 card and Mutter has some weird lag maximizing/resizing windows, while on the same driver Ubuntu doesn't. Ironically, fglrx makes Unity unusable, and Gnome 3 quick as butter, just full of artefacts XD. So on my hardware I can't really vouch for the situation, while Unity hasn't even started on all the Intel graphics cards I used (probably because they're all pre-2005).

They each have their share of issues, but it looks like all the official environments have said good bye to old video hardware, even if they're very light (I get 300 MB RAM use in Gnome 3, max). In general, if you're using officially supported hardware with official drivers, (NVIDIA blob, ATi Catalyst, Intel), you should do some research and file a bug report. But for the most part there are too many small issues with unsupported hardware to say that either Unity or Mutter is smoother. On recent hardware there shouldn't be any visible difference in performance.

Also, I think it's important to note that Unity and Compiz in Ubuntu is now a bit different from straight Compiz. At least from my experience, the code acts very differently and different bugs show up in common compiz elements.

---

### Post by michaelzap on 2011-05-16
> **screaminj3sus said:**
> I have noticed after trying Unity and Gnome 3 on a few machines, that mutter seems far faster and more stable than compiz.

I've used natty on both ati and intel video cards (ati hd2600 with fglrx and oss driver, intel Iron Lake), both of them have a few annoying visual bugs. The minimze animation is sometimes a little laggy, the minimize animation has some visual glitches near the top left if you minimized a mazimized window, and the fade out animation on app indicators has an annoying white flicker. 

Mutter handles window resizing far better. I can't even enable "normal" window resizing mode in compiz or its horrifically slow, gnome shell its totally fine. Generally it doesn't seem very "smooth" compared to gnome shell or aero. I don't think I've seen even one visual "quirk" yet with mutter, compiz is full of them.

Gnome shell also handles thumbnails for minimized windows fine, unlike compiz.

I've seen a lot of people say how compiz is so much better and how there was no reason for gnome to switch away from it, but I couldn't disagree more. Gnome shell seems far less buggy and much smoother. I think the complains about it being slow are based on old pre-release versions of mutter. I remember trying it quite a while ago and it was indeed slow as hell, but it has improved* a lot.*
I also was amazed at how smooth Gnome Shell is and how little RAM and CPU it uses. It uses less RAM than my Xfce Debian system! I really like Compiz for some systems, but I think that the Unity devs have made a major mess of it.

---

### Post by NightwishFan on 2011-05-16
I like mutter better. It seems like it was a bit slow in earlier versions but it runs great now. Also these "quirks" the OP speaks of I can confirm happen a lot less on mutter than compiz.

---

### Post by BlacqWolf on 2011-05-16
To me, Compiz seems fast but not all that stable. I've had it crash once or twice on me before. A few other times I encountered hanging. I still use it though as the issues aren't very constant.

Mutter just seems to lag window arrangement a bit and the effects are boring and they don't even fit in to the environment that well, though I've never encountered a crash with it.

---

