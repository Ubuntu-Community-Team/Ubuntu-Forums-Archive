---
title: "Sound only works for sudo after suspend (System 76 laptop)"
date: 2016-11-23
forum: System76 Support
---

### Post by opus1 on 2016-11-23
Ever since upgrading to Xenial on my System 76 laptop, the sound occasionally stops working after resuming from suspend.  In these cases, if I start anything with sudo (e.g., sudo audacious), the sound will work, but starting anything without sudo won't (e.g., audacious started in the terminal gives the errors "ALSA lib pulse.c:243:(pulse_connect) PulseAudio: Unable to connect: Protocol error" and "ERROR util.cc:140 [audgui_simple_message]: ALSA error: snd_pcm_open failed: Connection refused.')

Logging out and then back in doesn't fix the error and I tried to do an "alsa force-restart", which didn't do anything either. The only way to get the sound to come back for normal users is reboot.

Prior to Xenial, the up time on the laptop would be months and I would suspend/resume at least once a day with no sound problems.  Now I am rebooting every 4 or 5 days.

I would like to fix the problem, but failing that, I would like to know how to restart alsa for a normal user without having to reboot.

---

### Post by ajgreeny on 2016-11-23
Try ```
sudo alsa force-reload
``` as suggested in the page at [http://askubuntu.com/questions/303686/no-sound-after-startup-have-to-alsa-force-reload](http://askubuntu.com/questions/303686/no-sound-after-startup-have-to-alsa-force-reload)

---

### Post by a-emma on 2016-11-23
Hi Opus1,
My name is Emma and I work at System76.[COLOR=#000000][FONT=Arial] First, let's make sure the hardware is being recognized with these commands:  
aplay -l
[COLOR=#000000][FONT=Arial]lspci -v | grep -A6 Audio

[/FONT][/COLOR] Deleting the config files, reinstalling the sound related packages, and making alsa force reload solves problems like this many times. Try running the following commands and see if that fixes your system:  

rm -r ~/.config/pulse ~/.config/pavucontrol.ini 

sudo apt install --reinstall alsa-base alsa-utils pulseaudio linux-sound-base libasound2  

pulseaudio --kill 

sudo alsa force-reload 

pulseaudio --start 

Any luck?
[/FONT][/COLOR]

---

### Post by opus1 on 2017-02-10
Wow, many apologies for not following up.  I found a workaround but forgot to post it here.  Basically, I found in another forum that if I open a terminal and issue a ```
pulseaudio -k
``` followed by a ```
pulseaudio -v
``` then the sound works again and I don't have to reboot.  I wish I could prevent it from happening altogether, but it now happens so seldom that I don't worry about it.  (although, that begs another question... why did it happen so often after upgrade, but now not very often? maybe something was updated...)

---

