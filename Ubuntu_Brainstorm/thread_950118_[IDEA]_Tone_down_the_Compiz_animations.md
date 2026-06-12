---
title: "[IDEA] Tone down the Compiz animations"
date: 2008-10-16
forum: Ubuntu Brainstorm
---

### Post by rockin_goliath on 2008-10-16
Compiz is a very nice addition to the desktop. The use of drop shadows, scaling windows, zoom animations for minimizing and maximizing windows, and the Expo function to display your workspaces are great ways of making the desktop more physical, productive and fun to use. However, the open, close, and "fading zoom" (when you click on an icon on the panel are not functional at all, and are most of the time distracting, which reduces our work flow. They also don't look that great when used on computers with low refresh rates on the display. 

I propose that those three animations, open, close and icon zoom, be disabled completely, leaving the other functions mentioned above constant.

---

### Post by cardinals_fan on 2008-10-16
> **rockin_goliath said:**
> Compiz is a very nice addition to the desktop. The use of drop shadows, scaling windows, zoom animations for minimizing and maximizing windows, and the Expo function to display your workspaces are great ways of making the desktop more physical, productive and fun to use. However, the open, close, and "fading zoom" (when you click on an icon on the panel are not functional at all, and are most of the time distracting, which reduces our work flow. They also don't look that great when used on computers with low refresh rates on the display. 

I propose that those three animations, open, close and icon zoom, be disabled completely, leaving the other functions mentioned above constant.
I'm confused.  Are those settings enabled by default?

---

### Post by rockin_goliath on 2008-10-16
The ones mentioned in the second paragraph are.

---

### Post by pastalavista on 2008-10-16
Compiz is a bit much for me. Too much going on. I love the tricks it does but they're too confusing to configure and they won't stay saved when I have to disable it to watch full-screen video.

---

### Post by smartboyathome on 2008-10-16
I think that we got a good balance right now. If we disable those, people will be saying "Give us more Compiz Effects! I want my animations!". If we enable more effects, people will say "Tone down Compiz Effects!/Get rid of Compiz!".

Personally, those effects you mentioned are ones I personally like. It makes Compiz *smoother* for me, which increases my productivity.

---

### Post by gnomeuser on 2008-10-17
I voted turn it off by default. The reason has nothing to do with the effects settings as such but rather that the underlying technology just isn't there yet.

We need kernel modesetting, DRI2 and GEM to be solid before you can accomplice simple things such as playing a movie without the window becoming black when it's moved around. 

Add to this the fact that we simply need better drivers, the free ones we have only the radeon (r200-r500) and the intel drivers are properly supported. The proprietary ones are riddled with problems and cause odd crashes (such as when I use the nvidia driver on my laptop, it tends to tear or misrender the window decorations, also I am seeing many more application crashes when these drivers are enabled due to nvidias wrong assumptions on stack usage in the kernel).

As a technology Compiz is probably fine, we could look forward to the day when we can enable it by default for everyone with a tasteful set of animations. But it has been wrongly assumed ready for far to long, the underlying technology isn't here yet and Canonical is doing nothing to correct this situation.

I also doubt that Compiz is all we need, it only gives us very broad effects, we will also want more subtle effects such as what clutter enables us to do in applications. The whole desktop should be a bit more alive and getting there solely by way of Compiz effects seems implausible.

---

