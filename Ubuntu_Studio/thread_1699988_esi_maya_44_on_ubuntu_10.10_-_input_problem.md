---
title: "esi maya 44 on ubuntu 10.10 - input problem"
date: 2011-03-04
forum: Ubuntu Studio
---

### Post by jesuslovesben on 2011-03-04
Hi there!

I need some help with my esi maya 44 soundcard: I can't get the input channels working. It's great that the output works straight away, but I can't get any microphone/line-in input. The normal mixer does show one input channel but there is no input recognised. Envy 24control doesn't start up at all. Does anybody have an idea?

Thanx,

Ben

---

### Post by Pablo_F on 2011-03-04
Hi, 

Are you trying to run envy24control from a terminal?

What is the terminal output of cat /proc/asound/cards

---

### Post by jesuslovesben on 2011-03-04
> **Pablo_F said:**
> Hi, 

Are you trying to run envy24control from a terminal?

What is the terminal output of cat /proc/asound/cards

Thanx for replying!

I've tried both - have it run from terminal and menu.

The output is:

benjamin@benjamin-desktop:~$ envy24control
No ICE1712 cards found
benjamin@benjamin-desktop:~$ ^
benjamin@benjamin-desktop:~$ cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfbfec000 irq 47
 1 [Maya44         ]: ICE1724 - ESI Maya44
                      ESI Maya44 at 0xdc00, irq 17
benjamin@benjamin-desktop:~$

---

### Post by Pablo_F on 2011-03-04
Hi, 

Oh, it seems that card is not supported by the snd-ice1712 module, but snd-ice1724. You can check with *lsmod* or *cat /proc/asound/modules*.  Afaik, envy24control is for ice1712 cards only.

I don't own a card like yours but I could try to help if you give the output of 

**arecord -l && aplay -l**

**amixer -c1** (similar to alsamixer but in text only mode, please use code tags)

You can always ask/search in the alsa users mailing list.

Cheers, Pablo

---

### Post by jesuslovesben on 2011-03-05
Hi!

I finally managed to get some Line-In signal using alsamixer, but no microphone input and I also couldn't use it in Jack, as it didn't show there.

I'll keep on trying,

just posted your requested outputs:

> **Pablo_F said:**
> 
**arecord -l && aplay -l**



**** Liste der Hardware-Geräte (CAPTURE) ****
Karte 1: Maya44 [ESI Maya44], Gerät 0: ICE1724 [ICE1724]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Maya44 [ESI Maya44], Gerät 1: ICE1724 Secondary [ICE1724 Secondary]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: HDMI [HDA ATI HDMI], Gerät 3: ATI HDMI [ATI HDMI]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Maya44 [ESI Maya44], Gerät 0: ICE1724 [ICE1724]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Maya44 [ESI Maya44], Gerät 1: ICE1724 Secondary [ICE1724 Secondary]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Maya44 [ESI Maya44], Gerät 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

> **Pablo_F said:**
> **amixer -c1** (similar to alsamixer but in text only mode, please use code tags)


[B]Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 205 [80%] [-25.00dB] [on]
  Front Right: Playback 205 [80%] [-25.00dB] [on]
Simple mixer control 'PCM',1
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 204 [80%] [-25.50dB] [on]
  Front Right: Playback 204 [80%] [-25.50dB] [on]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 91
  Front Left: Capture 0 [0%] [-99999.99dB] [on]
  Front Right: Capture 0 [0%] [-99999.99dB] [on]
Simple mixer control 'Line',1
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 91
  Front Left: Capture 81 [89%] [19.50dB]
  Front Right: Capture 81 [89%] [19.50dB]
Simple mixer control 'Mic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive penum
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]
Simple mixer control 'Mic Phantom Power',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Output',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Bypass',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Bypass',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Crossmix',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 80
  Mono:
  Front Left: Playback 72 [90%] [-2.00dB]
  Front Right: Playback 72 [90%] [-2.00dB]
Simple mixer control 'Crossmix',1
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 80
  Mono:
  Front Left: Playback 73 [91%] [-1.00dB]
  Front Right: Playback 73 [91%] [-1.00dB]
Simple mixer control 'H/W',0
  Capabilities: penum
  Items: 'PCM Out' 'Input 1' 'Input 2' 'Input 3' 'Input 4'
  Item0: 'PCM Out'
Simple mixer control 'H/W',1
  Capabilities: penum
  Items: 'PCM Out' 'Input 1' 'Input 2' 'Input 3' 'Input 4'
  Item0: 'PCM Out'
Simple mixer control 'H/W',2
  Capabilities: penum
  Items: 'PCM Out' 'Input 1' 'Input 2' 'Input 3' 'Input 4'
  Item0: 'PCM Out'
Simple mixer control 'H/W',3
  Capabilities: penum
  Items: 'PCM Out' 'Input 1' 'Input 2' 'Input 3' 'Input 4'
  Item0: 'PCM Out'
Simple mixer control 'Multi Track Internal Clock',0
  Capabilities: enum
  Items: '32000' '44100' '48000' '64000' '88200' '96000' '176400' '192000' 'IEC958 In'
  Item0: '44100'
Simple mixer control 'Multi Track Rate Locking',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Multi Track Rate Reset',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'SPDIF',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [off]
[/B]

---

### Post by jesuslovesben on 2011-03-05
solved it - gnome-alsamixer did the job for me! Thnx a lot for your advise, it made me try out different mixers!

---

### Post by sgx on 2011-03-05
Hi, could you check the output of

 lsmod

to see if it has both snd_ice1712 and snd_ice1724?
This might help future discussions.

Cheers

---

### Post by siabost on 2011-11-03
edit: OOPS Hadn't noticed that this thread is marked "SOLVED" - will start a new thread...

Hi Guys,

Ubuntu Studio 11.10 64bit
ESI Maya44 PCI Card (4in/4out)

I have a slightly different problem with this card:
In Jack it shows me only 2 inputs & 4 outputs no matter how I change things in Jack settings.

The card is recognised by both Jack and the installed SoundMixer utility. I installed gnome-alsamixer but it refuses to start (Ubuntu Studio no uses XFCE desktop so I don't know if this is the cause). Alsamixer-gui only shows 2 channels and allows no adjustment.

I haven't tried alsamixer from the terminal yet so that's left to try.

It seems, though I'm not sure, that Jack splits the inputs so that HW1,0 is ICE1724 inputs 1 & 2 & HW1,1 is ICE1724 inputs 3 & 4) but I'm short of connector leads at the minute so can't prove it.

Does anyone have any idea how to get 4 inputs functioning together?

Many thanks.

---

### Post by krzakx on 2011-11-14
**jesuslovesben** you have USB or PCI version? I have USB version and I can't adjust input levels. Please help me.

---

