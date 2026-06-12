---
title: "Importing iPad-recorded h264 into any ubuntu studio video editors"
date: 2016-09-27
forum: Ubuntu Studio
---

### Post by pjmnoble2 on 2016-09-27
Incredibly frustrated . . I recorded a series of clips on my iPad (h264, 1080p, 29.9fps). I transferred these to my ubuntu studio computer (which I use as a music studio . . .it is outstanding at that). I then import the clips into a video editor . . and I tried all of them, kdenlive, openshot, LiVes, cinelerra. on the first attempt to quickly check a clip the software hangs - in all of them. I tried using the smallest clip I had (20Mb), I tried transcoding them all to lower quality h264 using the kdenlive transcoder. Nothing works . . . having been so pleased  with the music studio, I am astounded at how incapable these programs are.

All the clips play fine (beautifully) in VLC

The machine is a three core AMD 2.1GHz motherboard, ATI graphics

I used to edit video on a pentium 2 machine with a cheap and cheerful matrox card 20 years ago and it worked a thousand times better than any of these . . .While the video files are now 4x the resolution, I am amazed at how a standard file format can kill these.

I wondered if they are using a common library that is causing the problem and that is not used by VLC . . .(the ubuntu default video player does not play them either)

Any suggestions really welcome. I need to cut up loads of clips and align them to a sound track - iMovie on my ipad can probably do this but is a fiddly interface.

Cheers

PJ

---

### Post by pjmnoble2 on 2016-09-28
SOLVED . . . .

Problem which meant previewing any clip in kdenlive, openshot, cinelerra, lives and flowblade caused the software to hang was . . . the sound system. Switch off jack and kdenlive and openshot work fine. None of the programs gave an error or warning of any kind.

Now editing with kdenlive . . .magic.:D
Just gotta do without Jack during these sessions (though on researching, aloop-daemon might help with this)

---

