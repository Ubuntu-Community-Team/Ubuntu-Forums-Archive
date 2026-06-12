---
title: "Audacity won't play imported mp3"
date: 2008-12-04
forum: Ubuntu Studio
---

### Post by timchesonis on 2008-12-04
I need to make a mix of music using Audacity. Let me start by saying that I have researched the forums on this one.  I keep coming across threads where people say that they can't record audio, but I can't hear an imported mp3.  

I've even been to mediubuntu and installed everything they offered, but still, to no avail.  I can hear the music from RythmBox, but nothing from Audacity.  I can import the file, even "play" the file, but I get no sound.  Please advise, as I desperately have to create a project in short order.  Thanks!

SOLVED: I implemented "surfsunadam" suggestion regarding making everything ALSA, and now i can play mp3 files!  Cool beans!

---

### Post by surfsunadam on 2008-12-04
Unplug any external sound cards.
Go to preferences in audacity and make sure your playback is set to Alsa (default) . Then go to System (in ubuntu) - Preferences - sound and makes sure all of them are set to ALSA

---

### Post by djbushido on 2008-12-04
Also try converting to .wav or .ogg to see if these work - Audacity doesn't use medibuntu codecs, all of that is inline.

---

### Post by unoodles on 2008-12-04
If you do not have pulseaudio configured correctly, make sure jack is not running. After starting audacity you can kill jack by typing 'kill `pgrep jack`'.
If you do have pulseaudio configured. Simpy type 'padsp audacity'

---

### Post by Curt12 on 2009-08-08
hey, sorry to resurrect an old thread, but i searched and this thread seemed the most relevant.  i am having the same problem as the original poster, but none of the suggestions have worked.  same thing with .mp3 and .wav... it looks like it's playing, but it's not.  all the files i tested work fine in other programs.

thanks,
curt

---

