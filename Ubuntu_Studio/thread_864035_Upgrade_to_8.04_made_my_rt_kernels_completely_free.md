---
title: "Upgrade to 8.04 made my rt kernels completely freeze"
date: 2008-07-19
forum: Ubuntu Studio
---

### Post by kuovsk.anekask on 2008-07-19
I finally upgraded a couple of weeks ago and near the end of the upgrade I briefly ran out of space on my root partition while it was upgrading the kernel, but almost everything works fine, except for my kernel. I use a realtime kernel for audio work (JACK), and it constantly freezes - completely. Nothing works. Mouse doesn't move, keyboard doesn't work, sometimes the audio loops. Only thing that works is my reset button. If I boot any of my old real-time kernels they do the same, but all my generic kernels are fine. 

I can't ssh in, ctrl+alt+f1 or ctrl+alt+backspace doesn't do anything, everything in /var/log looks normal. I've tried reinstalling it and all the packages I can find related to the rt kernel but the crashes persist. 

I've looked around for similar posts but for everyone else the RT kernel seemed to be the *fix* - the opposite to my situation. So does anyone have any ideas on what's causing my problem, or should I just downgrade? 
(mods: I've probably posted this in the wrong place, please move it as you see fit)

---

