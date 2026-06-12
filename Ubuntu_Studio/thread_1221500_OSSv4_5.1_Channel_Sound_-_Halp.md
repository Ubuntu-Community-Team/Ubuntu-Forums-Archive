---
title: "OSSv4 5.1 Channel Sound - Halp"
date: 2009-07-23
forum: Ubuntu Studio
---

### Post by tehkane on 2009-07-23
I posted this on the 4Front support forum but I haven't yet got a reply. IRC people haven't been able to solve the problem as well >.<

Decided to switch from ALSA to OSSv4 yesterday and I'm having me some problems getting 5.1 audio. Stereo sound on front two speakers works, though. So everything installed fine. 
 
When running osstest: 
   Front two speakers output audio through left and right
   Rear speakers output through PCM4 
   Center and Sub output through Center/LFE 
 
So the speakers work, I'm just not getting 5.1 sound when, for example, playing music in Audacious or VLC. A guy on IRC linked me to a 6 channel audio file (identifies speakers to help with setup) that I launched with MPlayer. That resulted in my front speakers outputting correctly and my center/sub outputting what was supposed to be sent to the rear speakers. Rear speakers did nothing.

So according to osstest, my speakers work (though, rear speakers come from PCM4 instead of the supposed rear channels) I just can't get applications to them all :/

Any ideas?

The guide I followed to install was: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
Though, when I got to this part:
> Be sure to set System -> Preferences -> Sound to use the OSS/4 "sinks". You may have to restart GNOME for this option to appear.I had no sinks option...
gst-plugins-bad is installed, before you ask :P
> kane@kane-desktop:~$ dpkg -l gstreamer0.10-plugins-bad
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  gstreamer0.10- 0.10.11-2ubunt GStreamer plugins from the "bad" set[quote="ossinfo -v3"]
kane@kane-desktop:~$ ossinfo -v3
Version info: OSS 4.1 (b 1052/200903240621) (0x00040100) 
Platform: Linux/x86_64 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 (kane-desktop)

Number of audio devices:    10
Number of audio engines:    14
Number of mixer devices:    1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 ATI HD Audio interrupts=5593043 (5669153)
    HD Audio controller ATI HD Audio
    Vendor ID    0x10024383
    Subvendor ID 0x1458a022
     Codec  0: ALC885 (0x10ec0885/0x1458a002)
 2: oss_usb0 USB audio core services


Mixer devices
 0: High Definition Audio ALC885 (Mixer 0 of device object 1)
    Device file /dev/oss/oss_hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps: 
    Device handle: PCIa0221458-0000:00:14.2-mx01
    Device priority: 10


Audio devices
HD Audio play front               /dev/oss/oss_hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      Out engine  1: 0/HD Audio play front
                     Available for use 
      Engine      2: 10/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au01
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 8
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play rear                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 1/HD Audio play rear
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au02
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play center/LFE          /dev/oss/oss_hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 2/HD Audio play center/LFE
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au03
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play side                /dev/oss/oss_hdaudio0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 3/HD Audio play side
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au04
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play pcm4                /dev/oss/oss_hdaudio0/pcm4  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 4/HD Audio play pcm4
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au05
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio play spdif-out           /dev/oss/oss_hdaudio0/spdout0  (device index 5)
    Legacy device /dev/dsp5
    Caps: TRIGGER MMAP 
    Modes: OUTPUT 
      Out engine  1: 5/HD Audio play spdif-out
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au06
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,88200,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin0  (device index 6)
    Legacy device /dev/dsp6
    Caps: DUPLEX TRIGGER MMAP 
    Modes: IN/OUT 
      In engine   1: 6/HD Audio rec mix
                     Available for use 
      Engine      2: 10/HD Audio play front (vmix)
                     Available for use 
      Engine      3: 11/HD Audio play front (vmix)
                     Available for use 
      Engine      4: 12/HD Audio play front (vmix)
                     Available for use 
      Engine      5: 13/HD Audio play front (vmix)
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au07
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin1  (device index 7)
    Legacy device /dev/dsp7
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 7/HD Audio rec mix
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au08
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec mix                  /dev/oss/oss_hdaudio0/pcmin2  (device index 8)
    Legacy device /dev/dsp8
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 8/HD Audio rec mix
                     Available for use 
    Input formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001010):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au09
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated

HD Audio rec spdifin              /dev/oss/oss_hdaudio0/spdin0  (device index 9)
    Legacy device /dev/dsp9
    Caps: TRIGGER MMAP 
    Modes: INPUT  
      In engine   1: 9/HD Audio rec spdifin
                     Available for use 
    Input formats (0x00001410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE    - 32 bit signed little endian
    Output formats (0x00001410):
      AFMT_S16_LE    - 16 bit signed little endian
      AFMT_AC3        - AC3 (Dolby Digital) encoded audio
      AFMT_S32_LE    - 32 bit signed little endian
    Device handle: PCIa0221458-0000:00:14.2-au10
    Related mixer dev: 0
    Sample rate source: 0
    Preferred channel configuration: Not indicated
    Supported number of channels (min - max): 2 - 2
    Native sample rates (min - max): 44100 - 192000 (44100,48000,96000,192000)
    HW Type: Not indicated.
    Minimum latency: Not indicated
[/quote]

[quote="ossmix"]
kane@kane-desktop:~$ ossmix
Selected mixer 0/High Definition Audio ALC885
Known controls are:
jack.green.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.green [<leftvol>:<rightvol>] (currently 19.9:19.9 dB)
jack.green.mute ON|OFF (currently OFF)
jack.black.mode <front|rear|center/LFE|side|pcm4|input> (currently pcm4)
jack.black [<leftvol>:<rightvol>] (currently 19.9:19.9 dB)
jack.black.mute ON|OFF (currently OFF)
jack.orange.mode <front|rear|center/LFE|side|pcm4|input> (currently center/LFE)
jack.orange [<leftvol>:<rightvol>] (currently 19.9:19.9 dB)
jack.orange.mute ON|OFF (currently OFF)
jack.gray.mode <front|rear|center/LFE|side|pcm4|input> (currently pcm4)
jack.gray [<leftvol>:<rightvol>] (currently 19.9:19.9 dB)
jack.gray.mute ON|OFF (currently OFF)
jack.pink.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.pink [<leftvol>:<rightvol>] (currently 19.9:19.9 dB)
jack.pink.mute ON|OFF (currently OFF)
jack.fp-pink.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.fp-pink [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.fp-pink.mute ON|OFF (currently OFF)
jack.blue.mode <front|rear|center/LFE|side|pcm4|input> (currently input)
jack.blue [<leftvol>:<rightvol>] (currently 19.9:19.9 dB)
jack.blue.mute ON|OFF (currently OFF)
jack.fp-green.mode <front|rear|center/LFE|side|pcm4|input> (currently front)
jack.fp-green [<leftvol>:<rightvol>] (currently 19.9:19.9 dB)
jack.fp-green.mute ON|OFF (currently OFF)
record.mix.mute.mic1 ON|OFF (currently OFF)
record.mix.mute.fp-mic1 ON|OFF (currently OFF)
record.mix.mute.linein1 ON|OFF (currently OFF)
record.mix.mute.fp-headphone1 ON|OFF (currently OFF)
record.mix.mute.green1 ON|OFF (currently OFF)
record.mix.mute.black1 ON|OFF (currently OFF)
record.mix.mute.orange1 ON|OFF (currently OFF)
record.mix.mute.gray1 ON|OFF (currently OFF)
record.mix.mute.input-mix1 ON|OFF (currently OFF)
record.mix1 [<leftvol>:<rightvol>] (currently 20.9:20.9 dB)
record.mix.mute.mic2 ON|OFF (currently OFF)
record.mix.mute.fp-mic2 ON|OFF (currently OFF)
record.mix.mute.linein2 ON|OFF (currently OFF)
record.mix.mute.fp-headphone2 ON|OFF (currently OFF)
record.mix.mute.green2 ON|OFF (currently OFF)
record.mix.mute.black2 ON|OFF (currently OFF)
record.mix.mute.orange2 ON|OFF (currently OFF)
record.mix.mute.gray2 ON|OFF (currently OFF)
record.mix.mute.input-mix2 ON|OFF (currently OFF)
record.mix2 [<leftvol>:<rightvol>] (currently 23.9:23.9 dB)
record.mix.mute.mic3 ON|OFF (currently OFF)
record.mix.mute.fp-mic3 ON|OFF (currently OFF)
record.mix.mute.linein3 ON|OFF (currently OFF)
record.mix.mute.fp-headphone3 ON|OFF (currently OFF)
record.mix.mute.green3 ON|OFF (currently OFF)
record.mix.mute.black3 ON|OFF (currently OFF)
record.mix.mute.orange3 ON|OFF (currently OFF)
record.mix.mute.gray3 ON|OFF (currently OFF)
record.mix.mute.input-mix3 ON|OFF (currently OFF)
record.mix3 [<leftvol>:<rightvol>] (currently 20.9:20.9 dB)
misc.mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.fp-mic [<leftvol>:<rightvol>] (currently 31.4:31.4 dB)
misc.linein [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.fp-headphone [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.green [<leftvol>:<rightvol>] (currently 26.9:26.9 dB)
misc.black [<leftvol>:<rightvol>] (currently 22.4:22.4 dB)
misc.orange [<leftvol>:<rightvol>] (currently 22.4:22.4 dB)
misc.gray [<leftvol>:<rightvol>] (currently 22.4:22.4 dB)
misc.input-mix <mic|fp-mic|linein> (currently mic)
misc.front-mute ON|OFF (currently OFF)
misc.input-mix-mute1 ON|OFF (currently OFF)
misc.front1 [<leftvol>:<rightvol>] (currently 44.9:44.9 dB)
misc.front2 <front|input-mix> (currently front)
misc.rear-mute ON|OFF (currently OFF)
misc.input-mix-mute2 ON|OFF (currently OFF)
misc.rear1 [<leftvol>:<rightvol>] (currently 37.9:37.9 dB)
misc.rear2 <rear|input-mix> (currently rear)
misc.center/lfe-mute ON|OFF (currently OFF)
misc.input-mix-mute3 ON|OFF (currently OFF)
misc.center/lfe1 [<leftvol>:<rightvol>] (currently 39.9:39.9 dB)
misc.center/lfe2 <center/LFE|input-mix> (currently center/LFE)
misc.side-mute ON|OFF (currently OFF)
misc.input-mix-mute4 ON|OFF (currently OFF)
misc.side1 [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
misc.side2 <side|input-mix> (currently side)
misc.pcm4-mute ON|OFF (currently OFF)
misc.input-mix-mute5 ON|OFF (currently OFF)
misc.pcm41 [<leftvol>:<rightvol>] (currently 28.9:28.9 dB)
misc.pcm42 <pcm4|input-mix> (currently pcm4)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Multich)
vmix0-src <Fast|Low|Medium|High|High+|Production|OFF> (currently High)
vmix0-outvol <monovol> (currently 25.0 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm10 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm11 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm12 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm13 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
[/quote]

Ideas?

---

### Post by tehkane on 2009-07-25
Shameless self-bump...
Really getting sick of stereo output >.<

Anyone?

---

### Post by martinbaselier on 2009-07-26
You might need to change some settings to your driver.

First check what your driver is : 
**lsmod | grep oss**

in my case this is:
oss_usb
oss_hdaudio -> this is my soundcard
osscore

**modinfo oss_hdaudio** shows the parameters I can add to it.

now create a config file:

**sudo gedit /etc/modprobe.d/hdaudio.conf**

Since I have a laptop I disabled all extra channels, so they don't show up in the mixer:

options oss_hdaudio hdaudio_jacksense=1

Hope this helps.

---

### Post by alecmg on 2009-11-09
I'm having same problem with OSS: stereo sound plays only through front speakers.
Problem with wrong channels to wrong speakers was easily solved in ossxmix
And sources with surround sound (movies) play perfectly using all channels.
But usual mp3 files are not upmixed and sound really lame without subwoofer.

So how do we enable upmix of stereo to 5.1?

---

### Post by c-shadow on 2009-12-18
Same problem here. Anyone found any info on stereo upmix to 5.1?

---

