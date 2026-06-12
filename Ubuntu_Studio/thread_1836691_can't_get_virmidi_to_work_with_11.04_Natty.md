---
title: "can't get virmidi to work with 11.04 Natty"
date: 2011-08-31
forum: Ubuntu Studio
---

### Post by ajaustin on 2011-08-31
I had virmidi working fine with 10.4 Lucid but since updating to 11.04 Natty I cannot make it work.

I have followed the HOWTO [http://tldp.org/HOWTO/MIDI-HOWTO-10.html](http://tldp.org/HOWTO/MIDI-HOWTO-10.html) which is the best and about the only reference I can find.  It's out of date but I've done my best with it.

I have installed the standard 11.04 installation as an update from 10.04 - generally everything is fine, just this one problem.

My installation includes:-

paman - Pulse Audio Manager
pulseaudio
pulseaudio-module-jack
qjackctl
jackd1 (I can't get jackd2 to work)
aconnectgui - midi router
vmpk - virtual midi piano keyboard
timidity - midi synthesizer

Here's what I've done:-

```
/etc/modules

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
snd-virmidi index=1
```

virmidi seems to load fine

> tony@ubuntu:~$ lsmod|grep virmidi
snd_virmidi            13064  0
snd_seq_virmidi        13309  1 snd_virmidi
snd_rawmidi            25269  2 snd_seq_virmidi,snd_seq_midi
snd_seq_midi_event     14475  2 snd_seq_virmidi,snd_seq_midi
snd_seq                51291  8 snd_seq_dummy,snd_seq_virmidi,snd_seq_midi,snd_seq_midi_event
snd                    55295  19 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_virmidi,snd_seq_virmidi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tony@ubuntu:~$

I put these lines in /etc/modprobe.d/alsa-base.conf

```
 # mods for virmidi
 # Configure support for OSS /dev/sequencer and
 # /dev/music (aka /dev/sequencer2)
 # (Takashi Iwai advises that it is unnecessary
 # to alias these services beyond the first card, i.e., card 0)
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-8 snd-seq-oss

 # Configure card 1 (second card) as a virtual MIDI card
alias sound-slot-1 snd-card-1
alias snd-card-1 snd-virmidi
```

the sound stopped working altogether so I took them out again.

I've checked

> tony@ubuntu:~$ cat /proc/asound/cards
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1981B at irq 21
 1 [VirMIDI        ]: VirMIDI - VirMIDI
                      Virtual MIDI Card 1
tony@ubuntu:~$

> tony@ubuntu:~$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 1- 3]: raw midi
  3: [ 1- 2]: raw midi
  4: [ 1- 1]: raw midi
  5: [ 1- 0]: raw midi
  6: [ 1]   : control
  7: [ 0- 4]: digital audio playback
  8: [ 0- 3]: digital audio capture
  9: [ 0- 2]: digital audio capture
 10: [ 0- 1]: digital audio capture
 11: [ 0- 0]: digital audio playback
 12: [ 0- 0]: digital audio capture
 13: [ 0]   : control
 33:        : timer
tony@ubuntu:~$

> tony@ubuntu:~$ aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'Virtual Raw MIDI 1-0' [type=kernel]
    0 'VirMIDI 1-0     '
client 21: 'Virtual Raw MIDI 1-1' [type=kernel]
    0 'VirMIDI 1-1     '
client 22: 'Virtual Raw MIDI 1-2' [type=kernel]
    0 'VirMIDI 1-2     '
client 23: 'Virtual Raw MIDI 1-3' [type=kernel]
    0 'VirMIDI 1-3     '
client 129: 'TiMidity' [type=user]
    0 'TiMidity port 0 '
    1 'TiMidity port 1 '
    2 'TiMidity port 2 '
    3 'TiMidity port 3 '
tony@ubuntu:~$

> tony@ubuntu:~$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'Virtual Raw MIDI 1-0' [type=kernel]
    0 'VirMIDI 1-0     '
client 21: 'Virtual Raw MIDI 1-1' [type=kernel]
    0 'VirMIDI 1-1     '
client 22: 'Virtual Raw MIDI 1-2' [type=kernel]
    0 'VirMIDI 1-2     '
client 23: 'Virtual Raw MIDI 1-3' [type=kernel]
    0 'VirMIDI 1-3     '
tony@ubuntu:~$

Everything is as per the HOWTO.

HOWTO says

>  $ ln -s /dev/snd/midiC2D0 /dev/midi20
 $ ln -s /dev/snd/midiC2D1 /dev/midi21
 [...]

but this should not be necessary, so don't do this at home, kids! 

I can't find an install of for aseqview anywhere and don't know if it would be useful if I did.

I can use either qjackctl or aconnectgui to make the virtual patches.

I test thus:-

1. start timidity
2. launch vmpk virtual keyboard
3. edit connections in vmpk to send output to a timidity port
4. play the keyboard and I can hear the piano

5. edit connections in vmpk to send output to virmidi port
6. change the connections in aconnectgui
[IMG]http://www.wikiwhatever.com/aconnectgui-1.jpg[/IMG][IMG]http://www.wikiwhatever.com/aconnectgui-3.jpg[/IMG]
7. play the keyboard and there is no sound
8. conclusion: virmidi is not working.

If anyone can shed any light on this I would be grateful.

Tony

---

### Post by ajaustin on 2011-09-05
deleted

---

### Post by ajaustin on 2011-09-08
deleted

---

### Post by ajaustin on 2011-09-08
I got an answer to this at [http://lau.linuxaudio.org/](http://lau.linuxaudio.org/).  There is a mailing list there and you can subscribe at [http://lists.linuxaudio.org/listinfo/](http://lists.linuxaudio.org/listinfo/).

I seems that the reason I couldn't make virmidi work was that it is the wrong tool for the job I was trying to do.  I should have been using snd_seq_dummy kernel module.

Adding ```
snd_seq_dummy ports=4
``` to /etc/modules gives me 4 Midi Through Ports that I can use to send data between applications; in my case from Band in a Box to Reaper (both under Wine).  Works great!

Tony

---

### Post by s.fox on 2011-09-08
Please do not create duplicate threads. Thank you.

Theads merged.

---

