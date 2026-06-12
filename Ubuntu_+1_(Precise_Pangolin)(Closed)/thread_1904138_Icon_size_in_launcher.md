---
title: "Icon size in launcher?"
date: 2012-01-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by candtalan on 2012-01-04
Does anyone know if the Icon size in the launcher is going to have any size options any time soon?

I took a few CDs of 11.10 to a techy DIY meeting recently and someone had a need of an immediate install of something to test a webcam. The 11.10 worked well, except that on the fairly large display (approximately 20 inches) and on the relatively old machine - (quite common) - the icon size looked huge (awful, in a bad way). The size looked like one inch across although I did not want to measure it (and draw even more attention to it!) and the first reactions were that the display parameters were simply not configured correctly. However, the resolution was 1024x768 which was the highest available from that machine. These numbers are not altogether bad, and the machine was not running at all slow. The ad hoc audience and user are the very same group of self confident tech type of people who would start using Ubuntu and run with it, but the lack of a (simple?) option for small icons in the launcher gave a really poor impression.

(FWIW I like Unity and I am an active advocate for Ubuntu)

Edit: ah! In my installation of Precise, updated, I have now installed compiz settings manager, and I see that in the Ubuntu Unity Plugin, Experimental, there is a Launcher Icon Size slider. Currently not apparently effective, but  this looks very hopeful

---

### Post by ajgreeny on 2012-01-04
As you say this is an old machine, it may only be running unity-2d in which I don't think the icon size is editable.

Maybe I am wrong, but I am not running unity at all, so very likely I know nothing!

---

### Post by hansdown on 2012-01-04
Hi, candtalan.

If you install 

```
myunity
```

You can resize the icons more effectively, than whith compiz.

---

### Post by grahammechanical on 2012-01-04
The Unity Plugin experimental options do work. I have been able re-size my icons to the lowest possible size and also to reduce the opacity of the top panel to zero (makes it transparent).

But as already noted, this has no effect in Ubuntu 2D and that is because Ubuntu (Unity 3D) uses Compiz as the window or compositing manager and Ubuntu 2D uses metacity.

The install process will set up a default user environment. It does not install proprietary video drivers, which may be needed for running the 3D effects. Depending on the machine you may end up with 2D or a limited 3D because the open source video drivers are work in progress.

Likewise it does not install Compiz Configuration Settings Manager because some of the other Compiz effects are not well intergrated with Unity (things break). Compiz intergration with Unity is also a work in progress. 

In my opinion it would have been better if these Compiz effects had been removed from CCSM until proven to work and then re-installed by updates. This should have been done when Unity was brought in with 11.04. I would not be surprised to one day see a Unity Settings utility in System Settings by default that removes the need to install CCSM. It would be a front-end for CCSM.

I do not want to moan too much about Compiz because I have seen the Xmas blog post of the Compiz maintainer and he is under a lot of stress. And I know what that is like.

I am running a 20 inch DTV/monitor at 1680 x 1050 and I admit that the default icon size does look large for my preference. I keep in mind that the intention is for Unity to work well with touch screens and some people might like large icons on a touch screen.

Regards.

---

### Post by effenberg0x0 on 2012-01-04
> **grahammechanical said:**
> 

In my opinion it would have been better if these Compiz effects had been removed from CCSM until proven to work and then re-installed by updates. This should have been done when Unity was brought in with 11.04. I would not be surprised to one day see a Unity Settings utility in System Settings by default that removes the need to install CCSM. It would be a front-end for CCSM.

I do not want to moan too much about Compiz because I have seen the Xmas blog post of the Compiz maintainer and he is under a lot of stress. And I know what that is like.


Completely agree with you. Also, ccsm can be set to know which plugins are broken. But I'm backing off a little on the compiz bug reporting/dev "pressure" since I read that. I had the impression Canonical was providing more help to compiz since they choose it to be the base for Unity but it seems unfair to leave it in the hands of a single maintainer.

---

### Post by cariboo on 2012-01-04
I don't think that it is Canonical that isn't giving Sam extra support, from what I recall he had very little programming experience when he took over maintaining Compiz, he may have bitten off a little more than he can chew, with a complete rewrite.

Looking at the latest changelog, it looks like Sam is getting help from Didier Roches and Matthias Klose.

---

### Post by 1roxtar on 2012-01-05
The app MyUnity is in the software center and is a great tool for Unity 3D.  It is very simple to use and does it's job very well.  For noobs, I'd stay away from CCSM.  Resizing the icons and launcher in the 2D version is something I'd like to see too.  Especially for a netbook, the icons look too big.

---

