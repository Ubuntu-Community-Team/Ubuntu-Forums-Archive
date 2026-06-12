---
title: "jack-rack: no sound"
date: 2009-12-13
forum: Ubuntu Studio
---

### Post by breek on 2009-12-13
this is what i do:

- open jack control and click on start
- start jack-rack
- add some stuff (preamp, reverb..)
- connect system -> capture_1 to jack_rack_1785 -> in_1
- connect system -> capture_2 to jack_rack_1785 -> in_2
- connect jack_rack_1785 -> out_1 to system -> playback_1
- connect jack_rack_1785 -> out_2 to system -> playback_2

but i hear no sound from speakers (soundcard works as i hear mp3s and videos and mic/line-in sliders are up).
what's wrong?

---

### Post by AutoStatic on 2009-12-14
What are you running through jack-rack? And did you enable the effects, they are disabled by default.

---

### Post by breek on 2009-12-14
i connected my guitar to the mic input (my soundcard has only this as input) and the "enable" button on every effect is pressed

---

### Post by AutoStatic on 2009-12-14
And what if you run **alsamixer** from a terminal? If alsamixer only shows PulseAudio then the command is possibly **alsamixer -c0**. Is the mic enabled and not muted (MM means muted)? And do you have a mic boost option? It's also possible that you need to switch between input sources, which input sources are active now?

---

### Post by breek on 2009-12-15
pulseaudio was not installed, only libpulse so i installed pulseaudio too but nothing changed.
alsamixer is set as shown in the screenshots.
i tried mic1 and mic2 but nothing changed

---

### Post by AutoStatic on 2009-12-15
Your Mic Boost is muted, could you enable the Mic Boost? And thanks for the screenshots! And why did you install PulseAudio? You didn't have to.

---

### Post by breek on 2009-12-15
because pulseaudio looked to me a better soundserver :P
i've tried mic boost but doesn't solve the problem :(

---

### Post by AutoStatic on 2009-12-15
Ah, you have Xubuntu, then PulseAudio is not installed by default.
Did you also try toggling the Mic switch again after enabling the Mic Boost? There is also a possibility that the signal from the guitar is still too weak, doubt that though.

---

### Post by breek on 2009-12-19
ok, i solved one problem but still i can't get what i want.
i changed the cable connecting my guitar to soundcard (seems that a stereo cable cannot be used for this purpose) and now i hear my guitar from speakers (even before i start jack).
the problem is that whatever i add on jack rack the sound doesn't change, only the plain sound from guitar :(
any ideas?

---

### Post by AutoStatic on 2009-12-19
Could you post a screenshot of the Connections window of QjackCtl? Did you route the input signal through JACK-Rack?

---

### Post by gorgon on 2009-12-19
Also, did you (as AutoStatic mentioned in 2nd post) enable the effects with the 'enable' button on each effect?

On my JackRack it doesnt make the connections in Jack on startup, you might have to go to the Jack control, to 'Connect' and the make the connections from 'capture' to 'jack_rack' and 'jack_rack' to 'playback'.

---

### Post by breek on 2009-12-19
thanx for the quick reply ;)

here is the screenshot ->

[[IMG]http://img138.imageshack.us/img138/8389/jacke.th.png[/IMG]](http://img138.imageshack.us/i/jacke.png/)

---

### Post by gorgon on 2009-12-19
> now i hear my guitar from speakers (even before i start jack).

ok, i didnt see that you wrote this earlier - so there should be a setting in your sound mixer (alsamixer) where you choose your input. Click the speaker icon and try different settings - im not familiar with the interface of xubuntu sound mixer...

tell us how it goes!

---

### Post by gorgon on 2009-12-19
Actually, you can do this from alsamixer - make sure that the mic volume is all the way down in the 'playback' section, then switch to 'capture' (hitting TAB) and make sure mic volume is up and that the right input is selected (might be called 'input source' or 'mic sel' or something...).

---

### Post by breek on 2009-12-19
it doesn't work :(
i selected/deselected "line-in capture", "microphone capture", and "aux capture" without success.
in the "capture" tab i raised the sliders and activated the control, after muting line-in and mic... but it doesn't work :(
when i do the connection shown in the previous screenshot i hear a bit more background noise

---

### Post by gorgon on 2009-12-19
Hm, ok, looking at your screenshot of the jack connections it looks like you got an external soundcard with many inputs? Try connecting some of the alsa_pcm monitor channels to jack_rack.

also, try to use an effect in Jack Rack that you can hear clearly if its working or not, like a delay. Distortion can be quite subtle at times.

---

### Post by RaumTrug on 2009-12-19
Hi! seems like you're connecting right, most alsa drivers use channel 1 & 2 for left/right stereo, the others are probably for surround sound.

install "jack meterbridge" and connect your signal to it like you did with jack rack. you should hear your signal from the guitar with some nasty delay that'll be unbearable for a realtime guitar fx setup due to your bad jackctl configuration, and the meter should display something. also disable those "monitor" and "hw monitor/meter" stuff, I doubt your card supports them! plus in the alsamixer playback tab mute line/mic or whatever you're using, but select, unmute & turn up in the capture tab, or you'll hear the signal doubled with slight delay (one from the soundcard directly playing thru the input, and one from the jack routing input->meter->output, this is what you want!)

if still no success, try routing some music prog like audacious or aqualung in jack mode to the outputs - if you hear something, then it's probably sound card configuration/alsa driver problems! if you hear nothing, try connecting one of the 2 music channels to any output, you should hear something, anyways!

cheers! ;)

---

