---
title: "Ubuntustudio RME Hammerfall"
date: 2008-06-03
forum: Ubuntu Studio
---

### Post by jonesints on 2008-06-03
Hi, 

I've got an RME Digi9636 soundcard. Jack recognizes the card without problem, but I can't seem to access any of the GUI tools provided for this card. ie HDSPConf and HDSPMixer won't load, and the Rmedigicontrol loads saying No RME Digi Souncard found...
I've got alsa-tools-gui and alsa-firmware-loaders installed.

Has anyone got the same card or know how to solve this issue?

many thanks!


Jonesints

UbuntuStudio 8.04 32bit
AMD Athlon 64 X2 Dual Core 4200+

---

### Post by couzin2000 on 2008-06-03
Hope I'm not disappointing you, I don't really have a solution for you, however I am curious to see about this problem since I too have (almost) the same config, and am looking to purchase a RME Hammerfall DIGI9652, to install into my Ubuntu-loaded system.

I'd love to hear about the performance of this after you've solved the issue!

(BTW, if you want to hear about a success story with this kind of hardware and Linux, read this: [http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm]("http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm")
Excellent article!)

You may want to find some info here: [http://www.alsa-project.org/main/index.php/Matrix:Module-hdsp]("http://www.alsa-project.org/main/index.php/Matrix:Module-hdsp")
This is a link to the ALSA website, which provides support for this card... you should be able to find something in there for you.

---

### Post by undfined on 2008-06-03
> **couzin2000 said:**
> 

(BTW, if you want to hear about a success story with this kind of hardware and Linux, read this: [http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm]("http://www.soundonsound.com/sos/feb04/articles/mirrorimage.htm")
Excellent article!)



Interesting.  I've got a Tascam DM-24 as well and am looking for a way to get rid of Windows on my recording PC.  Thanks for the link.

---

### Post by jonesints on 2008-06-04
Thanks couzin2000, I've had a look at the links and it made me realize the Rmedigicontrol, HDSPconf and HDSPmixer are not for this model of hammerfall I've got! so that's why they won't work..

On the other hand it just makes me think there MUST be a way to configure the digi9636 (aka hammerfall light) 

Anyone know what I can use?  I can change the device in the ALSA mixer to the hammerfall, but there isn't much I can do with it, for example, there are no faders!
I can use Jack to route the signals, but I don't want to have to use Ardour to control levels on the card!

Any clues?

---

### Post by fso_ on 2010-03-21
i have the same problem...

i tried to use the RME DIGI 9652 (Hammerfall) with Jack and also with just Alsa and Ardour. I now use it just plain with alsa, there is no need to use jack, however.. the performance is good, the card is working fine so far....

but:

as allready mentioned by others... i cant choose synch options for example... i used before suse linux 11.0. suse gave me a little cheap option menu where i could choose the prefered synch source and so on...

---

### Post by cb951303 on 2010-03-21
AFAIK, the main developer of Ardour is also the person who originally wrote the RME drivers (maybe he's still maintaining it) so you might have a better chance getting an answer in Ardour forum :popcorn:

---

### Post by fso_ on 2010-03-21
hmmm, maybe... thanks

---

### Post by fso_ on 2010-03-21
oh, i just found something, that might could help... 

cat /proc/asound/R15/**rme9652**

i did use that command in the terminal window... it schow me at least some kind aof a status the card is in at the moment.... looks like this at me:

mark@noname:~$ cat /proc/asound/R15/rme9652
RME Digi9652 (Rev 1.5) (Card #1)
Buffers: capture f3600000 playback f2c00000
IRQ: 18 Registers bus: 0xef000000 VM: 0xf85ea000
Control register: 24402f

Latency: 8192 samples (2 periods of 32768 bytes)
Hardware pointer (frames): 0
Passthru: no
Clock mode: autosync
Pref. sync source: ADAT1

ADAT1 Input source: ADAT1 optical

IEC958 input: Coaxial
IEC958 output: Coaxial only
IEC958 quality: Consumer
IEC958 emphasis: off
IEC958 Dolby: off
IEC958 sample rate: 48000

ADAT Sample rate: 48000Hz
ADAT1: Sync
ADAT2: No Lock
ADAT3: No Lock

Timecode signal: no
Punch Status:

 1: off  2: off  3: off  4: off  5: off  6: off  7: off  8: off 
 9: off 10: off 11: off 12: off 13: off 14: off 15: off 16: off 
17: off 18: off 19: off 20: off 21: off 22: off 23: off 24: off 
25: off 26: off

---

### Post by Pablo_F on 2010-03-21
Which module does it use?

cat /proc/asound/modules

---

### Post by fso_ on 2010-03-23
this is the output:

mark@noname:~$ cat /proc/asound/modules
 0 snd_rme9652
mark@noname:~$

---

### Post by fso_ on 2010-03-23
and this is what hdspconf says:

mark@noname:~$ hdspconf

HDSPConf 1.4 - Copyright (C) 2003 Thomas Charbonnel <thomas@undata.org>
This program comes WITH ABSOLUTELY NO WARRANTY
HDSPConf is free software, see the file copying for details

Looking for HDSP cards :
Card 0 : RME Digi9652 (Rev 1.5) at 0xef000000, irq 18
Card 1 : CreamWare GmbH CreamWare Noah Synthesizer at usb-0000:00:1d.1-2, full speed
Card 2 : BEHRINGER BCR2000 at usb-0000:00:1d.0-1, full speed
No Hammerfall DSP card found.
mark@noname:~$

---

### Post by fso_ on 2010-03-23
OK, i think i have found a solution, how to control the DIGI 96 Series Card, like set Wordclock Master, SynchSorce and what ever...

I have just type in the Terminal "amixer"... id did outputt me all the current settings...
When u type "amixer -help" u can see that u can change certain Options via the command line... probably just have to work my way through all the options...

this is how it looks, i am sure this is the solution... well gui would be more nice, but at least i can set the RME 9636 / 9652 to Wordclock Master this Way:

mark@noname:~$ **amixer**
Simple mixer control 'IEC958 Input Connector',0
  Capabilities: enum
  Items: 'ADAT1' 'Coaxial' 'Internal'
  Item0: 'Coaxial'
Simple mixer control 'IEC958 Output also on ADAT1',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Sample Rate',0
  Capabilities: volume volume-joined
  Playback channels: Mono
  Capture channels: Mono
  Limits: 0 - 96000
  Mono: 48000 [50%]
Simple mixer control 'ADAT1 Input Source',0
  Capabilities: enum
  Items: 'ADAT1' 'Internal'
  Item0: 'ADAT1'
Simple mixer control '**ADAT1 Sync Check',0**
  Capabilities: enum
  Items: 'No Lock' 'Lock' 'No Lock Sync' 'Lock Sync'
  Item0: 'Lock Sync'
Simple mixer control 'ADAT2 Sync Check',0
  Capabilities: enum
  Items: 'No Lock' 'Lock' 'No Lock Sync' 'Lock Sync'
  Item0: 'No Lock'
Simple mixer control 'ADAT3 Sync Check',0
  Capabilities: enum
  Items: 'No Lock' 'Lock' 'No Lock Sync' 'Lock Sync'
  Item0: 'No Lock'
Simple mixer control 'Channels Thru',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right - Rear Center - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ? - ?
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
  Rear Left: Playback [off]
  Rear Right: Playback [off]
  Front Center: Playback [off]
  Woofer: Playback [off]
  Side Left: Playback [off]
  Side Right: Playback [off]
  Rear Center: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
  ?: Playback [off]
Simple mixer control 'Passthru',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
[B]Simple mixer control 'Preferred Sync Source',0
  Capabilities: enum
  Items: 'IEC958 In' 'ADAT1 In' 'ADAT2 In' 'ADAT3 In'
  Item0: 'ADAT1 In'
Simple mixer control 'Sync Mode',0
  Capabilities: enum
  Items: 'AutoSync' 'Master' 'Word Clock'
  Item0: 'AutoSync'
Simple mixer control 'Timecode Valid',0
  Capabilities: pswitch pswitch-joined[/B]
  Playback channels: Mono
  Mono: Playback [off]


mark@noname:~$ **amixer -?**
amixer: invalid option -- '?'
Invalid switch or option needs an argument.
Usage: amixer <options> [command]

**Available options:**
  -h,--help       this help
  -c,--card N     select the card
  -D,--device N   select the device, default 'default'
  -d,--debug      debug mode
  -n,--nocheck    do not perform range checking
  -v,--version    print version of this program
  -q,--quiet      be quiet
  -i,--inactive   show also inactive controls
  -a,--abstract L select abstraction level (none or basic)
  -s,--stdin      Read and execute commands from stdin sequentially

**Available commands:**
  scontrols       show all mixer simple controls
  scontents      show contents of all mixer simple controls (default command)
  sset sID P      set contents for one mixer simple control
  sget sID        get contents for one mixer simple control
  controls        show all controls for given card
  contents        show contents of all controls for given card
  cset cID P      set control contents for one control
  cget cID        get control contents for one control

---

