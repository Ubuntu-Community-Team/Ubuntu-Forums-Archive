---
title: "Graphical Lag? Very Slow Galago Pro"
date: 2013-10-09
forum: System76 Support
---

### Post by zysh on 2013-10-09
Hey all, just got my Galago UltraPro and loving it. I've been having some issues with what I assume is a graphics card issue since I haven't seen my CPU go out of control yet. I'm still using Ubuntu 13.04 with Unity 3D.
When I first got the laptop I attempted to run a game via steam (dota2) but ended up with some poor performance and decided to worry about it later on.

A few days back I realized that when I leave the laptop alone for a few hours then come back to do some work, everything is extremely slow. The mouse will 'drag' and opening/switching chrome tabs prompted some lag. Tying in chrome prompts lag as well.
 Opening terminals also prompts lag.

After searching around for a bit I decided to try and upgrade to Kernel 3.8.2 and mesa 9.2. Luckily enough dota2 renders wonderfully now, but I'm still getting this weird graphical 'lag' when the computer is unattended for a few hours.
This seems to go away once I restart the computer. All upgrades & updates are applied.

Any idea what this could be? I've been trying to monitor processes but I really can't tell whats up. I assumed at first it may be an issue with chrome but the graphics lag continues once the browser is closed.

I've been thinking about upgrading the kernal again. There was a post on Phoronix awhile back about getting some nice performance with a 3.11 kernel.

---

### Post by Laiquendi on 2013-10-09
Have you monitored the resources? Like swap, ram etc?

---

### Post by zysh on 2013-10-09
Yeah I'm looking at it now. I lied when I said the CPU is getting a bit out of control. Ram looks fine, swap looks fine, but it looks like the CPU% is skyrocketing for any interaction, looks like it's getting to at least 80% when I drag chrome across the screen.

---

### Post by isantop on 2013-10-09
Make sure it's plugged into power. If it's running on battery, the CPU scales back too much to be much good playing games.

---

### Post by zysh on 2013-10-09
I opened up a support ticket and was advised to upgrade to 3.11 kernel. Everything looks good so far but I'll report back.

---

