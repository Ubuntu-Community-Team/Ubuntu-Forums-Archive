---
title: "No sound except in xbmc"
date: 2012-07-15
forum: Ubuntu Studio
---

### Post by leo_m on 2012-07-15
I have two users configured on my computer.  For one of them, there is no sound.  The other one I only use for XBMC in fullscreen mode and XBMC plays the music just fine.

Ubuntu Studio 12.04.

---

### Post by Laiquendi on 2012-07-15
Does it happen with all types of music files, or maybe just mp3?
You may lack some codecs (which would be strange in Ubuntu Studio though), or drivers. Do you know if you have the codecs installed?

---

### Post by leo_m on 2012-07-15
What's interesting is there are no system sounds (though I could not find setting for that anywhere).  Applications like Virtual MIDI keyboard do not produce any sound either. 

That said, I did not have the Ubuntu restricted extras installed.  Installed this package, can hear mp3s now, Skype installed and found to work as well, but system sounds, MIDI keyboard above are still the same (no sound)...

Also, attempting to use Pulse Audio Mixer results in 'Fatal error: Could not connect to PulseAudio'

---

### Post by Laiquendi on 2012-07-15
[FONT=Arial][SIZE=2]Glad I could help a little bit at least :P

You may still lack some of the codecs. To install the most common type this into terminal:
[/SIZE][/FONT][FONT=Arial][SIZE=2]**```
 sudo apt-get install non-free-codecs libxine1-ffmpeg gxine mencoder totem-mozilla icedax tagtool easytag id3tool lame nautilus-script-audio-convert libmad0 mpg321 mpg123libjpeg-progs 
```**[/SIZE][/FONT][FONT=Arial][SIZE=2]
System sounds should be available through "Sound" in dash, also if you'll click on the sound/volume icon (near the timer).[/SIZE][/FONT]

---

