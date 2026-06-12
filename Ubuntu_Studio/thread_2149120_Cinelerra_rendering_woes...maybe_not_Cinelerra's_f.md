---
title: "Cinelerra rendering woes...maybe not Cinelerra's fault?"
date: 2013-05-27
forum: Ubuntu Studio
---

### Post by swedstal on 2013-05-27
First, let me say this: I love Cinelerra. I have found it to be not only a powerful piece of software, but intuitive as well. Being that it is the first video editor I have used, I was very concerned about the learning curve. Terms like "Keyframe" and "Mask" meant nothing to me and I could not conceptualize the Camera/Projector relationship. Through the help of some wonderful tutorials I've been able to create some very impressive (to me at least) projects.

...but I have a problem.

I cannot figure out the rendering process. 

I really only have two goals:
1. Render video in 1280x720 (I'm not concerned with what format, nor even audio at this point).
2. Re-load that video back into Cinellera for further editing

I'll go over what I have tried and the problems I have encountered.

[B].MPG

[/B]This is the format I have tried most extensively. My rendering screen looks like this:

[IMG]http://i.imgur.com/uly9eWH.png[/IMG]

I've tried some different pipes to render in this format. The following one is the only one that has ever worked for me.

```
[COLOR=#333333][FONT=courier new]ffmpeg -f yuv4mpegpipe -i - -y -target ntsc-dvd %[/FONT][/COLOR]
```

This one works occasionally, but never perfectly. Though my project is set up in 1280x720 format, it only renders in 720x480. Adding the "-hq" to the pipe causes it not to render at all. Whenever it fails, I get this message:

[IMG]http://i.imgur.com/51IHkOk.png?1[/IMG]

Oddly enough, I've also noticed that the destination folder has an effect as to whether it successfully renders or not. I can see no reason why this should happen, further adding to my confusion. Additionally, when I do get it to render, loading it back into Cinellera often gives me this error message:

[IMG]http://i.imgur.com/iQqKGhm.png?2[/IMG]

After all of this I decided to try a new format.

[B].MOV


[/B]Not much to say here. When I try to render using "Quicktime for Linux" nothing happens. I doesn't freeze or crash, per se, but the rendering progress stays stuck at 0% even when left for hours. No luck.
[B]
.OGG

[/B]I actually thought I had something here. It was the first format that I was able to export in 1280x720 format. Were I doing a single render, this would be fine and dandy. Unfortunately, I am often wanting to reload the video back into the project to do further editing (requirement #2 from above). When I bring the .ogg file back into Cinelerra I get this error:

[IMG]http://i.imgur.com/eHoZpGk.png[/IMG]

This pops up any time the video is played or the cursor is moved

**Versions**
OS: Ubuntu Studio 10.04
Cinelerra: 2.1CV
FFMPEG: This one I'm actually not sure about. Here's what I get from the terminal:

```
FFmpeg version SVN-r0.5.9-4:0.5.9
```

I think that means 0.5.9, but I'm not sure what that 4 is doing in there.

**Possible Solutions**
After seeing what version of ffmpeg I have, I think that it may be my problem rather than Cinelerra. I see that ffmpeg Version 1.2.1 has been released. Maybe it's a rookie error, but I am not sure how to update to that version to see if that's the problem. In my Synaptic Package Manager it shows the latest version as "4:0.5.9". Do I need the latest version of Ubuntu Studio to upgrade to this version of ffmpeg? I'm really clueless about some of this stuff. I basically got the 10.04 version running stably a few years ago and decided not to touch it.

I apologize for the verbose nature of this post, but I like to show that I have at least tried a few things before begging for help. Thanks in advance for any thoughts!

---

### Post by jejeman on 2013-05-28
Option "-target ntsc-dvd" is DVD. So, no HD. Loose the option.
For intermediate file it's better to have keyframes on every frame (like DV has), It is easyer for editing, and go easy on compression. Try exporting like that. I don't have Cinelera installed so I can't go in details.
Don't touch ffmpeg.

---

