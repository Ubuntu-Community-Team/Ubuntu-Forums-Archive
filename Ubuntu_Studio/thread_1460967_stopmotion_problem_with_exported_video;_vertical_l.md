---
title: "stopmotion: problem with exported video; vertical lines"
date: 2010-04-23
forum: Ubuntu Studio
---

### Post by 2oucan on 2010-04-23
Using Stopmotion in Ubuntu Studio 9.10

I imported a .mp4 animation video to KINO, edited it, chopped it up into scenes and exported each scene as .png files. In some of the scenes I then edited some frames in Gimp and saved them as .png. I also created new scenes from scratch with .png files I created in GIMP.

I then created a sequence of scenes in Stopmotion and imported the relevant .png frames into each scene. Each scene plays perfectly in Stopmotion's playback facility but when I export to .mp4 **the scenes in which I didn't edit any of the frames play perfectly** but in scenes where I edited the frames or in scenes where I added completely new frames I get no colour and close spaced vertical lines (like watching very bad reception on a 405 line television on its side - except the image is the right way up - older readers will understand......). This doesn't affect all the frames that I have edited, only some.:confused:

Any ideas? Its a bit difficult Googling "stopmotion" as I get so many generic hits for animation in general.

Thankyou

---

### Post by LuridCinema on 2010-04-23
You can use ffmpeg to render the .png files to an output
Open a terminal in the same folder as the sequentially numbered images and insert
```
ffmpeg -f image2 -i %04d.png -r 06 -sameq output.mp4
```The above will render 4 digit, numbered .png files to a .mp4
The -r 06 is the number of images per second, so for 12 frames per second... -r 12
be sure and have the images sized for the desired output and you should be good to go.

THEN do the editing on the resultant .mp4 file would be my suggestion


Might help

---

### Post by gnarly_buttons on 2010-06-17
How did you get Stopmotion to export to mp4?  I can't even get that to work.

---

