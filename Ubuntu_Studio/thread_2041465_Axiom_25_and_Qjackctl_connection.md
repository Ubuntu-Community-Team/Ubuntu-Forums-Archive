---
title: "Axiom 25 and Qjackctl connection"
date: 2012-08-12
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2012-08-12
Hello, 

So I recently connected my Axiom 25 keyboard controller and I would like connected to programs like Hydrogen and Ardour. The problem is out of all the things listed in the connection screen, I don't know what to connect to what.

I have attached a couple of screen shots to show what I mean. I noticed all the connections for the axiom 25 show up only in the alsa tab.

Thanks ahead for the help, 

[ATTACH]222607[/ATTACH]

[ATTACH]222608[/ATTACH]

---

### Post by sgx on 2012-08-13
Hi, run these two commands twice, one with the computer started,
the axiom not connected, and no software apps running, and then
again, after plugging in the axiom

cat /proc/asound/cards

aplay -l

If the axiom is detected, it should display some relevant name within brackets, when running the commands the second time.

Look in qjackctl setup page, on the right side,

Input Device >

click the > widget, and hope there is something like you see
in the brackets from the commands.
Cheers

---

### Post by CrocoDuck on 2012-08-14
Hi. When I use my keystation88es I go to the ALSA tab in connections, I select "keystation88es" then I connect it where I need (ZynAddSubFX, Hydrogen, other virtual keyoboards to use MIDI tab etc). Have a try by selecting "Axiom 25" and connecting it to "Hydrogen" (for example). Making some experiment playing around with connections should not ruin things...

---

