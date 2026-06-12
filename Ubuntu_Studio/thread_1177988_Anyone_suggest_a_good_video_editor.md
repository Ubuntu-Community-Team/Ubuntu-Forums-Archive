---
title: "Anyone suggest a good video editor?"
date: 2009-06-04
forum: Ubuntu Studio
---

### Post by MetroidJunkie2008 on 2009-06-04
Pitivi isn't doing it for me. At the very least, I want a video editor that can mute sound and replace it with music, which Pitivi doesn't seem to be capable of doing. I'd prefer a video editor with functionality similar to WMM but not too complex to figure out. At the very least, those functions I mentioned.

---

### Post by igorzwx on 2009-06-04
Try mencoder:
[http://wiki.quakeworld.nu/Mencoder_howto#3._Using_audio](http://wiki.quakeworld.nu/Mencoder_howto#3._Using_audio)

This is how to replace audio:

**In this next example, mencoder adds an audio track from a .wav file and encodes it to mp3.**  mencoder input.avi -o output.avi -ovc copy -oac mp3lame -audiofile soundtrack.wav

**It is also possible to add an audio stream which is already encoded: ** 
 mencoder input.avi -o output.avi -ovc copy -oac copy -audiofile soundtrack.mp3
[http://wiki.quakeworld.nu/Mencoder_howto](http://wiki.quakeworld.nu/Mencoder_howto)
[http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide](http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide)

See also: 
Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready 
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

---

### Post by MetroidJunkie2008 on 2009-06-04
> **igorzwx said:**
> Try mencoder:
[http://wiki.quakeworld.nu/Mencoder_howto#3._Using_audio](http://wiki.quakeworld.nu/Mencoder_howto#3._Using_audio)

This is how to replace audio:

**In this next example, mencoder adds an audio track from a .wav file and encodes it to mp3.**  mencoder input.avi -o output.avi -ovc copy -oac mp3lame -audiofile soundtrack.wav

**It is also possible to add an audio stream which is already encoded: ** 
 mencoder input.avi -o output.avi -ovc copy -oac copy -audiofile soundtrack.mp3
[http://wiki.quakeworld.nu/Mencoder_howto](http://wiki.quakeworld.nu/Mencoder_howto)
[http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide](http://en.gentoo-wiki.com/wiki/HOWTO_Mencoder_Introduction_Guide)

See also: 
Howto make Ubuntu 9.04 (Jaunty Jackalope) Multimedia Ready 
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

I was kind of hoping for a gui to do this? I was asking for a video editor, not just an audio swap. I only plan to replace audio for a portion of the video.

---

### Post by igorzwx on 2009-06-04
sudo apt-get install avidemux

but the quality might be reduced during editing :)

Howto is here:
[https://wiki.ubuntu.com/ScreencastTeam/KnowledgeBase](https://wiki.ubuntu.com/ScreencastTeam/KnowledgeBase)

Try mencoder and ffmpeg ;)

---

