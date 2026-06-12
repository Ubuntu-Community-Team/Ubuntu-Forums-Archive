---
title: "How to get video clips edited and produced to DVD"
date: 2009-01-18
forum: Ubuntu Studio
---

### Post by hannuh on 2009-01-18
Maybe somebody could point me to the right direction with basics of video editing.
This is where I am now:
I load video clips from my JVS Everio to my hard drive, and I can play the .MOD files with Totem. I have all gstreamer codecs installed, and Totem-MoviePlayer/Gstreamer plays these files which are MPEG2 with ACL video perfectly.
The only video editor that plays them right is Pitivi.
Kdenlive, Cinelerra, etc. do not seem to be able to use the right codecs.
Now, I would like to edit the clips, just trim them, I don't even care about transisitions or background sound tracks at this time.
I understand that I have to come up with some kind of file which I can then produce to a DVD in qdvdauthor.
There seem to be two choices in Pitivi, to "render" or "save as".
What should I do here, what kind of file am I supposed to produce. Ptivi 0.11.1 does not prompt any file formats. What is rendering? 
In other words, what does qdvdauthor need in order to have the contents for a video DVD?
Or, is there some better way to do this?
Thank you,
Hannu

---

### Post by jounionni on 2009-01-22
> **hannuh said:**
> Maybe somebody could point me to the right direction with basics of video editing.
This is where I am now:
I load video clips from my JVS Everio to my hard drive, and I can play the .MOD files with Totem. I have all gstreamer codecs installed, and Totem-MoviePlayer/Gstreamer plays these files which are MPEG2 with ACL video perfectly.
The only video editor that plays them right is Pitivi.
Kdenlive, Cinelerra, etc. do not seem to be able to use the right codecs.
Now, I would like to edit the clips, just trim them, I don't even care about transisitions or background sound tracks at this time.
I understand that I have to come up with some kind of file which I can then produce to a DVD in qdvdauthor.
There seem to be two choices in Pitivi, to "render" or "save as".
What should I do here, what kind of file am I supposed to produce. Ptivi 0.11.1 does not prompt any file formats. What is rendering? 
In other words, what does qdvdauthor need in order to have the contents for a video DVD?
Or, is there some better way to do this?
Thank you,
Hannu

Hei Hannu!
Install Tovid and use it for doing DVDs from your MPEG2s. Tovid is in my opinion a little easier to use than qdvdauthor for makeing DVDs. Both use dvdauthor and other libraries etc for that. Mayby the tutor for Tovid is more clear than for Qdvdauthor.

You find Tovid+its GUI in Synaptic or you have to go to Getdeb and find there.....

---

### Post by hannuh on 2009-01-28
> **jounionni said:**
> Hei Hannu!
Install Tovid and use it for doing DVDs from your MPEG2s. Tovid is in my opinion a little easier to use than qdvdauthor for makeing DVDs. Both use dvdauthor and other libraries etc for that. Mayby the tutor for Tovid is more clear than for Qdvdauthor.

You find Tovid+its GUI in Synaptic or you have to go to Getdeb and find there.....

Thank you Jouni, that did it.
I managed to get my video stuff going. I took your advice, installed Tovid since qdvdauthor was crashing all the time.
I have a lot to learn to get to the level where I was with Windows and the Cyberlink programs, but now I have a working start and don't have fire up Vista any more.
Here is a summary just in case somebody is stuck with the same issues:
- I download the .MOD files from my JVC Everio to the HD
- import the clips into Pitivi
- edit, whatever can be done in Pitivi
- render and save the rendered file as .mpeg
- start Tovid-GUI, create menu > add videos > video options (16:9 neeeded to be manually specified, quality)
- third option in Tovid, "author and burn DVD"
Thank you - Kiitos!
Hannu

---

### Post by browndog on 2009-01-28
> **hannuh said:**
> Thank you Jouni, that did it.
I managed to get my video stuff going. I took your advice, installed Tovid since qdvdauthor was crashing all the time.
I have a lot to learn to get to the level where I was with Windows and the Cyberlink programs, but now I have a working start and don't have fire up Vista any more.
Here is a summary just in case somebody is stuck with the same issues:
- I download the .MOD files from my JVC Everio to the HD
- import the clips into Pitivi
- edit, whatever can be done in Pitivi
- render and save the rendered file as .mpeg
- start Tovid-GUI, create menu > add videos > video options (16:9 neeeded to be manually specified, quality)
- third option in Tovid, "author and burn DVD"
Thank you - Kiitos!
Hannu

Check out Kino if you get a chance.

---

