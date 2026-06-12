---
title: "Rendering to file sequence in Kdenlive-is there a script for this?"
date: 2010-05-09
forum: Ubuntu Studio
---

### Post by FrostBlue on 2010-05-09
Hi ,
I have tried to render a png file sequence by making the following rendering profile

f=image2 vcodec=png size=%widthx%height aspect=%dar

but it spits out on one png file while the rendering window progress bar shows it going through the whole footage.
So is there some variable I am not putting in to make it render a sequence of pngs incrementally.
The format section of the render profile maker window accepts 4 characters, so maybe I am missing a variable like @ # or % or something.
Also I saw that kdenlive accepts some kind of scripts,is it possible to make a simple script that makes render jobs for each frame with above mentioned render profile.
Sorry I am new to ffmpeg and MLT and am not a programmer.

Thanks in advance.

FrostBlue.

---

### Post by FrostBlue on 2010-05-13
Has been solved...

[http://www.kdenlive.org/forum/renering-file-sequence-there-script](http://www.kdenlive.org/forum/renering-file-sequence-there-script)

---

