---
title: "remote gaming on netbook: netbook + network + powerful desktop"
date: 2010-07-16
forum: The Cafe
---

### Post by earthpigg on 2010-07-16
Thoughts rolling around in my head.

My Atom netbook certainly is not powerful enough to render 30 frames per second of Urban Terror - it gets like 18 fps in Tux Racer.

But it ***is*** powerful enough to display 30 frames per second and output an audio stream, all rendered from my desktop (>90 FPS Urban Terror).

Other old computers are also powerful enough to display 30 fps and output an audio stream. Maybe even p4-era stuff.

using x forwarding over ssh returns things like this:

```
$ etracer **#tux racer is the game mentioned above that gets 17fps on my netbook**
Extreme TuxRacer SVN Development --  http://www.extremetuxracer.com 
(c) 2007 The ETRacer team
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
ETRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

*** etracer error: Couldn't initialize video: Couldn't find matching GLX visual (Resource temporarily unavailable)

```

and ssh with x forwarding tends to be a lot slower than the connection allows, anyways. anyone that has ever run synaptic over ssh knows this.

So, I suppose I have two options:

1) Any way to get x-forwarding (or hardware acceleration) to work well with games over ssh?
2) What other options are there for fast x-forwarding? Or, just raw image forwarding at a reasonable number of raw images per second? assume security is not a major concern.

---

