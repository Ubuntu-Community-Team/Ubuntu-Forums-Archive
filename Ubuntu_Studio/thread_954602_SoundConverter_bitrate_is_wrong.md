---
title: "SoundConverter bitrate is wrong"
date: 2008-10-21
forum: Ubuntu Studio
---

### Post by timandjulz on 2008-10-21
I am converting m4a files to mp3 using SoundConverter.  My preferences are set to use MP3 with "Variable Bit Rate", quality is set to "Very High" which should be 256kbps.

Per VLC, the input m4a file is:
```
bitrate 1411kb/s, sample rate 44100, codec mp4a.
```
And the output file is:
```
bitrate 48kb/s, sample rate 44100hz, codec mpga.
```

I double checked and mp3s I originally recorded in vbr show the 256kbps bit rate in vlc.

So the bitrate SoundConverter generated is way lower than what I had configured.  Have I got something configured wrong?

Thanks in advance,
Tim

---

### Post by timandjulz on 2008-10-21
bump

---

### Post by timandjulz on 2008-10-21
Last bump.  Anyone know what it will take to get SoundConverter to convert to vbr mp3 correctly?

Thanks
Tim

---

### Post by eye208 on 2008-10-22
Add ID3 tags. There is no way to tell the average bitrate of an MP3 file except by analyzing the file from beginning to end which takes time. If you add song duration info in ID3 tags, the player can at least guess the average bitrate by looking at the file size.

---

### Post by methodmarvel on 2009-03-15
I don't think that's what the OP means - I've experienced the same issue with files showing ~156kbps when I set it to VBR~256kbps

They should be at least >200 on the whole

---

### Post by sovesky on 2009-07-04
I've got exactly the same problem and I suspect it's a gstreamer LAME plugin bug.

---

### Post by igorzwx on 2009-07-04
Have you tried ffmpeg or mencoder?

On terminal:

man ffmpeg

     CLI Magic: Video conversion with mencoder 

[http://www.linux.com/archive/feature/121385](http://www.linux.com/archive/feature/121385)

---

### Post by pt123 on 2009-07-04
same problem here tried different settings for quality - insane high, to very high the filesizes outputed are the same. Mp3 players are reporting 160kbs CBR than 256 or 320 vbr it should

useless application

you are better of using Audacity

But that requires you to have lame installed

[https://help.ubuntu.com/community/Audacity](https://help.ubuntu.com/community/Audacity)

---

### Post by sovesky on 2009-07-10
Thanks for the link pt123, the thing is that audacity is much bigger and complex for such a minor task.

---

### Post by Hated On Mostly on 2009-07-15
Supposedly the bug is now fixed in version 1.4.4. I haven't tested it.

[http://soundconverter.berlios.de/](http://soundconverter.berlios.de/)
[http://developer.berlios.de/bugs/?func=detailbug&bug_id=15950&group_id=3213](http://developer.berlios.de/bugs/?func=detailbug&bug_id=15950&group_id=3213)

> # Force vbr-max-bitrate to 320 when using mp3+vbr, since gstreamer now defaults to 160.
(thanks psychoman, fix #15950)

No DEB package for this version out there yet.

---

### Post by Hated On Mostly on 2009-08-10
DEB package available now.

[http://packages.ubuntu.com/karmic/soundconverter](http://packages.ubuntu.com/karmic/soundconverter)

[http://packages.ubuntu.com/karmic/all/soundconverter/download](http://packages.ubuntu.com/karmic/all/soundconverter/download)

Did a couple of quick tests and the bitrate bug seems to be fixed.

---

### Post by pt123 on 2009-08-10
do these packages work on Jaunty

---

### Post by Hated On Mostly on 2009-08-10
> **pt123 said:**
> do these packages work on Jaunty

Worked for me on 8.10 (Intrepid Ibex). Will probably work perfectly fine on Jaunty.

---

### Post by sovesky on 2010-01-24
I'm using ubuntu 9.10 with SoundConverter 1.44 and still have that bug.

---

### Post by rduke15 on 2010-01-25
I also had that bug in Jaunty. It is supposed to be fixed in SoundConverter 1.4.4 ( [http://developer.berlios.de/bugs/?func=detailbug&bug_id=15950&group_id=3213](http://developer.berlios.de/bugs/?func=detailbug&bug_id=15950&group_id=3213) ).

But anyway, I switched to Sound**K**onverter (the KDE equivalent) which works fine and has more options.

---

