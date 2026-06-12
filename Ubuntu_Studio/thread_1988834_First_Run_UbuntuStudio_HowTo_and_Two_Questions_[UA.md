---
title: "First Run: UbuntuStudio HowTo and Two Questions [UART, Yoshimi]"
date: 2012-05-28
forum: Ubuntu Studio
---

### Post by tehowe on 2012-05-28
I'd held back for a while waiting for [the UbuntuStudioPreparation Wiki]("https://help.ubuntu.com/community/UbuntuStudioPreparation") to get updated and now that some work's been done there for Precise (thanks, ttoine!) I took the plunge.

The good/great news is I was able to get jack/studio functionality running by cherry picking the following commands from that page - since I want to run Ubuntu Studio via Unity or Cinnamon and also enjoy the security of a LUKS encrypted partition I wasn't able to simply install Precise UbuntuStudio, so I had to take this approach

```
sudo apt-get install vlc ubuntu-restricted-extras ubuntustudio-menu

sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring

sudo apt-get --quiet update && sudo apt-get --yes --quiet upgrade

sudo apt-get install alsa-firmware-loaders alsa-tools alsa-tools-gui alsa-firmware

sudo apt-get install linux-lowlatency linux-headers-lowlatency

sudo apt-get install pulseaudio-module-jack

sudo apt-get install qjackctl
```The only wrinkle is that I have to hold the SHIFT key on startup as soon as the bios screen comes up in order to reveal the GRUB menu, otherwise there is choice to select the lowlatency kernel and Ubuntu just boots with the latest generic kernel. I suppose I'll have to learn how to edit GRUB in order to get this to load the linux-lowlatency kernel consistently.

I've also installed amsynth and am testing with my E-Mu XBoard25 controller and an ALSA virtual keyboard

```
sudo apt-get install amsynth
sudo apt-get install vkeybd
```Things sound good via the E-MU controller or the virtual keyboard.

So now two questions/problems.

1. Yoshimi has no instruments and finding any online appears to be a trade secret. I can install and use ZynAddSubFX but if Yoshimi's so much better for connectivity how do I get a sound out of it?

2. Also, I have a Juno-106 hooked into my Audigy Soundblaster drive, which comes up in JACK with two selections for readable clients

0:Audigy MPU-401 (UART)
32:Audigy MPU-401 #2

Neither of these will pass any MIDI data when hooked up (under the ALSA tab) to either ZynAddSubFX or Amsynth. What do I need to tweak to get my larger keyboard feeding MIDI data to softsynths via JACK?

---

### Post by sgx on 2012-05-28
Hi, yoshimi uses the same zynaddsubfx sounds, link or copy
the 'banks' in the folder from /usr/share/zynaddsubfx to
the same location yoshimi folder.

More banks and individual sounds are here:

[http://www.kvraudio.com/banks.php?s=list&what=1187&format=&order=date](http://www.kvraudio.com/banks.php?s=list&what=1187&format=&order=date)

There is also a forum, that may provide answers from crossover
lin/win users

[http://www.kvraudio.com/forum/viewforum.php?f=47](http://www.kvraudio.com/forum/viewforum.php?f=47)

There are collections from Folderol, Cormi, Laba170 and Adriano Petrosillo,
and the Author himself, in case you, or anyone have missed them. They work in Yoshimi also.

[www.kvraudio.com/banks.php?s=dl&id=1365](www.kvraudio.com/banks.php?s=dl&id=1365)
[www.kvraudio.com/banks.php?s=dl&id=1455](www.kvraudio.com/banks.php?s=dl&id=1455)
[www.kvraudio.com/banks.php?s=dl&id=1285](www.kvraudio.com/banks.php?s=dl&id=1285)

For this next one below, paste the link in your browser,
when the screen fills with data, use the 'save page as' option.

[http://www.gospel.bo.it/albums/userpics/10222/Adriano_Petrosillo_Banks_-_06-Nov-09_tar.gz](http://www.gospel.bo.it/albums/userpics/10222/Adriano_Petrosillo_Banks_-_06-Nov-09_tar.gz)

extract it twice, and you get a 240K folder, named
Adriano Petrosillo, copy it
to your Banks folder

Paul Nasca, zynaddsubfx author has provided 180 sounds in this archive:

unsorted_zynaddsubfxParameters20060615.zip found here:

[http://zynaddsubfx.sourceforge.net/doc/instruments](http://zynaddsubfx.sourceforge.net/doc/instruments)

Use the 'open parameters' menu to load these multi-timbral patches,
not the banks! Place the expanded archive a separate folder, (named like aaa-zyn so it's first in the file requester), in
/usr/share/zynaddsubfx

some fabulous sounds are in there, so rename them to your needs!
Save your new creations with menu 'save parameters'.

---

### Post by sgx on 2012-05-28
> **tehowe said:**
> 
0:Audigy MPU-401 (UART)
32:Audigy MPU-401 #2

Neither of these will pass any MIDI data when hooked up (under the ALSA tab) to either ZynAddSubFX or Amsynth. What do I need to tweak to get my larger keyboard feeding MIDI data to softsynths via JACK?
see what commands reveal
aconnect -o
aconnect -i
arecord -l
aplay -l

items in quotes or brackets can go in the Setup page settings at

Input Device >
Output Device >

click the >   to see if there are any matches, if not,
you can replace hw: items with those from the command outputs.

usb midi, and 5pin midi can defeat each other in some cases,
sometimes you cannot use both at once. You might try daisychaining
the Juno to the e-mu.

The midi out on the xboard can change to midi thru, and 
'local on/off' option should be considered, both checked
in the xboard manual

[http://www.kvraudio.com/forum/printview.php?t=114355&start=0](http://www.kvraudio.com/forum/printview.php?t=114355&start=0)

an old discussion of Virus with xboard, instead of Juno.
Cheers

---

### Post by tehowe on 2012-05-29
> **sgx said:**
> see what commands reveal
aconnect -o
aconnect -i
arecord -l
aplay -l


Thanks sgx for pointing out those sounds and for the MIDI tips

Here's what I got by entering those commands

```
me@here:~$ aconnect -o
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'E-MU Xboard25' [type=kernel]
    0 'E-MU Xboard25 MIDI 1'
client 24: 'SB Audigy 1 [SB0090]' [type=kernel]
    0 'Audigy MPU-401 (UART)'
   32 'Audigy MPU-401 #2'
client 25: 'Emu10k1 WaveTable' [type=kernel]
    0 'Emu10k1 Port 0  '
    1 'Emu10k1 Port 1  '
    2 'Emu10k1 Port 2  '
    3 'Emu10k1 Port 3  '
client 130: 'FLUID Synth (4587)' [type=user]
    0 'Synth input port (4587:0)'

me@here:~$ aconnect -i
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 20: 'E-MU Xboard25' [type=kernel]
    0 'E-MU Xboard25 MIDI 1'
client 24: 'SB Audigy 1 [SB0090]' [type=kernel]
    0 'Audigy MPU-401 (UART)'
   32 'Audigy MPU-401 #2'

me@here:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 2: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0090]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

me@here:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audigy [SB Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 2: Audigy [SB Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Audigy [SB Audigy 1 [SB0090]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I noticed I can send to the Juno but not receive... so at least the cables are in right :)

I disconnected the XBoard and restarted JACK, then connected the Audigy drive to Qsynth to see if the ALSA USB MIDI device was interfering, but that didn't work.

Fire up the Xboard and connect it and it works ok. Huh. I'll test the Juno's send cable and try your daisychain suggestion.

---

### Post by sgx on 2012-05-30
Forgot to mention using command

a2jmidid -j default

to start the jackd midi port for yoshimi and other instruments.
Alsa midi works fine on many, but not all, and if your qjackctl
Alsa tab shows midi-through in and out ports, cross connect those
to each other, cables drawing a big X   
:guitar:

---

### Post by tehowe on 2012-06-08
> **sgx said:**
> Forgot to mention using command

a2jmidid -j default

to start the jackd midi port for yoshimi and other instruments.
Alsa midi works fine on many, but not all, and if your qjackctl
Alsa tab shows midi-through in and out ports, cross connect those
to each other, cables drawing a big X   
:guitar:

That's great, it's up and running now. Thanks sgx for pointing me in the right direction. 

MIDI on the Audigy doesn't seem to want to work, _however_ it's possible to send MIDI from Ardour3 (or another DAW) through the XBoard to the Juno as suggested, routing around the (unsupported?) Soundcard MIDI. I can't use the 88-key JUNO as a controller though, the MIDI only goes one way.

The correct procedure to switch the XBoard's MIDI Out to MIDI Thru is

Press Edit
Press the key labeled X1 (C#')
Move the Data Entry Slider so the LED screen reads 'Mid'
Press Enter
Move the Data Entry Slider so the LED screen reads 'tHr'

For the curious, here's what the system configuration looks like when things are working as they should.

[IMG]http://i.imgur.com/7HgUS.png[/IMG]

---

### Post by sgx on 2012-06-09
with the e-mu and juno unplugged, run the commands
aconnect -i
aconnect -o

and look for audigy midi hints, it may say
mpu401, e-mu10k or ?

then plug in the other gear one by one,
run the same commands and compare the same output,
to clarify which Creative Labs items are which.

command lsmod, should have a clump looking a bit
like this, which was an older ubuntu, and an audigy R4

snd_emu10k1_synth 14464 0
snd_emux_synth 41344 1 snd_emu10k1_synth
snd_seq_virmidi 13568 1 snd_emux_synth
snd_seq_midi_emul 14592 1 snd_emux_synth
snd_emu10k1 146208 6 snd_emu10k1_synth
snd_ac97_codec 111652 1 snd_emu10k1
ac97_bus 9856 1 snd_ac97_codec
snd_pcm_oss 46848 0
snd_mixer_oss 22784 1 snd_pcm_oss
snd_pcm 83204 4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc 16136 2 snd_emu10k1,snd_pcm
snd_util_mem 12416 2 snd_emux_synth,snd_emu10k1
snd_hwdep 15236 2 snd_emux_synth,snd_emu10k1

Glad things are working better. Thats a whole lot a cables!
Cheers

---

