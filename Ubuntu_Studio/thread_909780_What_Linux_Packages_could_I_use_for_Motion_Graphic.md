---
title: "What Linux Packages could I use for Motion Graphics?"
date: 2008-09-03
forum: Ubuntu Studio
---

### Post by ewangr on 2008-09-03
Am currently producing a series of fanimations (Example below):
[http://revver.com/video/1149612/affiliate/219725/my-lovely-ghost-episode-2-making-a-new-life/](http://revver.com/video/1149612/affiliate/219725/my-lovely-ghost-episode-2-making-a-new-life/)

Under Windows, I use Cepstral TTS for the voices, VideoSpin to put the graphics I create using Paint.net into the video, and Audacity for the music editing.

I know Audacity is multiplatform, and I can probably use GiMP for the pictures. But what are the Linux equivalents for Cepstral and Videospin?

TIA!

---

### Post by werries on 2008-09-03
[http://ubuntuguide.org/wiki/Alternatives](http://ubuntuguide.org/wiki/Alternatives)

---

### Post by ewangr on 2008-09-03
Well, since I didn't say I had looked there first, I guess I should have expected that suggestion :-)

However, I didn't see anything in the wiki for Text to Speech, and the video packages listed there don't seem to let you use JPG/PNGs with a separate soundtrack. Though it's possible I wasn't looking for things the way the wiki has them, or missed a feature or two...

---

### Post by Unterseeboot_234 on 2008-09-04
For real graphics in a real animation, I use a commercial product -- Unix Version -- called Anime Studio Pro. [_**AnimeStudio Pro.**_]("http://my.smithmicro.com/win/animepro/index.html") The 32-bit version of the software can lip-synch the audio with a bone-based graphic. AnimeStudio outputs wonderful Flash movies.

My choice for a video editor is Cinelerra because I can manipulate 64 tracks of audio or video, but I have my own personal methods to export-import-merge from graphics production into video presentation. For instance, with AnimeStudio I elect to export .png stills and use other software such as ffmpeg to merge those stills into DV-RAW or QuickTime movie clips.

I have a keen wish for Text-to-Speech and I have observed such software is a work in progress. The java efforts over on SourceForge show the most promise.

---

### Post by ewangr on 2008-09-04
So the short answer is that I can't do it with what's currently out there - or at least not nearly as easily? With VideoSpin I can bring in the picture, and adjust the length of the time the image is shown to fit the length of the audio clip by matching them on their tracks. Sounds like I'd have to time the clips and use FFMpeg to process them in Cinelerra, and then redo if I'm much off. Ouch...

---

### Post by Unterseeboot_234 on 2008-09-04
KdenLive (in the Add/Remove Synaptic) imports stills and exports a video using ffmpeg as a backend. 

I value time when I do video. I found I had a learning curve whereby I wasted weeks and weeks making discoveries. The choices available on other platforms might actually save you time.

Video on Linux is a personal preference of several tools. Cinelerra is my final edit because the tracks are visual timelines for audio and for video. Because Cinelerra is runs in 64-bit, rendering or transfering files are not so time-intesive. Because I run Ubuntu, I get for-real namespace in memory with no crashes. That is, I can surf the web while I render a video, or edit audio while I ray-trace a 3D scene.

---

### Post by wajiguqu0223 on 2008-09-04
Mr Fawkner says Bejeweled transfixed him because it takes "two worthy game-design principles and distils them kill into their most elementary modify"."On one [maple story mesos ](http://www.ugamegold.com/c_Maple-Story-Mesos/)accumulation, you jazz pattern-matching, which our brains seem hard-wired to revel, and on the added script you jazz an environs of haphazard possibility -

---

