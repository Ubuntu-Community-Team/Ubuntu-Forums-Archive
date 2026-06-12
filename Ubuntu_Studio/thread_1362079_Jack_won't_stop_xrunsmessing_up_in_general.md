---
title: "Jack won't stop xruns/messing up in general"
date: 2009-12-22
forum: Ubuntu Studio
---

### Post by emu42 on 2009-12-22
When I try to start up Jack under my sound card (usually hw:1) through qjackctl, it gives a lot of xruns and then freezes. I usually have to log out to stop Jack because "killall qjackctl" doesn't work. Same thing with jackd. 

I tried messing around with every single option, and the only one that did some difference was changing "duplex" to "capture only" (which made Jack immediately crash) or to "playback only" (which did not crash, but then I can't record).

But the weird thing is, it occasionally does work, and I don't know why it does or doesn't. I use a USB MIDI keyboard, which is usually hw:2. Oftentimes, the computer won't even boot with it plugged in. I just tried booting about 5 times with it plugged in without success, then after unplugging it, it works. But sometimes it's the other way around.

So I really have absolutely no idea what's happening, my computer seems to be fine (SB soundcard, 2gb ram). I'd really appreciate help on this!

---

### Post by AutoStatic on 2009-12-23
Hello emu42, what soundcard are you using (**lspci | grep -i audio** and **aplay -l**)? And what are your current JACK settings? Could you post a screenshot of the Settings window of QjackCtl?

---

### Post by emu42 on 2009-12-23
output of "lspci | grep -i audio":

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
02:03.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster



output of "aplay -l":

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



I posted these outputs, then tried to open qJack, which didn't open but rather froze my computer and I had to restart. So the device numbers may be different in this screenshot.

[IMG]http://img687.imageshack.us/img687/7249/jackckckckck.png[/IMG]

---

### Post by AutoStatic on 2009-12-23
Thanks! So both the Creative and the Ati soundcards have issues? I would set the Periods/Buffer setting to 2 instead of 3. 3 works out well for USB1 sound devices but not for onboard cards. At least, that's what I've read here and there and experienced myself.

---

### Post by emu42 on 2009-12-23
The ATI hasn't worked in quite some time, that's why I got the Creative to replace it. I set the periods/buffer to 2, but it still crashes. I think I'll try restarting a few times to see if that helps.

Edit: I rebooted, and everything works: Jack (no xruns), the MIDI keyboard, and all the applications. Thanks!

Edit2: It crashed again, lol. Actually got a lot of xruns when I hit the play button in Ardour, which slowed Jack down dramatically until it crashed altogether. No idea.

Edit3: Rebooted again, and Jack xrun'd immediately as I opened up Ardour. Perhaps Ardour is using up too many resources?

---

### Post by emu42 on 2009-12-23
Actually, ignore this topic, I'll be switching to Windows (at least for now). Seems like I won't be having these constant problems. But if you do find a fix, feel free to post it here for others, but I won't be checking this. Thanks for all your help!

---

### Post by M4st0d0n on 2010-01-12
Had a similar problem.

Solved it by uninstalling Pusleaudio.

Adding pulseaudio -k in the starter script of jack didn't do the trick because it would reload after each kill.

---

### Post by AutoStatic on 2010-01-12
You don't need to uninstall Pulseaudio. If you create a *client.conf* file in your *$HOME/.pulse/* directory with the following line in it you can kill Pulseaudio so that it won't respawn:
```
autospawn = no
```

---

### Post by flatko on 2010-11-25
OK, guys, I think I found the solution. Sometimes the very easy solutions come after trying almost impossible things.
I had this problem forever, until I tried to run Jack in 96 kHz, full duplex! It is the only frequency that works perfectly with CA0106 chips, and the sound quality is fantastic! Any other frequency gives A LOT of xruns and damaged input signals on full duplex.
So, that is - 96 kHz and all other settings are defaults. 
Hope that helps you all :)

---

