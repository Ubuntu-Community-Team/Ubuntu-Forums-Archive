---
title: "Clickpad support on HP Envy 14"
date: 2012-03-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nicocarbone on 2012-03-03
Hi. 

I am using Ubuntu 12.04 (beta 1 fresh install) and I have a HP Envy 14 laptop which uses a synaptic clickpad. I understand that precise now supports natively clickpads, however I am having some problems.

I can right-click, and left-click by a two-finger tap. But, I can't find a way to middle click. This pad has "soft buttons", an area in the pad which is supposed to simulate a physical button. They are not working in precise, pressing in the area dedicated to left-click does a right click like the rest of the pad. Clicking in the middle of the area dedicated for right and left buttons should trigger a middle-click, but this doesn't work either.

Is this how the click pad is supposed to work? Or this is a bug? Do I have to change something to enable this functions?

Thanks you.

---

### Post by roboconnell on 2012-03-14
I'm having trouble also with the Synaptics touchpad on my HP Envy 14 (1110 I think variant). I'm also having trouble with click-dragging (tends to end up clicking and not dragging) and general performance of the clickpad is fairly poor.

(Everything else is working great...4-5 hr battery life, with vgaswitcheroo and the RC6 on the i915)

I guess I'll head over to Launchpad to report bug...

---

### Post by balloons on 2012-03-14
File some bugs.. clickpad support is still early, even for precise. Beta2 should be better. However, the current plan is that more of the right click /left click areas will come with an SRU and in the next cycle. Feedback was being solicited on this issue recently.

---

### Post by onefthemany on 2012-03-18
create a folder in /etc/X11/:

xorg.conf.d

then create a file named 51.clickpad.conf and paste the following in to the file:

#script to add clickpad support for HP Envy 14

Section "InputClass"
Identifier "Default clickpad buttons"
MatchDriver "synaptics"
Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"

EndSection

#

Once you have done this simply log out and log back in again the clickpad will work with right and left click functionality


Also do not bother with the righclick.sh as this no longer works with the full 12.04 release

good luck

---

### Post by Sammy142 on 2012-03-18
I'm having trouble also with the Synaptics touchpad on my HP Envy 14 (1110 I think variant).

---

