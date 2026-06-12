---
title: "USB Audio Capture"
date: 2012-01-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by clivejo on 2012-01-07
I have a USB video capture device.  Its detected by the kernel and video is on /dev/video1 and I can see this OK in VLC.  However I cant seem to get the audio to work.

[B]cat /proc/asound/cards
[/B]```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4500000 irq 48
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xcdefc000 irq 16
 2 [Em28xxAudio    ]: Em28xx-Audio - Em28xx Audio
                      Empia Em28xx Audio

```

The audio device seems to be detected, but I'm unable to get any audio from it.  Anyone able to help?

---

### Post by lucazade on 2012-01-07
have you checked in 'alsamixer' if any channel is muted?

---

### Post by clivejo on 2012-01-07
> **lucazade said:**
> have you checked in 'alsamixer' if any channel is muted?

Yes, first thing I checked.

Also in System Settings > Sound > Input tab

Choose device for sound input : Video Grabber Analogue Sound and volume is 100% unmuted.

There seems to be two connectors : Line in and Video  
I have tried both of these.

---

### Post by clivejo on 2012-01-07
I have just run 'pavucontrol'

Under the tab 'Input devices' I cant see any Hardware Input devices, I was expecting to see the Video Grabber.

---

### Post by dino99 on 2012-01-07
on my system the sound chipset was not detected  (alc682) so i added it:

sudo nano /etc/modprobe.d/alsa-base.conf

you need to identify yours to set the good choice

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by clivejo on 2012-01-07
**cat /proc/asound/card0/codec* | grep Codec**
```
Codec: Conexant CX20583 (Pebble HSF)

```

**cat /proc/asound/card1/codec* | grep Codec**
```
Codec: Nvidia GPU 0a HDMI/DP
Codec: Nvidia GPU 0a HDMI/DP
Codec: Nvidia GPU 0a HDMI/DP
Codec: Nvidia GPU 0a HDMI/DP

```

**cat /proc/asound/card2/codec* | grep Codec**
```
cat: /proc/asound/card2/codec*: No such file or directory

```

Yet, the command

**cat /proc/asound/cards**
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4500000 irq 48
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xcdefc000 irq 16
 2 [Em28xxAudio    ]: Em28xx-Audio - Em28xx Audio
                      Empia Em28xx Audio

```

I dont really understand, is it that my system knows there is a third sound card/device, but it doesn't know how to use it?

---

### Post by clivejo on 2012-01-07
And the command

**arecord -l**
```

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Em28xxAudio [Em28xx Audio], device 0: Em28xx Audio [Empia 28xx Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by clivejo on 2012-01-09
I can hear and see video using this command

 [COLOR=#000000][B]mplayer tv:// -tv driver=v4l2:device=/dev/video1:audiorate=48000:immediatemode=0:forceaudio:alsa:adevice=hw.2:buffersize=64
[/B]
[/COLOR]
But cant get it working on VLC

---

