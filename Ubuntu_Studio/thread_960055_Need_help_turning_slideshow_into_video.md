---
title: "Need help turning slideshow into video"
date: 2008-10-27
forum: Ubuntu Studio
---

### Post by CC_Joe on 2008-10-27
Hi all,

So I have a slideshow I made with OpenOffice that I'd like to burn to a DVD.

At first I tried to use [www.authorstream.com](www.authorstream.com), which seemed like exactly what I needed. But when uploading my slideshow the website always timed out. So I decided to go the screencast route.

I am using recordmydesktop -- it's a pretty cool program. But I have a few problems with it. My presentation has sound and when I use this program the sound is quiet and tinny, even when I turn my volume way up. I think it's because it is using my external mic to record the sound that is coming from my speakers. I'd like to make it just record the digital sound, and turn off the external mic. I've been trying to adjust different mic/volume controls via GNOME, but so far the program always uses the external mic.

Can anyone steer me in the right direction?

EDIT: it says my device I'm using is a HDA NVidia (Alsa Mixer), but I also can select Conexant Cx20549 (Venice) (OSS mixer). But the Conexant only has a Volume bar and a Digital-1 bar, whereas the NVidia device has master/PCM/ext-mic/int-mic.

---

### Post by cotcot on 2008-10-27
In such a case I would use a video editor like blender, cinelerra or any other video editor with multiple tracks of which also sound tracks. Put the slides as pictures on the timeline, give them the time length you need and add sound on separate tracks. A video editor is more powerful in animating a slideshow than open office (impress). But this suggestion might be to late because you have done the work already in openoffice.

---

### Post by CC_Joe on 2008-10-27
Yeah, that might have been quicker in the long run.

What I ended up doing was using RecordMyDesktop to record the slideshow (this time minus sound) to get an .ogg file. Then I used mencoder to convert the ogg to avi like so:

```
mencoder nosound.ogg -ovc xvid -oac mp3lame -xvidencopts fixed_quant=2 -lameopts cbr:br=128:aq=0 -o nosound.avi
```

Now with a soundless .avi, I used avidemux to cut down the video to just the slideshow. I used mp3DirectCut (via WINE) to create the soundtrack to the movie. Luckily all I had to do was loop a mp3 twice and save it as a new file. Then avidemux let me add that new looped soundtrack back to the video.

End result, a slideshow movie with good sound! Now I'm using Devede to turn the .avi to a .iso, ready to burn to DVD.

Phew!

---

### Post by Lars Noodén on 2008-10-28
I'm not a flash fan, but would that work?


In OpenOffice.org: 
   File->Export->File Format->Macromedia Flash (SWF)

---

