---
title: "Listening to Music while running a Program through Wine"
date: 2010-01-26
forum: Wine
---

### Post by Dweomer on 2010-01-26
I'm not sure if this is normal or not, but I can find very little mention of it which surprised me. Am I supposed to have to run a program in Wine for listening to music as well as whatever other program I am also running (E.G. A video game), or is this something specific on my end? At first I assumed it was par for the course but being unable to find any information on the subject has lead me to suspect it might be uncommon to have this issue.

---

### Post by beastrace91 on 2010-01-26
The answer is no. You can listen to music through anything while running an application through Wine (personally I've used both Movie Player and Firefox while Wine gaming).

What Wine/Ubuntu versions are you using if this is not working for you.

Regards,
~Jeff

---

### Post by Jguy on 2010-01-26
I just had this issue on my machine. 

I would start up Banshee or Rhythmbox and start listening to music, or I would be watching any movie and run something in wine (not even a game, Notepad or winecfg would do it), and all sound quit. I would have to restart whatever was playing sound to get the thing to work again. Sound would also not work in wine at all.

I think this has something to do with ALSA vs. PulseAudio? If I remember right, Ubuntu made the switch in 9.10. What I did to solve this was to switch in winecfg the Audio Driver to 'EsounD' and Apply -> OK. This seemed to solve the issue as I could listen to music or watch a movie in conjunction with using a wine application.

Thanks,

---

### Post by Dweomer on 2010-01-26
> **beastrace91 said:**
> The answer is no. You can listen to music through anything while running an application through Wine (personally I've used both Movie Player and Firefox while Wine gaming).

What Wine/Ubuntu versions are you using if this is not working for you.

Regards,
~Jeff

Karmic Koala, and I've used both the Beta and Stable versions of Wine and had the problem on both. I can get music/audio fine from the programs Wine runs, and I can get music/audio from regular programs like Banshee. This could very well be a hardware issue, then. I built this computer, and it was my first one, and I never got the sound card working right so it's using just the integrated chip on the mobo. I also had sound issues with a couple of games from the software center but oddly enough no sound trouble with anything through Wine as long as I'm not also trying to play music or other media with audio components at the same time.

---

### Post by Dweomer on 2010-01-26
> **Jguy said:**
> I just had this issue on my machine. 

I would start up Banshee or Rhythmbox and start listening to music, or I would be watching any movie and run something in wine (not even a game, Notepad or winecfg would do it), and all sound quit. I would have to restart whatever was playing sound to get the thing to work again. Sound would also not work in wine at all.

I think this has something to do with ALSA vs. PulseAudio? If I remember right, Ubuntu made the switch in 9.10. What I did to solve this was to switch in winecfg the Audio Driver to 'EsounD' and Apply -> OK. This seemed to solve the issue as I could listen to music or watch a movie in conjunction with using a wine application.

Thanks,


That worked! Thank you! I've been working on this problem off and on for the better part of a week now.

---

