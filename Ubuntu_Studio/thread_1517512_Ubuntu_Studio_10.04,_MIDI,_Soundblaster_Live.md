---
title: "Ubuntu Studio 10.04, MIDI, Soundblaster Live"
date: 2010-06-25
forum: Ubuntu Studio
---

### Post by nfidia on 2010-06-25
Hi,

I have Ubuntu Studio 10.04 on my machine, with this kernel running:

> root@samba:/# uname -r
2.6.31-10-rt


I have the following two sound devices in my machine:

```
root@samba:/proc/asound# cat cards 
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 19
 1 [Live           ]: EMU10K1 - SB Live! 5.1
                      SB Live! 5.1 (rev.7, serial:0x80641102) at 0xcf00, irq 20
```

I disabled the HDA-Intel - HDA ATI HDMI onboard sound chip via Gnome´s Main Menu > System > Preferences > Sound. On the Output tab I selected "SB Live! Emu10k1 Analaog Stereo". I did not select on this tab the other option which says "Simultaneous output to SB Live! Emu10k1 Analaog Stereo"

I installed the PulseAudio Server and disabled the HDA-Intel - HDA ATI HDMI Onboard chip in the graphical PulseAudio Server settings ("Volume Control", "Configuration" tab). 

My machine has the following MIDI clients and ports:
```

jrad@samba:~$ aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 20:0    SB Live! 5.1                     EMU10K1 MPU-401 (UART)
 21:0    Emu10k1 WaveTable                Emu10k1 Port 0
 21:1    Emu10k1 WaveTable                Emu10k1 Port 1
 21:2    Emu10k1 WaveTable                Emu10k1 Port 2
 21:3    Emu10k1 WaveTable                Emu10k1 Port 3
```

Problem:

When I execute

> aplaymidi --port=<client number>:<port number> <MIDI file>

like:
> 
aplaymidi --port=14:0 <MIDI file>

, then I cannot hear anything. I tried all listed clients : ports.

But if I play the same <MIDI file> using Totem Movie Player, then I can hear the <MIDI file>.

Why isn´t there any sound when I use aplaymidi?

Next steps to try to resolve the behaviour:

1. I will now check if the HDA-Intel - HDA ATI HDMI onboard sound chip is disabled in the BIOS, if not, I will disable it. Then I will check if aplaymidi plays the MIDI file generating sound.

2. I will check if aplaymidi plays the MIDI file generating sound using the generic kernel.

3. I will report the results here.

---

### Post by VH-BIL on 2010-06-25
This thread might help you:
[http://www.linuxquestions.org/questions/slackware-14/adventures-with-playing-midi-files-667145/](http://www.linuxquestions.org/questions/slackware-14/adventures-with-playing-midi-files-667145/)

---

### Post by nfidia on 2010-06-25
Thanks VH-BIL, for your fast reply ;-)

I will now check the link that you have specified, but before that let me inform the all of you that 

a) the onboard sound chip was already disabled in the BIOS
b) that I cannot hear sound using aplaymidi with the generic kernel.

---

### Post by VH-BIL on 2010-06-25
I think the problem is that you are selecting the through port. Try another one. aplaymidi is wanting to know where to get the sounds to play the midi file.

---

### Post by nfidia on 2010-06-25
> **VH-BIL said:**
> I think the problem is that you are selecting the through port. Try another one. aplaymidi is wanting to know where to get the sounds to play the midi file.

I tried every client : port which "aplaymidi -l" lists - no sound.

---

### Post by VH-BIL on 2010-06-25
try running jack and a software synth maybe.

---

### Post by nfidia on 2010-06-25
> **VH-BIL said:**
> try running jack and a software synth maybe.

Hm, I think it is not a good idea to try to resolve this using JACK. Before JACK should be involved in this issue, the problem with no MIDI sound using aplaymidi should be resolved on a more basic level.

Jack is something that is residing "on top" of ALSA.

If ALSA does not make MIDI files hearable, JACK shouldn´t be able to make MIDI files hearable, too.

By the way, I tried to hear something using MusE (before that I started JACK). I could not hear anything.

---

### Post by nfidia on 2010-06-25
PS: I tried to hear something with aplaymidi by having loaded a sound font before with asfxload. Result: negative.

---

### Post by nfidia on 2010-06-25
Now I tried timidity with the following command:

timidity --volume=100 <MIDI file>

(thanks VH-BIL, you made me aware of this via the external link you posted)

, and voila, it could hear the MIDI file.

This behaviour lets me point to the fact, that, since I have installed the PulseAudio server, alsamixer does not provide anymore all channels for mixing (including one channel for setting the MIDI volume, I guess).

Since the installation of the PulseAudio server alsamixer shows only one channel, i.e. the Master channel, see the attachment

Could it be that the PulseAudio server cannot or shouldn´t be used in connection with MIDI?

---

### Post by VH-BIL on 2010-06-25
Glad it works :)

---

### Post by nfidia on 2010-06-25
Yes, nice that this works, at least with timidity ;-)

But I do not understand why I cannot hear any sound using aplaymidi.

Something else worked now: I loaded a soundfont, then I started JACK, then MusE, and I could generate sound within MusE ;-)

Why didn´t this work before? Hm, maybe I made a mistake while using MusE.

---

