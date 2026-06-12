---
title: "sound issue (again!)"
date: 2009-10-16
forum: Server Platforms
---

### Post by gobbledigook on 2009-10-16
Hi!

i have posted previously about my sound issues [here]("http://ubuntuforums.org/showthread.php?t=1254508") to which i had no response... so i have gathered some more (hopefully helpful) information to see if this can be solved :)

I am running: kernal 2.6.28-15-server as a small web host and fileserver, which provides a media function to my TV via [xbmc]("http://xbmc.org/"), my s-video output and the sound hooked up to an amp. The problem i am having is that although the sound works it is soooo quiet that i have to have the amp on max to hear anything! and even then, when watching a movie it can still be almost inaudable dialogue.

I already have alsa-base and alsamixer and pulseaudio installed - and turned up;) so i have looked at all the other threads with "sound" in the title, and hopefully some of this info will help to solve my problem :)

```
server@server:~$ lsmod | grep snd
snd_hda_intel         433844  4
snd_pcm_oss            46208  0
snd_mixer_oss          22528  1 snd_pcm_oss
snd_pcm                83204  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0
snd_seq_oss            37760  0
snd_seq_midi           14208  0
snd_rawmidi            29568  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                57008  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m                                                                             idi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi                                                                             di,snd_seq
snd                    62628  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm                                                                             ,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm

```

```
server@server:~$ asoundconf list
Names of available sound cards:
NVidia
```

```
server@server:~$ lspci|grep Audio
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
```

```
server@server:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf9ef8000 irq 21
server@server:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC662 rev1
server@server:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
server@server:~$ sudo nano /etc/asound.conf:

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```

---

### Post by gobbledigook on 2009-10-17
*bump* 

anyone?? can i install sound modules from ubuntu desktop editoin for example? and how would i do that?

---

### Post by ezacon on 2009-10-17
Once i had similar problem. It was the volume control for some channel too low or disabled.
Try in command line "alsamixer" and ensure none is muted and volume in at 100%.

Hope this help

---

### Post by gobbledigook on 2009-10-19
> **gobbledigook said:**
> I already have alsa-base and alsamixer and pulseaudio installed - and turned up

Yeah i'm way ahead of you there!! the most annoying thing about alsamixer is that it mutes on reboot!

---

### Post by shred_eng on 2009-11-15
hi, i linked to this thread from ubuntu server forum, i have sound on my ubuntu server, i decided to unistall alsa and pulse and install oss4, this worked real well,

edit: oops, i never noticed both posts were in same place, sorry for oss4 spam

---

