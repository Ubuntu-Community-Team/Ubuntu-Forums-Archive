---
title: "mp4 to mpeg convert ?"
date: 2007-07-17
forum: The Cafe
---

### Post by silent1643 on 2007-07-17
is there any program out there to convert mp4 to mpeg or avi?
windows or linux, every one i have found you gota pay for it, blows

---

### Post by Steveway on 2007-07-17
Try out mencoder.
It's a command-line app but the manpage is very detailed, so if you read the manpage you'll know the command.

---

### Post by artships on 2007-07-18
Mencoder doesn't recognize an MP4 file (an iTunes video).

---

### Post by stmiller on 2007-07-18
Try the VLC Wizard. File>Wizard

---

### Post by ixus_123 on 2007-07-18
mp4 is just a container file, as is avi

the actual video inside these containers could be divx, h264 or any of a number of video codecs.  The same goes for the sound file in the container. It could be mp3, aac, ogg etc.

use VLC to view the file, then get info from the menu - from there you can think about converting and for your converting needs mencoder is the way to go.

get it from the mplayer website where you'll also find detailed docs on how to use it

---

### Post by fjf on 2007-07-19
I know this one! I know this one! I know this one!
Just install DeVeDe.  Easy to use, will create mpeg files or a DVD ISO file with menus from *.avi files.  Works great.  In my athlon64 3500 it takes about 6 hours to create a 4.5GB DVD.

---

### Post by artships on 2007-07-20
> **ixus_123 said:**
> mp4 is just a container file, as is avi
use VLC to view the file
Fine advice, but taking it results in:

bash > vlc 01.mp4
VLC media player 0.8.6 Janus
[00000300] mp4 private error: drms_init(priv) failed (could not get system key)
[00000307] main decoder error: no suitable decoder module for fourcc `drmi'.
VLC probably does not support this sound or video format.
[00000280] main playlist: stopping playback

Any idea how to get around that?

Oh, and using the wizard...

VLC media player 0.8.6 Janus
[00000300] mp4 private error: drms_init(priv) failed (could not get system key)
[00000307] main decoder error: no suitable decoder module for fourcc `drmi'.
VLC probably does not support this sound or video format.
[00000360] mux_ps private: Open
[00000364] mp4 private error: drms_init(priv) failed (could not get system key)
[00000353] stream_out_transcode private error: cannot find decoder
[00000353] stream_out_transcode private error: cannot create video chain
[00000370] main packetizer error: cannot create packetizer output (drmi)
[00000360] mux_ps private: Close
[00000280] main playlist: nothing to play

Further research makes me think that VLC may work, but only if run on the same computer that downloaded the video.   It's a DRM thing.

---

### Post by LostAndFound on 2008-03-21
Hi,

You could also try the program Avidemux. It worked for me in converting a Camera video to mpg from mp4. The mp4 version was cut off (cropped to top right quarter) in any Linux player I used (mplayer VLC, Xine etc) and on a friend's Vista laptop.  It did play correctly in Quicktime on a Mac. After trying the mencode command-line options (it would be quicker /more worthwhile spending 7 yrs studying for a Phd in Computing!) and DVeDe etc, I finally opened it in Avidemux and saved it again as mpg, and it both opened and converted the movie correctly and un-cropped. Also worked very fast.

So Avidemux may be a solution!

---

### Post by arkangel on 2009-01-27
What about the other way around 

I have an avi I want to packet as mp4

---

### Post by geoken on 2009-01-27
> **artships said:**
> Fine advice, but taking it results in:


Are you trying to work with DRM'd content?

---

### Post by super breadfish on 2009-01-27
A lot of MP4 files use odd AAC variants for audio which won't work with video programs from the standard repos. Compile your own or try Medibuntu.

---

### Post by duds2008 on 2009-02-06
irivertor?

---

### Post by hessiess on 2009-02-06
FFMpeg.

---

### Post by jethro10 on 2009-02-06
I find AviDemux solves 99% of all my problems like this.

---

### Post by jelabarre on 2012-12-30
> **LostAndFound said:**
> Hi,

You could also try the program Avidemux. It worked for me in converting a Camera video to mpg from mp4.
 
But we need to convert *from* MP4 *to* MPEG-PS.  Avidemux seems to only work the other way (it certainly didn't like the MP4 files I gave it)

---

### Post by Sef on 2012-12-30
necromancing, so locked.

---

