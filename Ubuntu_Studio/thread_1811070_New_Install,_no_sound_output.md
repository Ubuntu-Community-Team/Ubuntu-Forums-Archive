---
title: "New Install, no sound output"
date: 2011-07-24
forum: Ubuntu Studio
---

### Post by chrisrodgers on 2011-07-24
Hi!  I am very new to Ubuntu and all of the Ubuntu Studio components.  I installed Ubuntu Studio on my PC (full install on a new hard drive, installed all packages).  I mounted a windows drive that has some mp3s on it and tried to play one with Audacious.  I see the bars going up and down as the song is playing, but I am not getting any sound out of my speakers.  

I assume there is more setup for me to do.  Any pointers to where I can start?

When I installed, I made my user part of the audio group.  I am using the onboard sound from the motherboard.  Reading a few of the threads here, I see that some info might be helpful:

> chris@dumbo-PC:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
chris@dumbo-PC:~$ cat /proc/asound/cards /proc/asound/modules /proc/asound/version ~/.asoundrc
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd02a0000 irq 48
 0 snd_hda_intel
Advanced Linux Sound Architecture Driver Version 1.0.23.
cat: /home/chris/.asoundrc: No such file or directory
chris@dumbo-PC:~$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 3/3
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chris@dumbo-PC:~$ 
My main goal with this setup will be to make voice recordings and remix music.  Can an Mbox 2 Mini be used for mic in?

---

### Post by ~!geek!~ on 2011-07-24
Don't know much about the technicalities involved in your case! 
It seems that while installing a lot of studio stuff you got more than one sound driver and the active one is not compatible with your sound thing. To check if this is the case:
Go to sound button on the panel-> sound preferences-> devices ->
Now check if a number of devices are visible there. Play the song. Select different devices. If u get sound on one, keep that selected. Done.

 I m not sure why should u even follow this. Still no harm in giving it a try.

---

### Post by chrisrodgers on 2011-07-24
I am not sure where "panel" is.  Is that from the Ubuntu main menu button in the upper left of the desktop?

I did find a sound post in the general Ubuntu forum that helped troubleshoot sound.  Turned out that everything was muted.  I ran alsamixer and all channels had MM at the bottom.  I had to unmute ALL of them (then they all had green box with 00 instead of MM).

Part of the troubleshooting guide suggested to put the driver (snd-hda-intel in my case) in the /etc/modules file.  I see that /etc/modules already has three entries: loop, lp, and rtc.  Should I add my sound driver or just leave it alone?

---

### Post by jejeman on 2011-07-24
If everything works now leave it alone.

If you find out later that something is not working you will deal with it than.

---

### Post by sgx on 2011-07-24
> **chrisrodgers said:**
> I am not sure where "panel" is.  Is that from the Ubuntu main menu button in the upper left of the desktop?

I did find a sound post in the general Ubuntu forum that helped troubleshoot sound.  Turned out that everything was muted.  I ran alsamixer and all channels had MM at the bottom.  I had to unmute ALL of them (then they all had green box with 00 instead of MM).

Part of the troubleshooting guide suggested to put the driver (snd-hda-intel in my case) in the /etc/modules file.  I see that /etc/modules already has three entries: loop, lp, and rtc.  Should I add my sound driver or just leave it alone?

Hi, run the lsmod   command, it will list the system kernel modules,
snd-hda-intel or similar will be one of them. Each sound related module will be listed, along with the other modules it interracts with:

snd_ice1712            50334  0 
snd_ice17xx_ak4xxx      1992  1 snd_ice1712
snd_ak4xxx_adda         7570  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427              5944  1 snd_ice1712
snd_ac97_codec         90143  1 snd_ice1712
ac97_bus                 850  1 snd_ac97_codec
snd_i2c                 3141  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         4983  1 snd_ice1712
snd_rawmidi            15287  2 snd_usbmidi_lib,snd_mpu401_uart
snd_seq_dummy           1135  0 
snd_seq_oss            25264  0 
snd_seq_midi_event      4648  1 snd_seq_oss
snd_seq                42136  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          4457  4 snd_rawmidi,snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            33822  0 
snd_pcm                60702  4 snd_usb_audio,snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_timer              15383  2 snd_seq,snd_pcm
snd_page_alloc          6037  1 snd_pcm
snd_mixer_oss          12981  1 snd_pcm_oss
snd                    43189  17 snd_usb_audio,snd_hwdep,snd_usbmidi_lib,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               5025  1 snd

Not the same methodology as needing drivers in windows xxx. Modules
can be added

modprobe snd_ice1712

or removed: rmmod snd_ice1712

or 'blacklisted' by putting them in the blacklist textfile in
/etc/modprobe.d. So if you bought a new soundcard, you might do
that to snd-hda-intel, to minimize system conflicts.

Cheers

/etc/

---

### Post by chrisrodgers on 2011-07-24
Thanks for the info, very helpful!  If anyone is curious, here is what I see - filtering on "intel" to make it relevant:  
```
$ lsmod | grep intel
snd_hda_intel          33211  4 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_pcm                96391  3 snd_hda_intel,snd_hda_codec
snd                    67382  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

```

---

