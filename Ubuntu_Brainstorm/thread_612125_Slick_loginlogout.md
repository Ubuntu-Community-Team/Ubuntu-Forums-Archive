---
title: "Slick login/logout"
date: 2007-11-13
forum: Ubuntu Brainstorm
---

### Post by chrisccoulson on 2007-11-13
I was reading [this]("http://architectfantasy.com/?p=1") article a short while back, and I do think it has some valid points - especially concerning the overall polish surrounding the implementation of Compiz. For example, the author points out the fact that Compiz exits before some other running applications on logout, causing undesirable artefacts. The example the author gives is with Cairo Clock, where a black area appears behind the clock on logout. I assume a similar thing could happen with things such as Avant and Screenlets.

Currently when I log in to Gutsy, it appears that Metacity starts, then the panels appear, then disappear again as Metacity is replaced with Compiz, before finally appearing again. Then the applets appear randomly one-by-one on the panels.

This doesn't look very polished. I don't want to start a flamewar, but when you log into Vista, the desktop fades nicely in to view.

I know there is a spec on Launchpad for slick-boot. Do people think that there should also be a spec for improving the login/logout phases as well? (I couldn't find one on Launchpad, and AFAIK, slick-boot only goes as far as GDM).

If there is enough support, I'd be more than happy to draft a blueprint for it (but I might need a bit of support with that)

---

### Post by smartboyathome on 2007-11-13
I would say this is definately needed since the Splash Screen was taken out of Gutsy! Maybe haev a Baou-like splash screen (for those of you that don't use XFCE, it covers the whole screen and tells you the process of what is loading, then dissapears when it loads), and then fades out after everything else is loaded.

---

### Post by 23meg on 2007-11-13
It can be a good idea to write a separate blueprint, since [slick-boot]("https://blueprints.launchpad.net/ubuntu/+spec/slick-boot") doesn't seem to cover the GNOME startup/shutdown phases, and there seems to be no other blueprint that does. Let me know if you need help with it.

But the thing to note is that slick-boot has been declined for discussion in UDS-Boston, and doesn't look like it will go ahead in Hardy; the whiteboard note indicates that shortage of workforce is the reason. As always, writing the blueprint isn't enough; we need people to do the actual work.

---

### Post by DizzyTech on 2007-11-13
*cough*Splashy*cough*

---

### Post by 23meg on 2007-11-13
*cough*Topic*cough*

---

### Post by chrisccoulson on 2007-11-13
I'll have a go at starting a blueprint tomorrow when I've finshed work. I understand that there would probably be too much work in this to target at Hardy, although I'll help out where I can. It's a shame that there isn't the manpower to deal with the pile of blueprints that seem to have been open for quite a while:(

smartboyathome: I haven't seen the splash screen for XFCE before. Does Xubuntu ship with it? And does the fade out work without compositing? (I ask because I might try it out in a virtual machine tomorrow)

DizzyTech: Isn't splashy an alternative to usplash? If so, then we're talking about different things;)

---

### Post by smartboyathome on 2007-11-13
> **chrisccoulson said:**
> smartboyathome: I haven't seen the splash screen for XFCE before. Does Xubuntu ship with it? And does the fade out work without compositing? (I ask because I might try it out in a virtual machine tomorrow)

It doesn't fade in even with compositing (I think). I can't remember though, as I haven't used XFCE in a while.

Also, it isn't default in Xubuntu, wish it was though :(

---

