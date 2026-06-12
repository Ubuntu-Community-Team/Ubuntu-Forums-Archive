---
title: "Control Pulse Audio volume from command line"
date: 2009-12-18
forum: Server Platforms
---

### Post by junapp on 2009-12-18
Installed a minimal karmic setup, no gui, for task of playing some music through some speakers.

after some of the initial enhancements (vim-full, getting a proper bashrc file going) I installed mplayer, and the restricted formats. 

Using a command like 'mplayer song.mp3' it appears that the song is being played but no sound is coming out. I recalled setting up and reading that volume for some is muted upon installation.

I tried, alsamixer (after installing alsa-utils) but that throws some errors "function snd_ctl_open failed for default: No such file or directory"

I tried 
lspci | grep audio 
and see my Intel AC'97 Audio Controller (onboard)

Then tried
aplay -l
and got "device_list:223: no soundcards found...

Thinking this might be a pulseaudio vs alsa issue I installed pulseaudio-utils and gave 'pavucontrol' and 'pavumeter' figuring one of those might display a volume setting option.

in my /etc/modprobe.d/alsa-base.conf
I've got 
options snd-hda-intel
(which I believe to be correct).

I stumbled upon:
[http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller](http://unixmen.com/linux-tutorials/documentations-a-howto/524-ac97-audio-controller)
and gave that a go, which did produce sound when running the osstest, but still nothing from mplayer.

Anything further to try?

---

### Post by junapp on 2009-12-18
I should mention that I used the * and / keys to get mplayer's volume to 100%, but still no sound.

---

### Post by junapp on 2009-12-18
not an ideal solution, but I edited 
/etc/mplayer/mplayer.conf

and changed the line
ao=pulse,alsa,sdl:aalib
to
ao=oss,pulse,alsa,sdl:aalib

which seems to have produced sound at least.

---

### Post by glethro on 2010-01-19
I have a similar problem, are you using 9.10 server?

---

