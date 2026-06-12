---
title: "burning dvd on Brasero"
date: 2009-02-07
forum: Ubuntu Studio
---

### Post by bu2971x on 2009-02-07
I am trying to burn a video file onto DVD. I would like it to be compatible
with an Oppo dvd player,DV 980H that uses hdmi 480 720  1080 etc.
I tried it in Brasero and the Oppo(hdmi) said resolution not supported.
I tried it in Svideo and it said same thing.Anybody know how to do this??
Maybe another burner that lets you choose resolution..????
whats the scoop..????  thanks
8.04 Ubu

---

### Post by Tharmas on 2009-02-26
The problem is not with your dvd burner software.
Is it MPEG4 (Xvid, DivX,...) in .avi?
Usually (don't know if that's your case) dvd players don't play such movies with width resolutions above 720 pixels. Even if they use hdmi 480 720 1080 etc.
If your video has width resolution higher than 720, I advise you to resize it with avidemux to something like 720x400 for an aspect ratio of 16:9 or 640x480 for an aspect ratio of 4:3. Save the file as .avi, burn it again and try it in your dvd player.

---

