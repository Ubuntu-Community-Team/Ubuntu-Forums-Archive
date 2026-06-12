---
title: "Ubuntu 9.10 with Studio, Audiophile 2496, big problems..."
date: 2010-04-16
forum: Ubuntu Studio
---

### Post by cissiny on 2010-04-16
Hi all,

I am new here and I hope that it is ok that I post about this even though similar threads do exist. None of them seems to help me anyway? I've been working with this for a couple of days (and nights) and searched all over the net for a solution. So far, I just can not get the audio to work in our studio computer... Right now, I've "lost" the card again after doing some things discussed here [http://linuxmusicians.com/viewtopic.php?f=4&t=2256](http://linuxmusicians.com/viewtopic.php?f=4&t=2256) (i.e. adding the username to the group audio and editing limits.conf). I think that I must reinstall Ubuntu 9.10 and the Studio package, will do that tomorrow.

First of all - this is our old but very much used studio computer. I am not a musician, my fiance is (pro since many years) but as I have much more experience with Ubuntu than he has it is sort of up to me to get this working. We use to have XP on the computer, has been very buggy the last months. Upgraded the memory (now we have 3 GB, 2 GB is from new OCZ Platinum RAM memory). Then we installed 9.10 and the Studio package. The sound card is an M-Audio Audiophile 2496.

At first, we could not find the sound card at all. I searched on the net and found out that it might be that Pulseaudio did not work with 9.10 and that soundcard. Uninstalled Pulseaudio and got some limited sound (on youtube and also midi-files in Rosegarden, not Rosegarden's own files though). As I am Swedish, I asked for some advice at Swedish forums. I reinstalled Pulseaudio (card disappeared and so did the little sound we had), did some workarounds (I'd be happy to link to those) and finally got partial sound back (only youtube, not midi). 

Then I searched the net again, and tried the above mentioned solution with the group audio and the document limits.conf. That was to try to get Jack audio server up and running. It only resulted in the sound card disappearing again and I have not been able to fix that again...

So, I'm thinking of reinstalling Ubuntu 9.10 tomorrow. Plus the Studio package. The thing is, my fiance is sort of upside down since he can not use the studio. First of all, we must get the connection from his instrument (electric bass) to mixer to sound card working. Just so that he can hear the bass through the speakers. Everything is wired just as it was with XP. I don't know if it's just some settings or if something else is missing?

Any clues? I would be very happy to post output from commands, links to what I have tried etc.

Thanks a lot in advance for any ideas!

Best wishes,

Cissi in Sweden

---

### Post by cchhrriiss121212 on 2010-04-17
I have a card with the same chipset and pulse does not work very well with it, it is a known bug and has been so for a while. But once set up with jack+alsa they are great to use. I should also say that re-installing should not be necessary right now.
 
As you upgraded to studio, you should have two kernels installed. The studio package comes with the rt kernel which is what you want to use for work with jack. You can set it as default with startup manager, which is in synaptic.

Could you post what the terminal command "aplay -l" gives?

---

### Post by sgx on 2010-04-17
Hi, in qjackctl, click the setup button on the main screen, then in the middle-far-right of the setup screen, by 

Input device  >
Output device >

click the > widget to see your soundchips/cards, and select either
ice_1712 multi, or Maudio 24/96, both are part of your soundcard. See which works best.

Type   lsmod   in a terminal, this will list kernel modules, the m-audio sound chip, labeled snd_ice1712 in linux, will be in the list, perhaps several times, in lines that may look like this:

snd_intel8x0           30208  2 
snd_ice1712            58820  1 
snd_ice17xx_ak4xxx      3780  1 snd_ice1712
snd_ak4xxx_adda         8452  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              8356  1 snd_ice1712
snd_ac97_codec        102664  2 snd_intel8x0,snd_ice1712
ac97_bus                1668  1 snd_ac97_codec
snd_i2c                 5508  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         7364  1 snd_ice1712
snd_rawmidi            23200  1 snd_mpu401_uart
snd_seq_dummy           2760  0 
snd_seq_oss            32032  0 
snd_seq_midi_event      7300  1 snd_seq_oss
snd_seq                54992  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          7312  4 snd_rawmidi,snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            44768  0 
snd_pcm                82760  4 snd_intel8x0,snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_timer              22188  2 snd_seq,snd_pcm
snd_mixer_oss          16644  1 snd_pcm_oss
snd                    62756  21 snd_intel8x0,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
snd_page_alloc          9228  2 snd_intel8x0,snd_pcm
soundcore               8192  1 snd

the motherboard soundchip, snd_intel8x0 in my case, and ice1712 from the m-audio card may compete for access to the sad hodgepodge of linux audio implementations presented in most linux distros, so you can shut off the motherboard sound in the computer bios setup, or create a textfile named blacklist in

/etc/modprobe.d

containing just the name of your motherboard sound module, as displayed by lsmod. If blacklist already  exists, just add a new line to it, and resave it.

Cheers

---

### Post by cissiny on 2010-04-17
Thanks cchhrriiss and sgx!

I think a new install is needed, I messed up when trying to get Jack to work, haven't been able to find the soundcard since then...

aplay -l gives
```
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: ICH5 [Intel ICH5], enhet 0: Intel ICH [Intel ICH5]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: ICH5 [Intel ICH5], enhet 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

```

(Use to be audiophile as 0 and the others as 1)

lsmod gives:
```
Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30104  0 
snd_ac97_codec        101504  1 snd_intel8x0
snd_pcm_oss            37312  0 
snd_mixer_oss          16220  1 snd_pcm_oss
snd_pcm                76416  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
ac97_bus                1532  1 snd_ac97_codec
snd_i2c                 5020  0 
snd_seq_oss            29280  0 
snd_mpu401_uart         7196  0 
usblp                  12636  0 
iptable_filter          3100  0 
snd_seq_midi            6624  0 
ip_tables              11692  1 iptable_filter
snd_rawmidi            22336  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ppdev                   6688  0 
snd_seq                51088  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               16544  1 ip_tables
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             31940  1 
lp                      8964  0 
shpchp                 32272  0 
parport                35340  3 ppdev,parport_pc,lp
snd                    61188  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_i2c,snd_seq_oss,snd_mpu401_uart,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               5280  0 
soundcore               7264  1 snd
snd_page_alloc          9060  2 snd_intel8x0,snd_pcm
joydev                 10240  0 
usbhid                 38208  0 
usb_storage            52768  2 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
floppy                 54916  0 
e100                   32420  0 
mii                     5212  1 e100
intel_agp              27676  1 
agpgart                34988  1 intel_agp

```

So, I've messed up... I'll reinstall and come back after that! :)

Thanks for the input!

Best wishes,
Cissi

---

### Post by rac9876 on 2010-04-19
I have an M-Audio Audiophile 24/96 too. PulseAudio didn't work for me with the default install of Ubuntu 10.04 (either regular version or Ubuntu Studio) either. The problem seems to have been that the sound card's analogue inputs and outputs weren't understood by PulseAudio. I fixed it by using [the instructions in comment #119]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/178442/comments/119") under [bug #178442]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/178442").

---

### Post by bohemier on 2010-05-11
> **rac9876 said:**
> I have an M-Audio Audiophile 24/96 too. PulseAudio didn't work for me with the default install of Ubuntu 10.04 (either regular version or Ubuntu Studio) either. The problem seems to have been that the sound card's analogue inputs and outputs weren't understood by PulseAudio. I fixed it by using [the instructions in comment #119]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/178442/comments/119") under [bug #178442]("https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/178442").

Hello rac9876,

I can't make it work with those instructions... I inserted this line in /lib/udev/rules.d/90-pulseaudio.rules

```
SUBSYSTEMS=="pci", ATTRS{vendor}=="0x1412", ATTRS{device}=="0x1712", ATTRS{subsystem_vendor}=="0x1412", ATTRS{subsystem_device}=="0xd634", ENV{PULSE_PROFILE_SET}="m_audio-audiophile-2496.conf" 
```

and created the file /usr/share/pulseaudio/alsa-mixer/profile-sets/m_audio-audiophile-2496.conf with this contents:

```
# This file is part of PulseAudio. 
# 
# PulseAudio is free software; you can redistribute it and/or modify 
# it under the terms of the GNU Lesser General Public License as 
# published by the Free Software Foundation; either version 2.1 of the 
# License, or (at your option) any later version. 
# 
# PulseAudio is distributed in the hope that it will be useful, but 
# WITHOUT ANY WARRANTY; without even the implied warranty of 
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU 
# General Public License for more details. 
# 
# You should have received a copy of the GNU Lesser General Public License 
# along with PulseAudio; if not, write to the Free Software Foundation, 
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA. 
 
; M-Audio Delta Audiophile 2496 
; 
; This card, based on the Via ICE1712 chipset, has two stereo audio channels 
; (1 in and 1 out) and a separate S/PDIF digital stereo channel. Like with 
; all ICE1712-based cards, this is exposed by ALSA as a single 10-channel 
; device with some of the channels not connected. 
; 
; 
; See default.conf for an explanation on the directives used here. 
 
[General] 
auto-profiles = no 
 
[Mapping analog-stereo-in] 
description = Analog Stereo Input 
device-strings = hw:%f,0 
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9 
direction = input 
 
[Mapping analog-stereo-out] 
description = Analog Stereo Output 
device-strings = hw:%f,0 
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7 
direction = output 
 
[Mapping analog-digital-stereo-out] 
description = Analog/Digital Stereo Output 
device-strings = hw:%f,0 
channel-map = front-left,front-right,aux0,aux1,aux2,aux3,aux4,aux5,front-left,front-right 
direction = output 
 
[Mapping digital-stereo-out] 
description = Digital Stereo Output 
device-strings = hw:%f,0 
channel-map = aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,front-left,front-right 
direction = output 
 
[Mapping digital-stereo-in] 
description = Digital Stereo Input 
device-strings = hw:%f,0 
channel-map = aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,front-left,front-right,aux8,aux9 
direction = input 
 
 
[Profile output:stereo] 
description = Analog Stereo Output 
output-mappings = analog-stereo-out 
input-mappings = 
priority = 80 
skip-probe = yes 
 
[Profile output:stereo-da+input:stereo-analog] 
description = Analog Stereo Input/Output 
output-mappings = analog-stereo-out 
input-mappings = analog-stereo-in 
priority = 100 
skip-probe = yes 
 
[Profile output:stereo-da+input:stereo-analog] 
description = Analog Stereo Input/Output, Digital Stereo Output 
output-mappings = analog-digital-stereo-out 
input-mappings = analog-stereo-in 
priority = 90 
skip-probe = yes 
 
[Profile output:spdif] 
description = Digital Stereo Output (Analog Disabled) 
output-mappings = digital-stereo-out 
input-mappings =  
priority = 60 
skip-probe = yes 
 
[Profile output:spdif+input:spdif] 
description = Digital Stereo Input/Output (Analog Disabled) 
output-mappings = digital-stereo-out 
input-mappings = digital-stereo-in 
priority = 70 
skip-probe = yes 
 
```

Then rebooted... Now, my 2496 is not listed anymore under hardware, in  sound preferences whereas before I had only the digital outputs listed.

I wonder if this is due to improper rules in /lib/udev/rules.d/90-pulseaudio.rules... I noticed the format is different from what is already there:

```
SUBSYSTEMS=="usb", ATTRS{idVendor}=="17cc", ATTRS{idProduct}=="1978", ENV{PULSE_PROFILE_SET}="native-instruments-audio8dj.conf"
SUBSYSTEMS=="usb", ATTRS{idVendor}=="17cc", ATTRS{idProduct}=="0839", ENV{PULSE_PROFILE_SET}="native-instruments-audio4dj.conf"
SUBSYSTEMS=="usb", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="2012", ENV{PULSE_PROFILE_SET}="maudio-fasttrack-pro.conf"

```

TIA

---

### Post by bohemier on 2010-05-12
Allright! I was able to make it work with this: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/63)

---

