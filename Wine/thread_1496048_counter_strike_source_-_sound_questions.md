---
title: "counter strike source - sound questions"
date: 2010-05-28
forum: Wine
---

### Post by Schui on 2010-05-28
Hello,

I am quite a Linux newbie, so please bare with me. I have managed to get counter strike source to play very well, even with voice chat (I can hear other people).

The only reason I got voice to work was to disable pulseaudio:
sudo pkill pulseaudio
However, this is very annoying to type in to terminal every time I wish to play. Also it sucks because I can't listen to anything else while playing, or it messes up my game.

I've searched around and found nothing similar to my problem.

If there could be a way to automatically disable pulseaudio whenever I launch the game, how would I do this?

Also, any way I could get my mic to work? It doesn't work in any app including the game. 

I am using the following code for the Steam launcher:
env WINEPREFIX="/home/sky/.wine" wine "C:\Program Files\Steam\Steam.exe" -applaunch 240 -startwindowed -width 1024 -height 768 +map_background none -dxlevel 80 -heapsize 512000 -vsync

I have Ubuntu 9.10 and wine 1.0.1

Thanks in advance for any help! Sorry if this post is in the wrong place!

---

### Post by Strevin on 2010-05-28
Go to your Wine Config and go to sounds and put on Full Emulation. You may have to switch between OSS and ALSA to get it to work. Also put the window emulation with the Graphic tab as well and put it in a window smaller than your full screen. I had the same problem with Starcraft hopefully this does the same for you.

As for your mic. The system may have muted itself. Just go into you sound and unmute the mic and you should be good to go. Had the same problem with Skype.

---

### Post by Schui on 2010-05-28
I tried it, no luck sadly. I set it to "full", and tried "emulation", and I also clicked the button to "emulate driver". Nothing worked without typing the command:

sudo pkill pulseaudio

Now it's acting funny to where when I try to exit the game (or when it crashes) it just puts me at the Ubuntu login screen. I don't even USE the login screen! Very odd. Also sound is rarely working, like 1 time out of 10, and then if I'm lucky I can join a server and everything is fine until it crashes or my FPS drops to about 10. This usually happens after about 5 minutes play time.

I'm not sure what you meant about the graphics thing. Also, my mic isn't working. I don't really care as long as my game works fine!

I'm completely lost for what to do.. this is totally out of my ball park.


edit: I tried the virtual desktop and it seems to have eliminated the lag / crashing to login error. It still seems to "crash" like it would otherwise but it's on the virtual server so it's ok. Now to get sound working!

---

### Post by asdfoo on 2010-05-29
You should upgrade to the latest testing release of Wine which is wine-1.2-rc2.

Wine 1.0.1 is about 1.2 years old which is a very long time.  There are numerous updates and fixes since then.

---

### Post by Schui on 2010-05-29
> **asdfoo said:**
> You should upgrade to the latest testing release of Wine which is wine-1.2-rc2.

Wine 1.0.1 is about 1.2 years old which is a very long time.  There are numerous updates and fixes since then.

Wow I had no idea I was using such an old install! I must have made some mistake.

I updated wine to the version you recommended. However, I'm still having to kill pulseaudio for the game to work properly. Something funny is happening, though. It seems as if my keyboard does not work in the game unless pulseaudio is enabled. And then after it's enabled, the sound goes away and the game crashes soon after. The sound is also very "static" and distorted when it's working.

Is there a workaround for the pulseaudio issue?

Thank you guys very much for your help, I really appreciate it.

---

