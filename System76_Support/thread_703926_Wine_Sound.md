---
title: "Wine Sound"
date: 2008-02-21
forum: System76 Support
---

### Post by Gonzell on 2008-02-21
Has anyone had any luck getting sound to work with wine with any of the System76 laptops? More specifically with Steam Games (Half-life 2, Counter-Strike Source, etc.) I'm able to run these games fine...but I haven't any sound. I already have the OSS driver selected in the winecfg and I'm told that ALSA does not work with Counter-Strike correctly. Either one I enable, when I click the "Test Sound" button, it says: "Audio Test Failed".

Suggestions? (I'm using a Pangolin)
Thanks

---

### Post by thomasaaron on 2008-02-22
This from the **winecfg** section of...
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

It may be useful.

> If you experience stuttering, bad sound or no sound what so ever, then you must try a few things in winecfg. Just type winecfg in a terminal, press enter, and the wine configuration application window should appear and you should go to the audio tab.

For most people OSS will work better than ALSA, so you should make sure that only OSS is ticked. But for some ALSA works better, so try that as a second solution, make sure you only have one ticked at a time.

Also, refer to the Voice chat section for information on getting multiple audio streams working with OSS and ALSA (more than one program using audio at once). It will wave you grief should you ever want to listen to music and chat on Ventrilo or Teamspeak while playing, and similar.

You may also try ticking Driver Emulation or setting the Hardware Acceleration dropdown to Emulation. Remove it again if it does not help. 

---

### Post by jmorth on 2008-02-23
This is what I did.

First you'll need the drivers for your sound card. I had a disc that came with my mobo that had everything.

I loaded up the disc. I looked at the contents until I found the folder that had my sound card drivers in it. I explored that folder looking for a setup program. It was in a second folder after the first. I right clicked on it and opened it with WINE. It installed the files just like it would when being used on a Windbox.

I now have sound in my games under WINE.

It worked for me and I hope it works for you.

---

### Post by Gonzell on 2008-02-23
Oooh...I never thought about doing that.

I actually got the sound working by following one of the steps in the WoW tutorial. I did an apt-get for aoss and I use that when launching Steam and everything works pretty good now. I also have the ALSA driver selected in the winecfg.

Thanks

---

### Post by thomasaaron on 2008-02-25
Well, I'm glad the WoW tutorial worked. But I'm definitely glad to learn about downloading drivers via wine. Thanks for sharing that.

---

