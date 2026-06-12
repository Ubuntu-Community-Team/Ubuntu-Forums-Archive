---
title: "Sound Problem Gazelle"
date: 2007-06-15
forum: System76 Support
---

### Post by DesiArnez6 on 2007-06-15
Having thought that me speakers were blown, it seems that atleast my left speaker has mysteriously revived itself, but ONLY for one file, and ONLY when headphones ARE plugged in??! But crytal clear, no distortion, but VERY low volume. (And no headphone sound), then when headphones are removed, teh left speaker also shuts off.

All other files CAN be heard with the headphones, but the left speaker stayes silent, and the right speaker makes scratchity distorted but barely audible sounds UNTIL headphones are plugged in, as if it weer blown, but I am not sure.

So basically I am Now sure that the laeft speaker atleast is fine, BUTonly for one file if headphones are plugged in, strange.

(As a side note, not sure if related, but the first problem I noticed only after the first 5 upgades (Firefox GIMP and some lib... files??) and the addition of XMMS from the repositories. The left speaker "resurrection" I noticed only after installing mplayer from terminal, and RealPLayer from the website "bin"file)

....UPDATE.. I just tried this mysterious file again, (Codec MPEG-1 video/audio on Ubuntu) (ffdsow Audio/ffdswho MPEG4 video/ and MPEG-l stream splitter) and results: without headphones plugged in, left speaker silent, right speaker distorted, with headphones plugged: now works fine but the "ubuntu startup drums contunuing to play in the background over and over, now eve with Totem closed, and now with everything closed, so now I must restart...

...OK, restart, try same file, new result, without headphones left speaker silent, right speaker distorted heavily, plug headphones in and ??? only right headphone works?? unless i pullit out just a little bit, then both headphone sides work perfectly Strange. ..... So now I test all my other files and ... Headphones work perfectly on both sides! , retry mysterious file, only right headphone works, until I pull the cord out a tiny bit, then both sides???

As another note, I realize that "dialtones" as in when you are dialing sound PERFECT without headphones from the right speaker (IT so happened the movie has a place where you can here dialtones and THAT is the ONLY thing that sounds perfect and ONLY from the right speaker, anything else is distorted. Very strange.

Any more strange speaker/headphone behavior and I'll be sure to let you know, if it changes its behavior again. Bad part is, I'm no longer getting the perfect low level sound from the left speaker when the headphones are plugged in, now its just silent again for all files. Hmm.

---

### Post by thomasaaron on 2007-06-15
Try running your system 76 driver and selecting the Restore option.
This should re-load Alsa. Let's see if that does any good.

Also, try turning your PCM down some. And set your little icon in the upper right to control the master. (If the PCM is too high, it might be causing problems.)

---

### Post by jkvelu on 2007-10-06
> **thomasaaron said:**
> Try running your system 76 driver and selecting the Restore option.
This should re-load Alsa. Let's see if that does any good.

Also, try turning your PCM down some. And set your little icon in the upper right to control the master. (If the PCM is too high, it might be causing problems.)

thanks a lot...

i am new to ubuntu...all these days... sound from speaker was fine.. all of sudden.. there was low volume...i try to play with sound control and nothing happened...

then i read this post.. and did changes in PCM and now i can heard the sound as hell :guitar:

thanks a lot... and also i set all the controls to ALSA in sound control panel..

---

