---
title: "Video editing-Cutting out the black bands(theora)"
date: 2006-07-04
forum: The Cafe
---

### Post by WaterWalker on 2006-07-04
Is there an easy way to cut out the black bands on the top&bottom of some of my video's.
Note: The video´s are encoded in Theora, But none of the Video editors seem to be able to open it.

---

### Post by matthinckley on 2006-07-04
what do you mean cut out the black bands?  are you wanting to stretch the image to fit a 4:3 screen? or do pan & scan?  

those black bands are because the video is in 'letterbox' format, which is the way the director of the movie intended for you to see it.. when there are no black bands, what usually has occured is somebody has zoomed into the 'letterbox' video so that the picture you see fills your entire 4:3 screen, but you are actually losing some of the picture when this happens...

---

### Post by WaterWalker on 2006-07-04
[QUOTE=matthinckley]what do you mean cut out the black bands?  are you wanting to stretch the image to fit a 4:3 screen? or do pan & scan?  

those black bands are because the video is in 'letterbox' format, which is the way the director of the movie intended for you to see it.. when there are no black bands, what usually has occured is somebody has zoomed into the 'letterbox' video so that the picture you see fills your entire 4:3 screen, but you are actually losing some of the picture when this happens...[/QUOTE]
I know there are black bands when you see a movie full-screen.
But if you watch them in a small window you shouldn't see any black bands(which is the case with me).

---

### Post by matthinckley on 2006-07-04
oh you mean the black bands are actually encoded into the video, instead of the video just 'being' letterbox, you get a 4:3 window all the time with black bands...  hmm.. I've seen this before but I don't know how to fix it..  sorry...

---

### Post by wmcbrine on 2006-07-04
In MPlayer or MEncoder, you can use the "crop" video filter. E.g.:

mplayer -vf crop=720:360 filename

for a typical 16:9 movie encoded to 4:3 NTSC letterbox (720:480).

---

