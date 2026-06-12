---
title: "Software/Hardware combo for recording Live Presentations"
date: 2009-05-12
forum: Ubuntu Studio
---

### Post by CNLiberal on 2009-05-12
A division in my company spends a great deal of their time giving trainings.  These training encompass MS Powerpoint slideshows, video (be it on the computer or DVDs from a DVD player), remote controlled camera (with the possibility of more) and several microphones.  They want to take these different sources and record them all and then put together a DVD/Video file with fades between different video sources (computer screen/cameras/DVD).  We are spending a lot of money on an installer to give us equipment that I'm not convinced is really built for what we need.  He's giving us a MediaPointe DMR.  It's based on Windows and gives us "low resources" errors all the time.  It sucks.  Every time the group wants to start a recording, we have to reboot the damn thing.  The DMR also records in WMV format.  Yuck.
Anyway, I'm just doing some research to see if there's something Linux can do for us.  I want the ability to record from several different sources in a format that's open and can easily be mixed with other formats using free software.  I also want the ability to make a DVD ISO file and have it played in standard NTSC DVD players.  One other thing that might be nice, is the ability to stream the current video/audio sources being recorded out onto our local network.

One of the reasons I want to go with Linux is that it's free, I can add as much storage to the backend that I want and I can use some pretty standard hardware I think.

Now like I said, I'd like to be able to record everything separately with a "time stamp" if you will.  Some way to sync the audio with the video.  Then I can mix everything together the way I want.  If there's a better way to do this, I'd love to hear it.  Any and all options will be explored.  Thanks for your help!

Jim

---

### Post by thorgal on 2009-05-12
maybe not exactly what you are asking but a MythTV based system could do the streaming no sweat.
It is streaming MPEG2 video(and embedded audio) so you could even burn stuff to DVD.

MythTV comes with a lot of useful plugins, is designed as a backend / frontend system types, can accept many different inputs (analog TV, S-Video source, whatever produces mpeg2 frames as far as I can tell). It time-stamps every recording, you can edit some from a mythfrontend, archive them, etc.

The server can serve mulitple frontends, there's a mythweb plugin that can run on an apache server (same as myth-backend machine), and you can do a lot from this web-interface.

Sure it is more TV program oriented but there's no reason why it would not work with other video sources (frame grabbers, etc).

[www.mythtv.org](www.mythtv.org)

just an idea, might not cut it in the end but who knows ?

---

### Post by CNLiberal on 2009-05-12
thorgal:

Thanks for the post.  I'm actually running MythTV at home so I'm familiar with the software.  I thought about doing a MythTV setup but I think I could accomplish the same thing with just doing a:

cat /dev/video0 >> file.mpg

I just am not aware of video editing available in Linux/Ubuntu.  I guess I could do a script that will record from all sources.  But I want a way to do it simultaneously.  Once I have the recordings, I don't know how to put them all together with transitions etc.  I want high quality video from each, so a Haupage PVR card for the different video feeds would be great.  I'm not sure how to capture the video from the Windows computer though (not to mention the audio from it as well).  Then stripping the audio and video from each input and mixing it all together.  Any ideas?

Jim

---

### Post by CNLiberal on 2009-05-12
I don't know anything about video editing.  I don't know what format would be best for capturing the video.  I don't know how well the Mac of Linux software would deal with that capture.  My goal is to just put some hardware together that captures all the pieces (video cameras, mics, video/audio from Windows computer).  Then I can hand those files over to someone with experience with video editing.

---

### Post by thorgal on 2009-05-12
sounds like you want to really edit the video pieces together ...
mmm, that's not really my area ... some ppl here are doing a lot of work with video editing though, I would be surprised if no one showed up with a tip.

---

### Post by markbuntu on 2009-05-12
gimp can do a lot of the graphics stuff but it can get very complicated

cinerella and kdenlive are two popular video editors for linux, you should check them out. If you want a full featured audio workstation for mixing and editing and syncing audio you should check out ardour, it is better than many expensive windows DAWs. 

All of these things will take some time to learn and the learning curve can be pretty steep but there is very little they cannot do that commercial products do.

---

### Post by lukeiamyourfather on 2009-05-12
There's no single package of software that will handle all of your needs in this situation. Sounds more like the work for a multimedia specialist or an entire department dedicated just to the media aspects. 

I'd break things down into smaller tasks then work from there. For example use something like Audacity to record audio narrative for PowerPoint presentations and export images from OpenOffice or PowerPoint. Use the audio and images to create a video of the presentation in a video editor (there are plenty for Linux).

This isn't possible in Linux really (at least with a lossless codec) but you could use something like Camtasia to record a PowerPoint with audio narration then use the video to create a DVD or other training material. That way the timing of the slides, audio, and compilation of the video are all one step by capturing.

One way or the other I'd strongly advise creating dedicated media for the training videos, don't just record a regular training presentation and put it into a video (those always suck, its harder than it looks). People learn differently in person and from a screen and compiling media for an in person presentation is different from compiling media for a training video. Removing the need to record a live presentation makes the whole process much more simple and manageable. Cheers!

---

