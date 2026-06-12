---
title: "[SOLVED] usb midi keyboard help with Jack control"
date: 2008-10-11
forum: Ubuntu Studio
---

### Post by wenbill on 2008-10-11
Hello, I am trying to get an Emu Xboard 49 keyboard to work in Ubuntu studio. I am new to Linux. I have started Jack control first. I opened zynaddsubfx. I opened the connect in jack control.When I used the midi tab, I just see system in  the left window. I think zynadsubfx was in the right window. when I selected system in the left window the right window changed to a system option also.
  If I choose the Alsa tab rather than midi the I see an option for emu 24 Xboard 49 on the left and some options on the right. one option is zynaddsubfx another is xboard 49.

 I get sound from the virtual keyboard through my speakers. But I am trying to get input from my new keyboard. Any help would be appreciated.

Edit: I found the problem, I was using the raw midi driver. I changed to seq and then my keyboard was recognized.

---

### Post by thorgal on 2008-10-11
do you have an ALSA tab ? I would use that one for MIDI connections. Chances are that you started jack without its internal MIDI handling, so it can only deal with audio. But the ALSA MIDI handling is fine, as long as the audio outputs are handled with jack. The ALSA tab in qjackctl has been introduced a long time ago for convenience because jack is not exactly done with its own MIDI implementation.

---

### Post by ivanhoe75 on 2008-10-16
> **thorgal said:**
> do you have an ALSA tab ? 
ALSA tab in zynaddsubfx or jack?(i have same problem)

---

### Post by thorgal on 2008-10-16
in qjackctl

---

### Post by ivanhoe75 on 2008-10-16
Fine, but jack does not work. It starts I can choose Alsa and connect some devises (I must use uart mpu 401 and destination prog - zynaddsubfx?) it connects but no result. I saw at this forum I must switch system sound off and delete pulse audio is it nesessary? after switching off all sound I do not hear any sound at all even in zynaddsubfx

---

### Post by thorgal on 2008-10-16
it's probably because jackd is not running.
When you start it, the audio device must be available. If it is handled by another sound server (pulseaudio, esd, artsd, or other audio layer of that kind), jackd will not be able to use the audio device.

You can probably turn off pulseaudio. You don't need to uninstall it. I don't know much about PA because I don't use it, but I know that if it is running, you can kill it from a terminal by typing 

pulseaudio -k

Then, make sure jack is well configured (setup window in qjackctl) :
- correct backend (either ALSA, OSS or Freebob / FFADO depending on which low level driver you are using with your sound card). Hopefully, it will be ALSA. To make sure, in a terminal, type :

lsmod | grep snd

If you get a lot of stuff like snd-whatever, then your card is driven by ALSA. If that's the case, jack must be configured to use its ALSA backend. Look into the qjackctl setup window, in the Interface section. You can choose between several devices. Pick something called hw: x
x being the ALSA device ID (in case you have 2 or more audio devices, it could be 0, 1, etc). If you only have one sound card, then hw: 0 is what you need.

After that, never mind the rest (realtime option, etc), that can be configured later. Use the default setting :
rate 44100
frames per period 1024
number of periods per buffer 2

nothing else, just default.

If jack does not run proper with this setting, despite the fact that your card is driven by an ALSA driver, it could be that you need some more tweaking. If it runs, and you can finally hear some sound, you are in business and can improve latency, etc by setting up your box for realtime audio operations. There are places in the forum where this is described.

---

