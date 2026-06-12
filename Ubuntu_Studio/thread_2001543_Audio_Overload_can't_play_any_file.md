---
title: "Audio Overload can't play any file"
date: 2012-06-11
forum: Ubuntu Studio
---

### Post by HarryUP on 2012-06-11
I'm trying to make music covers of some sega genesis games.
So I wanted a program that can play .vgm files and that can individually activate/mute soundchannels.
I got Audio Overload, but it doesn't play any file: .nsf,.spc,.vgm...
According to this [http://ubuntuforums.org/showthread.php?p=11390596]("http://ubuntuforums.org/showthread.php?p=11390596")
it seems that it is an error in detecting the audio device. I tried that solution but didn't work on my Ubuntu Studio 12.04 installation.
I can play those different soundfile formats in Audacious but I can't mute channels, perhaps there's a plugin for that? I couldn't find any. Suggestions?

---

### Post by CrocoDuck on 2012-06-14
Hi. I never used these formats, but I found some software you may try:
 
[http://atariarea.krap.pl/stymulator/](http://atariarea.krap.pl/stymulator/) 
[http://code.google.com/p/qmmp/](http://code.google.com/p/qmmp/)

They should be avaible on software center.

I found this too, it looks fit all you needings:

[http://www.bannister.org/software/ao.htm](http://www.bannister.org/software/ao.htm)

you just have to download and extract the archive. You can also follow this page:

[http://www.chipamp.org/](http://www.chipamp.org/)

If your Audio Overload doesn't work (like mine...) try to execute it from a terminal:

```

cd /path of the extracted directory
./ao
```

end repost the output.

---

### Post by HarryUP on 2012-06-14
stymulator and qmmp can play some of the formats but none of them give me individual mute/unmute channels.
Thanks for suggesting chipamp, I had to install winamp via winetricks. (select classic skin, it crashes when selecting modern skins) then I can go to plugin options and mute the specific channels.
I would try that on the terminal when I get home and post the results.
EDIT:
This is what I get in the terminal.

/dev/dsp: No such file or directory

ERROR: unable to open soundcard.  Aborting.

---

### Post by CrocoDuck on 2012-06-15
Is exactly the same error it gives to me. Basically, Audio Overload needs OSS ([http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)). You can install it (some program still require it) but I don't reccomend to install it, because all the newest and coolest audio software uses alsa and jack (the last time I installed OSS it ruined my audio setup, so I purged it). Glad that chipamp worked with you!

---

