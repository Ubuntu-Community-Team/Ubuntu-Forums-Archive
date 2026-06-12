---
title: "Another noob with sound problems (slightly different)"
date: 2010-05-16
forum: Ubuntu Studio
---

### Post by CCraw on 2010-05-16
Good day,

I've just installed Ubuntu Studio 10.04 on some new hardware after using other versions on and off for a couple years. It's potentially awesome but I have a list of audio issues I need to deal with. Instead of a question-overload, I'm going to start from the top and work through each problem separately. 

Step 1:
Is there a way that I can get Ubuntu to completely ignore all other sound devices besides my Delta 1010, as in treat them like they don't even exist? I have no use for them and I feel that trouble-shooting will be easier if there's only 1 audio device that the system recognizes. I have the on-board sound disabled in bios but an RV710/730 chipset is still detected when I look in "Sound Preferences". This appears to be related to my video card. If it's not possible or way more trouble than it's worth, I'll just accept it and move on to fixing the actual problems.

Possibly relevant hardware stuff:
Processor: AMD Phenom 465 BE
Mobo: Gigabyte GA-770T-USB3
PCI Sound: M-Audio Delta 1010
Video: XFX Radeon HD 4650
4 gigs RAM 

Please let me know what additional info might be needed. I'm still fairly new to working with Linux (despite using it for years) so I appreciate any patience/hand-holding. 

Thanks,
Chris

---

### Post by sgx on 2010-05-16
Hi, in the folder  /etc/modprobe.d  there is, or can be a textfile called
blacklist. An unwanted soundchip or card would have its kernel module listed there. Mine reads

blacklist snd-usb-audio
blacklist snd_intel8x0

To see your modules, run the command  lsmod

a clump similar to this will be part of it, and sound devices
found by your kernel will appear. snd_ice1712 is typical for envy24 chips, as found in your nice Delta 1010:

snd_seq_midi_event      8704  2 snd_seq_midi,snd_seq_oss
snd_seq                54352  10 snd_seq_midi,snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_pcm_oss            42912  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_ice1712            63476  4
snd_ice17xx_ak4xxx      5248  1 snd_ice1712
snd_ak4xxx_adda         9472  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             10112  1 snd_ice1712
snd_ac97_codec        100516  1 snd_ice1712
snd_pcm                77188  5 snd_pcm_oss,snd_ice1712,snd_ac97_codec
snd_timer              24836  2 snd_seq,snd_pcm
snd_page_alloc         11656  1 snd_pcm
snd_i2c                 6656  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         9856  1 snd_ice1712
snd_rawmidi            25632  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9484  5 snd_seq_midi,snd_seq_dummy,snd_seq_oss,snd_seq,snd_rawmidi
snd                    56100  22 snd_seq_oss,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_pcm,snd_timer,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9440  1 snd

Notice my now blacklisted intel chip ( snd_intel8x0) is not mentioned :)

You'll need root privelidge to edit blacklist, something like

sudo gedit /etc/modprobe.d/blacklist

Good hunting!

---

### Post by CCraw on 2010-05-17
Thanks very much! That's exactly what I was looking for. The output from lsmod looked like this:

```

Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6471  0 
arc4                    1473  2 
snd_hda_codec_atihdmi     3055  1 
fbcon                  39612  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5875  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9921  1 vga16fb
snd_hda_intel          25545  0 
snd_ice1712            65411  0 
snd_hda_codec          85984  2 snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               6992  1 snd_hda_codec
snd_ice17xx_ak4xxx      3155  1 snd_ice1712
snd_ak4xxx_adda         8572  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_pcm_oss            41384  0 
snd_cs8427              7978  1 snd_ice1712
snd_ac97_codec        125298  1 snd_ice1712
snd_mixer_oss          16385  1 snd_pcm_oss
ac97_bus                1450  1 snd_ac97_codec
snd_i2c                 5582  2 snd_ice1712,snd_cs8427
snd_mpu401_uart         6889  1 snd_ice1712
snd_pcm                86461  5 snd_hda_intel,snd_ice1712,snd_hda_codec,snd_pcm_oss,snd_ac97_codec
snd_seq_dummy           1782  0 
snd_seq_oss            31649  0 
snd_seq_midi            5989  0 
snd_seq_midi_event      7331  2 snd_seq_oss,snd_seq_midi
snd_seq                57759  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
radeon                741479  2 
ath5k                 134627  0 
snd_rawmidi            23010  2 snd_mpu401_uart,snd_seq_midi
mac80211              243989  1 ath5k
ath                     9723  1 ath5k
snd_timer              23127  2 snd_pcm,snd_seq
ttm                    60585  1 radeon
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
cfg80211              149242  3 ath5k,mac80211,ath
edac_core              46065  0 
led_class               3732  1 ath5k
drm_kms_helper         31004  1 radeon
joydev                 10784  0 
serio_raw               4982  0 
edac_mce_amd            9214  0 
snd                    71776  17 snd_hda_intel,snd_ice1712,snd_hda_codec,snd_hwdep,snd_ak4xxx_adda,snd_pcm_oss,snd_cs8427,snd_ac97_codec,snd_mixer_oss,snd_i2c,snd_mpu401_uart,snd_pcm,snd_seq_oss,snd_seq,snd_rawmidi,snd_timer,snd_seq_device
xhci                   41192  0 
i2c_piix4               9639  0 
drm                   199884  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6024  1 radeon
soundcore               8394  1 snd
snd_page_alloc          8596  2 snd_hda_intel,snd_pcm
lp                      9400  0 
parport                37438  2 ppdev,lp
hid_logitech            8852  0 
ff_memless              5109  1 hid_logitech
ohci1394               30452  0 
usbhid                 40764  1 hid_logitech
hid                    83696  2 hid_logitech,usbhid
ieee1394               95721  1 ohci1394
r8169                  39298  0 
mii                     5237  1 r8169
pata_atiixp             4209  0 
ahci                   37614  2 

```

I blacklisted snd_hda_codec_atihdmi, rebooted, and it looks like the only audio device detected is my Delta 1010. Excellent start. I see numerous other suspicious modules that look like they might not be needed -  snd_hda_intel, for example. Should I just leave things alone?

Thanks again! 

-Chris

---

### Post by sgx on 2010-05-18
Hi, when things are working, impose a hard tweak-freeze,
and hit the record button while you still can :)
Cheers

---

