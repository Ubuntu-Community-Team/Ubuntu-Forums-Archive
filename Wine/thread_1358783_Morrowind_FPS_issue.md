---
title: "Morrowind FPS issue"
date: 2009-12-18
forum: Wine
---

### Post by Gosujii-sama on 2009-12-18
Yea probably going to say download the fps cleanup utility. ive looked at it and it wont help this issue. While running MW i get a fps issue in the sense of the game pausing like so
1sec fine no issue
0.1-0.2 sec freeze
1sec fine no issue
0.1-0.2 sec freeze
this continues throughout. i would say its a graphic issue but its not graphic runs fine and my system and hardware are all uptodate and more than enough to handle it. i remember before running it fine with this hardware before i upgraded from 8.04 to 9.10 karmic but since i reinstalled the system i dont have my settings that i did to create a smooth fps on morrowind. if someone could remind me what i might have missed would be great.

---

### Post by Capt. Blackwood on 2009-12-20
I have had this issue myself and i can tell you...it's not video it's sound. ALSA/Pulseaudio have latency issues with wine. Your best bet is to completely replace ALSA/Pulseaudio with OSS. I've done this and i know it works. My frame rate shot up quickly. It's a huge sound lag...the graphics are good.

---

### Post by beastrace91 on 2009-12-20
Are you suffering from [this bug](http://bugs.winehq.org/show_bug.cgi?id=14186) perhaps?

Regards,
~Jeff

---

