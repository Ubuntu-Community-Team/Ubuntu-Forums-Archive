---
title: "Mixxx (etc) don't like PulseAudio in 10.10 Maverick 64"
date: 2010-10-18
forum: Ubuntu Studio
---

### Post by daveuu on 2010-10-18
Hi

On a fresh install of 10.10 Maverick Ubuntu Studio 64 with an Edirol UA-5, M-Audio Fast-Track Pro attached via USB and HDA NVidia ALC1200 on-board audio interface, Mixxx appears to be generally defective by default.

- Graphical interface redraw has problems
- Tracks usually don't load
- If a track does load it doesn't play

If I edit /etc/pulse/client.conf with 'autospawn=no' then kill pulseaudio with 'pactl exit' and run Mixxx it is much more responsive and it will load and 'play' tracks (the waveform graph moves) using interface 'null'. If set to interface 'ALSA' it cannot connect to the audio device and the debug info includes references to pulse audio so I'm guessing ALSA is still mapped to a non-existent pulse audio server.

Finally, if I install 'jackd1' instead of 'jackd2' and restart, pulse seems completely broken and Mixxx will happily load tracks play them via ALSA but with the odd under-run/audio glitch.

Very finally: M-Audio Fast Track Pro has 4 outputs appearing as 2 stereo devices. Device B is also the SPDIF digital out (even though it's labelled as Analog Out B in pavucontrol). Even if Pulse Audio was friends with Mixxx in 10.10 64 out-of-the-box, it isn't :-(, Mixxx can only see 'pulse' as a single audio output device which pavucontrol in turn can only map to a single device: either M-Audio Fast Track Pro device A or device B. This means it is not possible to use 2 stereo outs from Mixxx into 2 separate devices, even if those 2 'devices' are in fact in a single hardware box . . . . Is there a way around this: if pulse can be made to work with Mixxx and other packages (FreeBirth for one is blocked from the sound devices by pulse by 'default') can I use 2 stereo 'devices' from one program (2 pulse sound servers?)

many thanks,

Dave

---

### Post by fatwilly6 on 2010-11-05
Hi there - forgive me for perhaps trying to teach you to suck eggs but have you made sure you have the right audio interface designated in system > sound preferences? I believe pulseaudio can only deal with one device at a time so if there are multiple devices on the system you need to ensure the device with the speakers is where the output is going. Also Intel HDA chips require config file editing/hacking and you should check the forums for how to id the chip and then see if any 'tweaks' are required. Also lots of people (including me) are struggling with Meerkat & sound - another few weeks should see the collective brain find solutions!

The other thing to try is reinstalling alsa as per [this thread]("https://help.ubuntu.com/community/SoundTroubleshooting")

---

