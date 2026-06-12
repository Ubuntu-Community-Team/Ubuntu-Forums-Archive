---
title: "Digitally remaster video tapes, 35  mm movies, etc."
date: 2009-08-13
forum: Ubuntu Studio
---

### Post by jonathonblake on 2009-08-13
All:

I've got some ancient videos, and even older movies to upgrade/convert to DVD. (These are all home movies, so there are no copyright issues involved in recreating them.)

Getting them to DVD is trivial. However, the audio quality is really  bad. (For starters, the audio volume wanders up and down, with no rhyme or reason.) Some of the video images show burns --- from when the projector was halted during a discussion of something on a frame ---  and other undesirable artefacts. (I realize this involves editing/creating every frame. Alfred Hitchock used to examine his movies image frame by image frame, to ensure that each individual  image was artistically perfect. I see no reason not to emulate that behaviour.)

My thinking is to rip the audio track into a single file, then manually edit/recreate it, so that the sound level is constant. Along the way I'd be adding commentary to it.   

Ideally, I'll end up with at least 5.1 surround sound, 1080i video quality.

Question:

What would be the most appropriate tools to use for this project?
(My preference is for FLOSS, but non-FLOSS tools that can run as _native_ application on Linux are acceptable. (If it runs under Wine, it is not running as a native application.)

Specifically:
* Best tool to convert the video files to individual images;
* Best tool to convert the individual images back to video;
* Best tools to edit the audio;
* Best tools to "upgrade" the audio to 5.1 surround sound;
* Best tool to merge the audio back into the video;

For those wondering why  I'm not asking for a tool to edit the individual images, the answer is because that is obvious --- GIMP & ImageMagick.

###

I realize that for most Hollywood DVDs, "digital remastering" is nothing more than dumping aged tape to DVD, and converting single track mono to two track mono. That result is worse than my home movies and is not what I consider to be "digital remastering".  I will concede that what I'm wanting to do is more along the lines of "digital reconstruction", than "digital remastering".

jonathon

---

### Post by jaqian on 2009-09-29
THe best tool I know for editing audio is Audacity. You can get it on getdeb.org should be in the repos as well.

---

### Post by kayosiii on 2009-09-29
The two tools on linux which are capable of audio cleanup are Audacity and Gnome Wave Cleaner GWC.

The video will be more problematic -- when doing a digital conversion you generally get the worst of both worlds.

There are quite a few tools that will convert a video file to a sequence of frames (I would typically use Cinelerra for this - Though I am sure somebody here can tell you the magically invocations to make ffmpeg do this for you -- or the inverse)

Cinelerra, Blender or ffmpeg would be good choices to do the inverse conversion.

I am not aware of any good tools for doing 5.1 sound (could be a licensing issue) Ardour I think does ambisonics... so purhaps ask there.

I think that DVD authoring programs will let you merge audio back into your video programs otherwise there are the usual suspects.

I assume you could probably use Cinepaint for the cleanup operations...

What ever you decide to do - you are up for a *LOT* of work... 
good luck

---

### Post by jonathonblake on 2009-09-29
> **kayosiii said:**
> The two tools on linux which are capable of audio cleanup are Audacity and Gnome Wave Cleaner GWC.

Audicity looked too obvious.  I thought I had to be missing something.

> when doing a digital conversion you generally get the worst of both worlds.

Which I've since discovered.

> somebody here can tell you the magically invocations to make ffmpeg do this for you -- or the inverse)

I got ffmpeg to convert one of the videos to individual images/frames. Well, it would have worked, had I not run out of disk space. :(
I thought a 1 TB drive would be big enough, but it wasn't.

> Cinelerra, Blender or ffmpeg would be good choices to do the inverse conversion.

I didn't realize Cinelerra could both convert to individual frames, and then put the individual frames back together. :)

I'm going to have to learn how to use Blender, for some animation effects I'd like to add. (Specifically, There is a five second sequence of a house being flooded --- over the roof.I want to add a "For Sale By Owner" sign floating in the water, with the phone number of the real estate agency that the owner of that property runs.)

> What ever you decide to do - you are up for a *LOT* of work... 

So I've discovered.

jonathon

---

