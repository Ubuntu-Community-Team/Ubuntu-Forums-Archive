---
title: "M-Audio M-Track output audio crashes to white noise using Pulseaudio"
date: 2016-08-06
forum: Ubuntu Studio
---

### Post by Musicjunkie4537 on 2016-08-06
I've experienced this problem in both 14.04 (Trusty Tahr) and 16.04 (Xenial Xerus) and using three different hardware systems.

I'm not sure if this is a problem with the USB Audio ALSA driver or a problem with PulseAudio.  Based on my observations, it is most likely PulseAudio, because I seldom come across this while using Jack.

At seemingly inconsistent intervals, the audio will start a pinging (sounds like tapping on glass or metal.  Other words I would use to describe it are hollow or fuzzy, ) as if the data streamed from my Audio Interface may not be in sync.

Most of the time, though, it will completely crash out and output a horrendous hiss of white noise. It completely eclipses the output of the audio currently being played-back and my hardware mixer's peak meter shows as full blast/extreme clipping. When the music is up loud the crash out is enough to make anyone go insane for a moment and throw off their headphones / unplug their equipment immediately to make it stop. (not to mention the potential to damage speakers and/or other audio equipment.)

This seems to occur most often while streaming audio in a browser. I initially thought it could be due to Flash or some browser behavior, but I have also experienced it with all browsers closed and streaming music stored on my hard disk using the Audacious playlist manager.

I use an OpenSUSE 42.1 for work and have not experienced this behavior on this OS yet.


Could this be a fault of PulseAudio?


I've had the audio dropouts/white noise crashes happen with Ardour sessions using Jack, but usually only when I've stepped away from my audio project for several hours and come back to it. When I close out of my project and qjackctl, then restart jackd and reload my session, everything is back to normal.

My current workaround in Pulse is to open pavucontrol, select the "configuration" tab, and set the M-Audio interface to off or set it to Analog Stereo Duplex and back to Digital Stereo Duplex.

Normally my setting is on Digital Stereo Duplex (IEC958)

I have also experienced this issue using Analog Stereo Duplex.



Any tips for debugging my PulseAudio configuration or potentially the ALSA driver in use would be greatly appreciated.

I've tried the solution here and it didn't make a difference.
[https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Glitches.2C_skips_or_crackling](https://wiki.archlinux.org/index.php/PulseAudio/Troubleshooting#Glitches.2C_skips_or_crackling)

---

### Post by Musicjunkie4537 on 2016-08-19
I've narrowed down the issue as to being a problem with PulseAudio. My other operating system gives the option to install it.  I tried and it crashed out on the other OS.  

Instead, I've decided to take PulseAudio out of the picture entirely.  Here's how I did it.

I uncommented and modified the following parameter in the  [FONT=courier new]/etc/pulse/client.conf[/FONT] file:
```
autospawn = no
```

Killed PulseAudio for the change to take effect:
```
user@hostname: pulseaudio --kill
```

Then manually configured ALSA to use my M-Audio M-Track audio interface as the default.

First I found how the system identified the different sound cards:
```
user@hostname:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD1984A Analog [AD1984A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: AD1984A Alt Analog [AD1984A Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: MTrack [M-Track], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

Then I modified the [FONT=courier new]/usr/share/alsa/alsa.conf [/FONT]to set the default card to the card number I found for the M-Track audio interface:
```
...
defaults.ctl.card 2
defaults.pcm.card 2
...
```


I haven't had any issue in about a week's worth  of daily use.  The hardware controls on the device basically do the job of Pulse anyway.

We can conclude that PulseAudio was the problem and should not be used with this Audio Interface.

---

