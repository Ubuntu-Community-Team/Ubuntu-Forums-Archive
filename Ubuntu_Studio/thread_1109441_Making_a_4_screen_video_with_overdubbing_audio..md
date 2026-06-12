---
title: "Making a 4 screen video with overdubbing audio."
date: 2009-03-28
forum: Ubuntu Studio
---

### Post by CodyT07 on 2009-03-28
Hello ubuntu users (sorry if wrong forum), I am trying an attempt at making my first video, which will feature me playing guitar. 
Basically, here is what I have

I have a camera ( Optimus MPEG 4 Video camera) that records in an ASF format when I copy it from camera to computer a
It can also double as a webcam though I haven't found the right drivers for it

An M-audio Fast Track  with a studio guitar mic



I want to make 4 videos and put them in a single video with split screen 2 times (a total of 4 screens) and be able to put audio from my Fast Track on it instead of using my Cams Mic. 

So to simplifiy things. Record 4 movies and put them all together in a 4 screen video. Add my audio (recorded on audacity most likely) over it. (Sorta cheap I know but don't tell anyone)

Anyone care to lead me to the right programs on how to do this?

I am using Ubuntu Studio 8.10, 64 bit with the generic kernel instead of the real time one. Cant find the correct nvidia drivers for it. 

Much appreciated 
:guitar:

---

### Post by cotcot on 2009-03-29
I am thinking about following paths. 

Blender VSE : using the tranform effect (scale and position) to put each track in a corner and then overlay them.

Cinelerra : using camera and projector (look in the good Cinelerra manual on their site)

Kdenlive : maybe with the picture-in-picture tool (not sure if it can handle 4 picture-in-pictures).

However I have not tried it myself with 4 tracks (only with 2 in blender).

---

### Post by Stochastic on 2009-03-29
Just to follow up on what cotcot said, here's a quick 'get to know blender video editing' screen cast:
[Part 1]("http://blog.rfquerin.org/2009/01/26/how-i-edit-videos-using-blender-maybe-part-one/")
[Part 2]("http://blog.rfquerin.org/2009/02/14/really-basic-blender-video-editing-part-2/")

I don't think they cover that particular effect, but they start you with the basics (blender is a bit overwhelming for new users).

---

### Post by wrathkeg on 2009-05-11
> **cotcot said:**
> I am thinking about following paths. 

Cinelerra : using camera and projector (look in the good Cinelerra manual on their site)



Cinelerra can do this.  Load the video (and audio tracks) with "append in new tracks" selected as the insertion strategy (from the "load files... window).  By right clicking on the tracks in time line and then selecting move up/move down you can change which track shows up in the compositor window.  Change the position of each track in the compositor window by clicking and dragging, or shift-click and drag to change the size.  Once done, go file > render and save the file in a format which suits.
at least, this is how I do this.
wk

---

