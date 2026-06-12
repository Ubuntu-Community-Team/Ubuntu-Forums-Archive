---
title: "ubuntu studio 16.04 Videos not playing after update"
date: 2016-12-25
forum: Ubuntu Studio
---

### Post by boombox2 on 2016-12-25
Hi there,
after I updated the system when prompted, videos on the internet will not play anymore. If i go to Youtube for example I can see the video loading on the progress bar and i can see the first frame, but the video does not progress. if i manually move the slider forward, it will show the frame at that time but sill doesn't play. the same problem i have playing files from my computer using Videos, but if I use VLC it works fine. I cannot find any related issues searching on the web, but before update everything was fine. I tried to reinstall flash plugin and did a system upgrade to 16.10, but still no luck. I have the same problem on firefox and chromium.
thanks

---

### Post by marseille2 on 2016-12-26
It might not be flash... Sometimes it's related to audio. (It happens to me too when I forget to turn something on).

If you basically are using UbuntuStudio out-of-the-box ... first check to see what pulseaudio (PA) is doing.

Make sure pulseaudio grabs the right sound card. This is important if you have more than one audio device (which includes video cards with HDMI, since PA sometimes grabs that card first (makes it the default audio card). The easy no-brainer way to do this (and switch sound cards and mics _if you use pulseaudio)_ is to install **pasystray**. ***See this [post]("https://ubuntuforums.org/showthread.php?t=2345894")***.

You can also check to see which audio devices are loaded from your terminal by typing:

```
$ cat /proc/asound/cards
```

---

### Post by kilo-kilo-delta8 on 2016-12-26
I just had an issue with Ubuntu Mate updating to 16.04 and the screen going black.  Turns out the AMD video driver(s) weren't being supported, thus affecting me.
I have since returned to US.  I have heard there is now a fix for the issue in the UM forums but am not 100% sure.
Nonetheless, I am petrified to update US to 16.04.  I think I will hold off for awhile.

---

### Post by kilo-kilo-delta8 on 2016-12-26
> **kilo-kilo-delta8 said:**
> I just had an issue with Ubuntu Mate updating to 16.04 and the screen going black.  Turns out the AMD video driver(s) weren't being supported, thus affecting me.
I have since returned to US.  I have heard there is now a fix for the issue in the UM forums but am not 100% sure.
Nonetheless, I am petrified to update US to 16.04.  I think I will hold off for awhile.


OOPS!  My bad, you said VIDEO, not the entire screen.  Disregard.....

---

### Post by boombox2 on 2016-12-27
Hi, thanks for the help, today I switched the computer on and it worked... go figure! Hopefully it will not happen again, but I've installed Pasytray, I'll check it out....Should i change the title to Solved?

---

### Post by boombox2 on 2016-12-27
Now, the problems seems to be related to Jackctl.
basically, when I switch on the computer, Jack starts automatically, only for some reason I have 2 sinks and 2 sources, I don't know exactly why. so what I usually do straight away I stop and start it again, and that gives me one sink and one source. Today I didn't do that, and videos on youtube worked. But when I stopped Qjack and started it again, videos stop playing, just froze. If I stop Jack, the video resumes. the strange thing is that I didn't mess with any of Qjack settings, I only updated system. Anybody knows what's going on?
here is out put from ~$ cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xcfdf8000 irq 25

---

### Post by marseille2 on 2016-12-28
I don't use PA these days, so I can't remember exactly which sinks initially show up... but* don't kill your pulseaudio-module-jack-sink *(or source). 

Jackd and pulseaudio won't talk to each other without the modules loaded. So if you leave Jackd on and kill the PA modules ... you won't be able surf the web and hear audio (which freezes youtube videos at the first frame).

Jackd by itself can't surf the web and hear sound without those PA modules. So assuming that you have **pulseaudio-module-jack** installed ... go to the command line and try reloading the modules (rebooting might work too, but if PA is being flaky ... maybe not).

```

$ pactl load-module module-jack-sink
$ pactl load-module module-jack-source

```

Also see this [thread]("https://ubuntuforums.org/showthread.php?t=2261067&highlight=pulseaudio+modules") for more about pacmd .... There is a way to make sure those sinks stay loaded.

---

