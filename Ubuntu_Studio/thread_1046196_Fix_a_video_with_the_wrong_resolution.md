---
title: "Fix a video with the wrong resolution"
date: 2009-01-21
forum: Ubuntu Studio
---

### Post by amar on 2009-01-21
Hi folk,

I am having problems with a video that was created with adobe premier pro CS3 -- the expensive one

The video has been exported, is massive (1.5 Gb for 6 mins) and has the wrong resolution.

The source video was 1280x1024, and the exported video is the same resolution, except that in the editing process, black edges were added, making a pillar-box effect making the video widescreen, then squashed the whole thing back together.

concidering the amount of time wasted with premier already I was hopping that it could be fixed on ubuntu

Any ideas or do I have to bite the bullet and reencode the thing again (and waste another 2-3 hours)

thanks

---

### Post by amauk on 2009-01-21
you can put it in a Matroska container (.mkv)
Matroska has an aspect ratio flag, and players will resize videos on the fly according to the flag

I've done this on a few camcorder videos, where the source material has long been erased
It's more CPU intensive to play (the player is resizing on-the-fly) and the quality does suffer

---

### Post by jethro10 on 2009-01-21
You can re-size and re-shap with avidemux.
It takes a little bit to learn but is ideal for this type of thing.

I use it for my videos off my camera, they are really good quality but not widescreen, so I crop a little bit, stretch/re-size a little bit and then add black borders left and right for the rest. Works great. Then it plays great on the widescreen TV.

I can't see any other options to re-coding, but 6 minutes shouldn't take long.

---

### Post by amar on 2009-01-21
> **jethro10 said:**
> You can re-size and re-shap with avidemux.
It takes a little bit to learn but is ideal for this type of thing.


Exactly what I was looking for.

It had a crop function which removed the black borders adobe had added, (and automatically sized them too)

then I was able to stretch it back to the 4:3 automatically as well.

Currently running it now, the file appears to me much smaller and allot quicker. Got to wonder why adobe couldn't have just worked in the first place.

Thanks

---

### Post by patchin_house on 2009-01-24
Matroska turned out to be the right approach in my case, because the source material was stretched horizontally to begin with. When I first did a transcode to XviD, I couldn't fix this. The MKV Files Creator, however, *does* allow you to set the ratio to what you want it to be (in my case 4:3), and *voila!* I got the proper dimensions this time (and in my case, no visible deterioration). 

Of course, I should mention that the video was destined for YouTube, so... ;-)

Well, at least the dimensions are correct now.

Philip David
2009.01.24

---

