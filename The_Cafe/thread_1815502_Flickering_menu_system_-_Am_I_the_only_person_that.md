---
title: "Flickering menu system - Am I the only person that notices it?"
date: 2011-07-31
forum: The Cafe
---

### Post by simpleblue on 2011-07-31
To some this may sound picky or non-existant but once you notice it you may change your mind...

What flickering am I talking about?

I'm talking about when you use the global menu system in Unity 11.04 and you switch from one tab to the next (say switching from 'file' to 'edit' or 'view') using the right or left arrow key or by dragging your mouse accross then tabs while holding the left mouse button.

The intial tab draw, when it first appears, is fine. It just 'pops' into place, as if out of nowhere, but as soon as you go to another tab or you let go of that tab then it flickers white, then disappears. That quick flashing of white is the flicker. Perhaps it wouldn't be so noticable if it flickered a dark charcoal grey as the default menu background is coloured, but it does not. It flickers an all out white, and even on my Asus i7 gaming laptop it's easily noticable, so I don't think it's a speed issue.

If you want to see what I mean and you don't have Unity then take a close look at this video between 5s - 20s:
[http://www.youtube.com/watch?v=MFvk1I-uUXw](http://www.youtube.com/watch?v=MFvk1I-uUXw)

I think that while some people might not notice this flickering it may still be registered in the mind as a feeling that something is just not right, or that the distro just doesn't feel 'polished' or stable enough.

For comparison, take a look at Gnome Shell. I've yet to see a noticable flicker in it. The menu at the top 'pops' on and off perfectly. It goes to add to the overall feeling of a solid, polished look. For this reason I would choose to show a newbie Gnome Shell instead. The same goes for playing Youtube videos. I remember they used to flicker when transitioning to fullscreen after the fullscreen button was pressed. Upon installing flashsquare there was absolutely not flicker. The thought that came to my mind was, "Damn, this is sooo smooth. This is starting to look very high quality."

Anyways, I have a feeling this is going to end up with more comments about me being unneccissarily picky, and perhaps in some ways I hope that's true, though I have a feeling that this flickering is unwelcome to many others. But please, do me a favour and look for yourself. Play around a little with different systems and really try to pay close attention to what's redrawing during switching menus... Then, if you don't agree, or you agree, comment. Don't just say, "Well, looks fine to me" or "I don't notice it", without even comparing or trying it out.

---

### Post by coffeecat on 2011-07-31
To be honest, I hadn't noticed this before - at least not until I watched the first few seconds of that video. Yes, it is noticeable and troubling on the video. No, it is barely noticeable and not at all troubling on my system because the white "flicker" lasts barely a fraction of a moment on my system. Which makes me think that it might vary according to the GPU and video driver in use.

@simpleblue, is that your video in the link? If not, is the white flickering as bad on your system and what GPU/driver are you using?

---

### Post by simpleblue on 2011-07-31
> **coffeecat said:**
> @simpleblue, is that your video in the link? If not, is the white flickering as bad on your system and what GPU/driver are you using?
Thanks for testing it out. :) ... No, that is not my video, but I've had 11.04 on 3 laptops and I can see the flicker in all of them (Nvidia and Intel drivers).

---

### Post by kaldor on 2011-07-31
It is present on my machine as well, but not nearly as severe. It's noticeable when I look for it, but otherwise it's fine.

---

### Post by AnotherMuggle on 2011-07-31
> **simpleblue said:**
> To some this may sound picky or non-existant but once you notice it you may change your mind...

I have just tested with the computer I am using at the moment (Intel Atom N450 Netbook with 2GB RAM) and I see the same flickering you are describing and showing in the video.  It would look better if it didn't flicker but at the same time, for me, it's a minor niggle and it doesn't bother me.

---

### Post by Tibuda on 2011-07-31
It looks like a compositing issue.

---

### Post by coffeecat on 2011-07-31
> **simpleblue said:**
> (Nvidia and Intel drivers).

Proprietary nvidia driver or nouveau for the nvidia card? I was judging by a machine with an ATI Radeon HD4350 card using the open source driver where the flickering is barely noticeable. I'll have a look on my Intel GPU netbook later.

---

### Post by AnotherMuggle on 2011-07-31
> **coffeecat said:**
> Proprietary nvidia driver or nouveau for the nvidia card? I was judging by a machine with an ATI Radeon HD4350 card using the open source driver where the flickering is barely noticeable. I'll have a look on my Intel GPU netbook later.

I can see it on my netbook, however, it's only noticeable when the active window is NOT maximised.  With a maximised window the transition is still there but it so minor it's almost invisible.

---

### Post by NCLI on 2011-07-31
Can't see it on 11.10, so maybe it's been fixed?

---

### Post by simpleblue on 2011-07-31
> **coffeecat said:**
> Proprietary nvidia driver or nouveau for the nvidia card? I was judging by a machine with an ATI Radeon HD4350 card using the open source driver where the flickering is barely noticeable. I'll have a look on my Intel GPU netbook later.
It's been a while since I've had Unity installed, and between all the other distros I've tried inbetween I'm no longer longer 100% sure.

---

### Post by FuturePilot on 2011-07-31
Most likely a driver issue. Can't reproduce it here.

---

### Post by simpleblue on 2011-07-31
> **NCLI said:**
> Can't see it on 11.10, so maybe it's been fixed?
I've just had a look at several 11.10 Youtube videos and it seems that a good half of these new videos don't have that issue at all. I also noticed that the ones that did not flicker seemed to have fading compiz effects, which btw, looked awesome. :)

So I'll cross my fingers and hope that it's fixed for Ocelot.

---

### Post by Larkspur on 2011-07-31
> **simpleblue said:**
> So I'll cross my fingers and hope that it's fixed for Ocelot.

I think it has.  I remember reading about it in one of the progress reports on omgubuntu.

---

### Post by pelle.k on 2011-07-31
Yes, **i have indeed noticed this**. It bugs me to no end. I'm willing to bet my left arm it has something to do with the global menu patch, applied to gtk/metacity in natty, since even the classic gnome desktop in natty have the same problem (both with the menubar in the window, or the new global menu on the top panel). I'm not having this problem with other distros though.
I'm on intel HD 3000 graphics btw (mbp 8,1).

---

### Post by cariboo on 2011-08-01
I'm running Oneiric here with nvidia using the proprietary driver, and there isn't any discernible flicker.

---

### Post by lucazade on 2011-08-01
It has been fixed.
This was the bug report: [https://bugs.launchpad.net/unity/+bug/687567](https://bugs.launchpad.net/unity/+bug/687567)

---

### Post by simpleblue on 2011-08-01
> **lucazade said:**
> It has been fixed.
This was the bug report: [https://bugs.launchpad.net/unity/+bug/687567](https://bugs.launchpad.net/unity/+bug/687567)
Sweet! Thanks for looking it up.

Looks like I'll be using Ocelot as one of the distros of choice to show to my friends. :p

:popcorn:

---

