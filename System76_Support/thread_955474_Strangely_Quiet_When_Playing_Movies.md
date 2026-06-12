---
title: "Strangely Quiet When Playing Movies"
date: 2008-10-22
forum: System76 Support
---

### Post by christophermluna on 2008-10-22
Well, the audio on my Pangolin (panp4n running 64bit Ubuntu) is working exceptionally well, now, except for one strange thing which I have not been able to figure out.

Whenever I play DVDs, it is terribly quiet.  I have the Totem Movie Player and the gxine installed on the laptop.  Gxine is quieter than Totem, but both are so quiet that it is almost impossible to hear dialog.

In Totem, under Edit > Preferences, and under the Audio tab I have the Audio Output type set to Stereo.

In gxine, under Audio > Controls I have the volume set to 100 and I have played with different settings on the Amplifier, even turning it up to max, and still the voices are little more than a whisper.

Also, the audio works great when playing a CD, or playing music or videos from other sources (like YouTube, Pandora, etc); and the issue is not with a single DVD, as I have tested several different DVDs.

It's not the biggest issue for now, because I can plug the laptop's audio-out into a surround sound setup I have for my desktop, and it will amplify the volume enough to be quite pleasant, but at some point I'll be getting rid of that setup, and I'd like to see if I can get this fixed before then.

Thanks in advance for taking a look.

---

### Post by thomasaaron on 2008-10-22
Yes, totem-xine is pretty quiet on my GazV5 too. I'm not sure about straight totem.

This problem has been mentioned in a number of posts, and I've never been able to figure it out. It seems to be inherent to a codec.

Thanks for bringing it up again, though. I'll work some more on fixing it. It would be nice to have that working.

---

### Post by glacialfury on 2008-10-23
Sometimes alsamixer has a slider set down low, even though the one in your systemtray is turned up all the way.  I had a problem with a movie being quiet (both in VLC and in Totem), and all my sliders were up.  Then I loaded alsamixer and saw the master slider was turned down.

This doesn't sound like your problem, but it never hurts to check.  Open a console and type "alsamixer" and take a look.

---

### Post by christophermluna on 2008-10-23
Thanks, but I already tried that.  I retried it at your suggestion, because the new driver seems to have given me more options than I had last time, but still no luck.  None of the new bars seem to control the movie volume.

---

### Post by Brickrat on 2008-10-26
I also have a new Pangolin and after quite a bit of work, finally got it to play movies, and the sound level is way too low to hear.   I checked an audio CD and it is better but certainly not loud.  I checked the alsamixer and it the master is set to max.   Headphone sound adequate, but I don't have to worry about going deaf either. 

Hopefully, someone will have some more things to try.

---

### Post by thomasaaron on 2008-10-27
Brickrat, are you using totem-xine?

---

### Post by Brickrat on 2008-10-27
Thomasaron: 

Yes, I changed it on Sunday to:   Totem Movie Player using xine-lib version 1.1.11.1 and GNOME.

Brickrat

---

