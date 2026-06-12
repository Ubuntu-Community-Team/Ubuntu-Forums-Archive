---
title: "3d sound program"
date: 2008-07-23
forum: Ubuntu Studio
---

### Post by amoose136 on 2008-07-23
Hello,

I am looking for a free software that functions like [this]("http://www.hitsquad.com/smm/programs/AirTrafficControl/") plug-in for audacity.


[INDENT]"Software Description

AirTraffic Control lets you work with your sounds on a map. You see a simple plan view of the room you are in with your speakers or headphones. Input and output channels are objects on the map. Outputs are like ears: the nearer the inputs come, the easier it is to hear them.

Feature summary:

    [LIST]
[*]Inputs and outputs are symbols on a map of your listening area.
[*]    Up to 16 input channels and 8 output channels are available.
[*]    An output channel is like an ear, and displays an outer circle for its limit of hearing.
[*]    Audio parameters are adjusted by moving inputs and outputs on the
[/LIST]
map, and by dragging on the circles to change their size. 

AirTraffic Control lets you place what you want to hear where you want to hear it. A wave of the mouse can be dramatic as a sound sweeps across your listening space.[/INDENT]"

I tried that plug-in in windows and all the graphics are removed so that it is just a bunch of sliders and is therefore, useless. I am looking for the same thing in Linux. (Maybe separate from audacity also) What should I use? Also, I am currently un-able to record any sound... but that's another problem for another day.

I have access to computers with Ubuntu 8.04, Hardy Heron (with compiz) and Windows XP, Home Edition.

Thanks in advance.

---

### Post by Stochastic on 2008-07-24
Ardour's multi-channel panning system (in the mixer window) operates very close to this.  There is also the Ambisonic Encoder/Decoder plugins that work great for giving realistic spatialization.

When you say "just a bunch of sliders and is therefore, useless" I wonder why you come to that conclusion.  All a "map" has is slider values for x and y, if you take the map away, the sliders should still work.  But I could be misunderstanding you.

---

### Post by amoose136 on 2008-07-24
> **Stochastic said:**
> When you say "just a bunch of sliders and is therefore, useless" I wonder why you come to that conclusion.  All a "map" has is slider values for x and y, if you take the map away, the sliders should still work.  But I could be misunderstanding you.

Well, kind of. There were about 25 sliders and none of them seemed to work. There were already sliders in audacity so to take away the map would be to take away the automation of the effect. Without it, I could just split the track into two tracks, set each track to a different speaker and then adjust volume levels. I'm doing this because I want to do a [foley]("http://en.wikipedia.org/wiki/Foley_artist") project.

I'm trying out Ardour right now. It looks like it should work for more then anything I will ever need it for.

Thanks for the reply.

---

