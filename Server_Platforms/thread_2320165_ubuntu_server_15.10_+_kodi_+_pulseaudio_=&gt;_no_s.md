---
title: "ubuntu server 15.10 + kodi + pulseaudio =&gt; no sound over HDMI  [fixed]"
date: 2016-04-11
forum: Server Platforms
---

### Post by pikoli on 2016-04-11
hey guys!

I installed kodi following this: [http://forum.kodi.tv/showthread.php?tid=231955](http://forum.kodi.tv/showthread.php?tid=231955) 

And sound was working fine. I could choose HDMI or analog, and there was sound on both outputs.

But because I wanted sound on both outputs to work simultaneously, I installed pulseaudio. 

Now i have two options in the Kodi: default and analog, and both output only to analog. It is like HDMI is not even recognised. help!

output of "aplay -l"
> card 0: PCH [HDA Intel PCH], device 0: ALC662 rev3 Analog [ALC662 rev3 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

output of pacmd list-sinks
> 1 sink(s) available.
  * index: 0
        name: <auto_null>
        driver: <module-null-sink.c>
        flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE
        priority: 1000
        volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
                balance 0.00
        base volume: 65536 / 100% / 0.00 dB
        volume steps: 65537
        muted: no
        current latency: 0.00 ms
        max request: 344 KiB
        max rewind: 344 KiB
        monitor source: 0
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 0
        linked by: 0
        configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
        module: 10
        properties:
                device.description = "Dummy Output"
                device.class = "abstract"
                device.icon_name = "audio-card"


---

### Post by pikoli on 2016-04-11
I realised, if I try to play sound with aplay on analog, it works:

aplay -D hw:0,0 /a.wav         <- sound is coming out

if I try to play it from hdmi speakers:

aplay -D hw:0,3 a.wav         <- no sound

I don't get error in terminal, it looks like it is playing, but there is no sound...



and here is my alsa information:
[http://www.alsa-project.org/db/?f=60b10f86b621b698e2c35aaeb84ab16bb36c8edd](http://www.alsa-project.org/db/?f=60b10f86b621b698e2c35aaeb84ab16bb36c8edd)

---

### Post by pikoli on 2016-04-12
Hey, I managed to fix the problem. Kind of.

I think it was caused by a bug in pulseaudio or something.

The thing is, that pulseaudio module "MODULE-UDEV-DETECT" should detect both, hdmi and analog out, but for some reason it only detects analog. But if I then run "MODULE-DETECT", also my HDMI out is recognised. With that, I get an error saying that "module-alsa-source" failed to load, but otherwise it works.

I tried to load "MODULE-UDEV-DETECT" twice, but it refuses to do so. :P

At the beginning I tried to alleviate the problem by manually adding HDMI out to pulseaudio: "load-module module-alsa-sink device=hw:0,3" and unmuting the S/PDIF (HDMI is disguised as S/PDIF in alsamixer), but pulseaudio would mute it upon every start. Bash script that run at boot kind of fixed that, but not entirely, because pulseaudio would sometimes still mute it during operation on its own (it probably restarted, but I am not sure)

And now I have a question if something is wrong, if I run MODULE-UDEV-DETECT and then MODULE-DETECT right after? 

bye

---

