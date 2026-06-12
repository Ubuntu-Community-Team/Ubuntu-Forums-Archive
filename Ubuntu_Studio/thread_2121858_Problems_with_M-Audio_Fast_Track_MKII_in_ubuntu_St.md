---
title: "Problems with M-Audio Fast Track MKII in ubuntu Studio"
date: 2013-03-03
forum: Ubuntu Studio
---

### Post by Tuxky on 2013-03-03
Hello. I'm recently back to using ubuntu, after terrible windows years, and I really like ubuntu Studio. However, I'm having trouble putting my M-Audio Fast Track II to work. I see many people in forums complaining about similar problems with similar m-audio products, but I also see some folks say it works just fine. About fast track pro, for instance, I've read it works 16 bit out-of-the-box, but to get it to record in 24 bits you have to compile the kernel. ( [http://joegiampaoli.blogspot.com.br/2011/06/m-audio-fast-track-pro-for-debian-linux.html](http://joegiampaoli.blogspot.com.br/2011/06/m-audio-fast-track-pro-for-debian-linux.html) )
 I can playback audio with audacious through it, and I can hear my guitar on my amp (that's connected to the fast track's headphones output) ONLY IF I switch direct monitor ON. I can't hear my guitar on rakarrack, audacity and ardour don't get any audio signal. Here's some command-line outputs to clarify:
[PHP]joao@joao-Satellite-L505D:~$ arecord -l && aplay -l
**** Lista de Dispositivos CAPTURE Hardware ****
placa 0: SB [HDA ATI SB], dispositivo 0: ALC272 Analog [ALC272 Analog]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 1: Track [Fast Track], dispositivo 0: USB Audio [USB Audio]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
**** Lista de Dispositivos PLAYBACK Hardware ****
placa 0: SB [HDA ATI SB], dispositivo 0: ALC272 Analog [ALC272 Analog]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 1: Track [Fast Track], dispositivo 0: USB Audio [USB Audio]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
joao@joao-Satellite-L505D:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf2400000 irq 16
 1 [Track          ]: USB-Audio - Fast Track
                      M-Audio Fast Track at usb-0000:00:12.0-3, full speed

[/PHP]
 Sorry my terminal is in portuguese, but I guess you get it. Dispositivo means device, the rest is similar to english words :-)
 I wanted to get it running in 16 bit mode, at least, before I try to compile the kernel. Tried to force 16 bit in jack setup, didn't work. Please, help me!
 Tuxky.

---

### Post by Tuxky on 2013-03-04
Now i'm not even listening to sound from the output, with audacious! Don't know if it's the RCA cable or what...

---

### Post by Tuxky on 2013-03-05
Solved playback. Just a momentary jack bug. Now I'm back at exactly the same situation I described at the first post. Anyone know if there's a way of doing it without all the kernel stuff?

---

### Post by Tuxky on 2013-03-06
It seems to be a problem with usb speed. M-Audio MKII has USB 2.0, but my lsusb output goes:
Bus 001 Device 007: ID 125f:c81a A-DATA Technology Co., Ltd. Flash drive
Bus 002 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 003 Device 007: ID 0763:2024 Midiman M-Audio Fast Track MKII
Bus 003 Device 006: ID 19ff:0211 Dynex 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Does it mean that the fast track is connected and working as usb 1.1? How to get it to work as 2.0? It doesn't matter in which port I plug it in, it's always Bus 003. My flash drive, however, as you can see connects to Bus 001.

---

### Post by jejeman on 2013-03-06
Even if it is USB 1.1 you should have plenty of speed for stream.
Your card 48KHz 24bit 2 ch. stream is 2.304 Mb/s which is < 12 Mbit/s FullSpeed USB.

Also, it says for the card that is USB 2.0 compatible, that does not mean that device is USB 2.0, which really don't need to be.

---

### Post by vecnu on 2013-03-18
I am interested in purchasing a M-audio fast track MKII. Did you finally solve the problem? 

Is there a similar audio interface which is known to work?

---

