---
title: "Software emulated slow-mo effects?"
date: 2008-08-27
forum: The Cafe
---

### Post by Jimmey on 2008-08-27
Does anybody know of any method to edit/enhance a video taken with a normal camera to make it look like it was captured using a special motion-capture camera?

Basically, a normal camera would capture at around 25 frames per second, meaning in normal playback you'd see 25 separate images every second - Resulting, when playing back at normal speeds, in fluid movement.

If you were to slow this video down a great degree, basically you're just spacing the number of frames over a greater number of seconds - And if you were to slow it down alot, you'd end up such a low number of frames per second that it becomes noticeably flickery/jagged.

I'm sure there'd be some software or method that, when there's a really low number of frames per second, could "guess" the difference between each frame, and fill in the gaps by adding extra, generated frames.

Does anyone know if this is possible? Or if there's any software to do it?

---

### Post by Daveski on 2008-08-27
Cinelerra has an interpolate frame video effect, but the 'guessed' frames are basically a weighted disolve of the frames on either side. This smooths the video somewhat, but will never fool you into thinking that it is real high-speed footage.

---

### Post by kpkeerthi on 2008-08-27
Pinnacle Studio has that feature. Sadly, no linux version :(

---

