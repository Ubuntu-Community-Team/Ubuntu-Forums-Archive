---
title: "Midi sounds distorted (but shouldn't be)"
date: 2009-02-17
forum: Ubuntu Studio
---

### Post by angelsneverdie on 2009-02-17
Hello, this is a follow up of [this post]("http://ubuntuforums.org/showthread.php?t=1068913")but the OS has changed from ubuntu desktop to ubuntu studio, so i'm updating here.

I just did a clean install of ubuntu studio on my laptop.  My goal here is to use midi to play the piano via my keyboard midi controller.  here are the steps I've taken so far:

-in terminal:  qsynth -a alsa

-in setup, select the piano soundfont.

-from the sound & video menu open JACK Control

-also from the sound & video menu open virtual midi keyboard (my midi controller will arrive in the mail later this week)

-In the alsa tab of the jack connection window i match up the virtual keyboard with the fluid synth and connect them.

and i play the virtual keyboard and it sounds not like a piano, but the sound of a racketball echoing in a racketball court . . . 

i hadn't changed any of the setting is qsynth other than selecting the soundfont.  the soundfont i'm using works fine on my desktop so I don't think that is the problem.

anyone know what the problem might be?  I just want it to sound like a piano . . .

thanks in advance!

p.s. when i mess around with the settings (reverb or chorus) in qsynth it doesn't seem to change the sound at all.

---

### Post by thorgal on 2009-02-18
hey!

I am on vacation so I cannot help you for a while. I'll be back this week so I'll see if I can help during the week-end.
Cheers!

---

### Post by angelsneverdie on 2009-02-18
> **thorgal said:**
> hey!

I am on vacation so I cannot help you for a while. I'll be back this week so I'll see if I can help during the week-end.
Cheers!

Thanks!  Have fun on vacation!

---

### Post by raboofje on 2009-02-18
> **angelsneverdie said:**
> My goal here is to use midi to play the piano via my keyboard midi controller. (...) qsynth -a alsa (...) and i play the virtual keyboard and it sounds not like a piano, but the sound of a racketball echoing in a racketball court

I noticed that in qsynth, too, and for me simply turning the gain (leftmost knob) down to ~20 gives acceptable results. Weird though.

---

### Post by angelsneverdie on 2009-02-18
> **raboofje said:**
> I noticed that in qsynth, too, and for me simply turning the gain (leftmost knob) down to ~20 gives acceptable results. Weird though.

I tried that, and all it did was make it quieter - same distorted sound.

---

### Post by raboofje on 2009-02-19
> **angelsneverdie said:**
> I tried that, and all it did was make it quieter - same distorted sound.

Is qsynth playing directly to ALSA or to JACK? Do other applications play without to ALSA/JACK without distortion?

---

### Post by thorgal on 2009-02-20
hi foobar ... uh! raboof :D
I told angelsneverdie to not start jack for audio, but just use qjackctl's convenient ALSA MIDI tab. So audio is using ALSA. 

I suggest he tweaks the buffer size in qsynth, it might be too small. I think IIRC that qsynth sets the buffer size to 64 frames by default, which is quite small. You can change that in the setup window and restart the qsynth ALSA driver (from the same window). Something like 256 or 512. It will increase the latency but not dramatically.

---

### Post by angelsneverdie on 2009-02-20
> **thorgal said:**
> hi foobar ... uh! raboof :D
I told angelsneverdie to not start jack for audio, but just use qjackctl's convenient ALSA MIDI tab. So audio is using ALSA. 

I suggest he tweaks the buffer size in qsynth, it might be too small. I think IIRC that qsynth sets the buffer size to 64 frames by default, which is quite small. You can change that in the setup window and restart the qsynth ALSA driver (from the same window). Something like 256 or 512. It will increase the latency but not dramatically.

I changed it to 256 and no sound came out - I changed it to 512 and guess what?  piano sounds came out!!!!!  I'll try hooking it up to the midi controller tonight and let you know how it sounds. 

Thanks for all your help!

---

