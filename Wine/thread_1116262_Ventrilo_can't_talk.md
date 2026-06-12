---
title: "Ventrilo: can't talk"
date: 2009-04-04
forum: Wine
---

### Post by robinsonbond007j on 2009-04-04
As you can see in the title, I'm having troubles talking in ventrilo. I tried looking around the internet and I didn't find anything on just people having troubles with a keybind/talking in vent. Now I'm very new to linux so I need a in-depth explanation if anybody knows how to fix it. And I have direct sound enabled in ventrilo. Not sure if their is something I need to do with the computer or not. But again any help would be wonderful. I just don't want to have to go back to windows just to talk in ventrilo. And I don't want to buy crossover.

---

### Post by robinsonbond007j on 2009-04-05
Well after looking around for the PTT scripts I found something but I can't find a pyvent.py anywhere on my computer. Anything would help getting vent to work properly would be nice. 

Here is the script I found that isn't working for me.
[http://ubuntuforums.org/showthread.php?t=1010743&highlight=pyvent](http://ubuntuforums.org/showthread.php?t=1010743&highlight=pyvent)

---

### Post by robinsonbond007j on 2009-04-05
Well I can do everything in vent but have people hear me now. I've tried about everything I found in the forums. But still can't get anybody to hear what I'm saying. And yes my hotkey is working and is be rendered in vent. I read about PulseAudio maybe be the problem but I don't have it highlighted under my sound option. Any help would be great.

---

### Post by FrozenFox on 2009-04-05
Do any other recording programs (Note: I wouldn't suggest using audacity; even with my system working properly with sound everywhere else, I can't get it to record) *not* being run in wine work properly? 

If not, check your sound in the terminal: alsamixer -c 0, and make sure your mic volume (toggle between input/output sections with f2/f3 and mute/unmute with m - 00 in the volume meter box means unmuted). Note that sometimes some weird things need to be enabled for your mic to actually pick up sound under here. Like mine can't work without 'amic' in the OUTPUT at max, and most of the 'aux' and 'analog' things ticked in the INPUT, as well as the expected mic and mic boost.

If that doesn't help and you still can't record outside of ventrilo, there's several possibilities. Pulseaudio is screwing it up, alsa is screwing it up, or something. You can temporarily disable pulseaudio I think via sudo /etc/init.d/pulseaudio stop or something of the sort. Naturally, to turn it back on again would be 'start'.

The reason this is a frequent problem is because many cards seem to lack a hardware mixer to handle multiple sound sources, and the software one doesn't seem to always work properly. One of pulseaudio's goals is to make it work a little more often by stopping programs that hog the sound card from doing so by forcing them to go through the pulse sound layer. Sometimes it works, sometimes it doesnt. Sometimes it unfortunately manages to make matters worse, where it would work without pulse. In any case, try that out.

If you get this stuff working outside of wine properly, run winecfg and try setting the audio tab to use ALSA instead of OSS, if it doesn't already.

If all that doesn't help, and recording works outside of vent/wine, try disabling directinput on vent, reload it, and try again.

If all -that- doesn't help, and recording works outside of vent/wine, you might look into how to use 'padsp' or install&use 'aoss' with wine set to use OSS in winecfg.

Unfortunately, this is a complicated problem that could be caused by all sorts of things.


Note that there is also a supposed 3rd party ventrilo client in the works called Spux, however it doesn't work yet as far as I am aware, as it only semi-recently started.

---

### Post by robinsonbond007j on 2009-04-05
I tried all of that and nothing worked for some reason :(

---

