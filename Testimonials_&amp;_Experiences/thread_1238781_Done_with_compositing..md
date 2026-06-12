---
title: "Done with compositing."
date: 2009-08-12
forum: Testimonials &amp; Experiences
---

### Post by NTolerance on 2009-08-12
After a couple of years trying the different Ubuntu/GNOME compositing methods I think I give up for now.  There's just too many regressions as compared to non-composited setups, and too many negative interactions with various software.  I run Ubuntu on a HP dv6000t laptop equipped with an NVidia 7400 Go CPU.  Here's my experiences with three compositing systems:

**Compiz**
1.  NVidia driver bug causes headache-inducing fullscreen flickering when Powermizer changes clock frequencies.
2.  VNC performance is slow due to extra eye candy.  compiz-switch is nice, but why can't we intelligently disable Compiz only during VNC sessions?
3.  Nomachine's "shadow" feature to control the local display doesn't work with Compiz.  
4.  Game performance can sometimes suffer while Compiz is running.  
5.  Another NVidia bug causes VNC to fail completely with Jaunty.

**xcompmgr**
1.  Performance is poor, uses lots of CPU time.
2.  Even though it's been out for years, it still crashes so often that you can't depend on it.  

**Metacity Compositing**
1.  Causes video playback to have horrible tearing/vsync issues.  Completely unwatchable.  

I understand that a lot of the problems with Compiz are NVidia's fault, but what can be done about this?  The other options (AMD and Intel) have their own share of problems.  Intel performance is horrid in Jaunty and will likely remain so for a long time given the major changes that are being made to that driver.  From what I've heard AMD's drivers are still behind NVidia's, and NVidia is giving me fits already.  

I don't expect xcompmgr to be any kind of real solution as it may be abondoned in favor of other options.  Metacity compositing offers some real hope in that it doesn't depend on shoddy video drivers, but then there's the vsync bug which makes it unusable.  

All this being said, what's the best course of action to get usable compositing in Ubuntu?

---

### Post by Ranax on 2009-08-12
I find that KWIN works flawlessly on Kubuntu 9.04 under nVidia, although my install is modified quite a lot over the standard OoTB Jaunty. I can play games fullscreen with KWIN enabled without  the annoying issues you get with Compiz or any noticable performance penalty. I can run videos fullscreen without any issues also. In Compiz if I try that, going anywhere near the edge of the screen causes it to flicker between the video/game and desktop.

---

### Post by Methuselah on 2009-08-12
I enabled compiz for a while as an experiment then turned it off subsequently.
It does not always play nice with other software due to limitations of the underlying X Server.

---

### Post by armandh on 2009-08-13
the overkill temtation is the problem [for me]
as long as I avoid conflicting effects and/or conflicting enabling key strokes, OOTB ubuntu and  down loaded CompizConfig Settings Manager work fine [for me] BUT not with any low mem on board video.

---

### Post by murderslastcrow on 2009-08-13
Some video cards don't play as nicely as others. If the video-card is right, you can run compiz just fine on 256 MB of RAM.

---

### Post by 3rdalbum on 2009-08-14
> **NTolerance said:**
> **Compiz**
1.  NVidia driver bug causes headache-inducing fullscreen flickering when Powermizer changes clock frequencies.

Is that what that is then? I only get it when using Opera, and even then only rarely.

> 2.  VNC performance is slow due to extra eye candy.  compiz-switch is nice, but why can't we intelligently disable Compiz only during VNC sessions?

It is a little. I think you should submit a feature request to the Gnome developers as I don't know if it's possible for other, uninvolved programs to tell if there's an incoming VNC connection.

To tell you the truth, I have Compiz running on my home server and VNC isn't really too bad.

---

