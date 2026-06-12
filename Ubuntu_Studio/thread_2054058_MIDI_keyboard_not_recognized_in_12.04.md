---
title: "MIDI keyboard not recognized in 12.04"
date: 2012-09-06
forum: Ubuntu Studio
---

### Post by jy_moustache on 2012-09-06
Hi all,
I've just installed the latest version of ubuntustudio (12.04) and tried it. It's default config works really well except my MIDI keyboard is not recognized by jack (or alsa) anymore.

The keyboard is a M-Audio Oxygen 8 v2 Class Compliant MIDI keyboard and was recognized out of the box by ALSA/JACK on my previous setup (Ubuntu 10.04).

Symptoms are strange :
 * keyboard is recognized as a usb device
 * keyboard is recognized as an audio device
 * keyboard doesn't appear is ALSA tab in QJAckCtl

Has anyone any idea why this is happening ?

Thanks a lot !
Cheers

jy

PS : Below are some logs.

```
$cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0400000 irq 45
 1 [v2             ]: USB-Audio - USB Oxygen 8 v2
                      M-Audio USB Oxygen 8 v2 at usb-0000:00:1d.1-1, full speed

``````
$ aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: Intel [HDA Intel], périphérique 0: ALC888 Analog [ALC888 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 1: ALC888 Digital [ALC888 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: Intel [HDA Intel], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
``````
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 004: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 004 Device 002: ID 147e:1000 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 007 Device 002: ID 046d:c062 Logitech, Inc. LS1 Laser Mouse, corded
Bus 007 Device 004: ID 0763:0195 Midiman Oxygen 8 v2
``````
$ lsmod
Module                  Size  Used by
snd_usb_audio          83446  0 
snd_usbmidi_lib        22777  1 snd_usb_audio
snd_rawmidi            22278  1 snd_usbmidi_lib
rfcomm                 36924  0 
parport_pc             30454  0 
ppdev                  12657  0 
bnep                   17304  2 
bluetooth             149293  10 rfcomm,bnep
vesafb                 12533  1 
nvidia              10920289  62 
snd_hda_codec_hdmi     30352  1 
snd_hda_codec_realtek    95198  1 
snd_hda_intel          25788  8 
snd_hda_codec          87980  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              12910  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            39968  0 
snd_mixer_oss          21707  2 snd_pcm_oss
snd_pcm                69043  7 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          12455  0 
snd_seq_oss            32416  0 
snd_seq_midi_event     13124  1 snd_seq_oss
joydev                 17045  0 
snd_seq                51504  8 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
arc4                   12418  2 
mxm_wmi                12433  0 
acer_wmi               21950  0 
sparse_keymap          12680  1 acer_wmi
usbhid                 39848  0 
snd_timer              22187  2 snd_pcm,snd_seq
hid                    72496  1 usbhid
snd_seq_device         12980  4 snd_rawmidi,snd_seq_dummy,snd_seq_oss,snd_seq
uvcvideo               65904  0 
videodev               74112  1 uvcvideo
iwlwifi               277351  0 
snd                    50814  29 snd_usb_audio,snd_usbmidi_lib,snd_rawmidi,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
mac80211              390762  1 iwlwifi
wmi                    17301  2 mxm_wmi,acer_wmi
psmouse                68512  0 
serio_raw              12733  0 
soundcore              12926  2 snd
snd_page_alloc         12841  2 snd_hda_intel,snd_pcm
cfg80211              159973  2 iwlwifi,mac80211
video                  17678  0 
mac_hid                12609  0 
lp                     12826  0 
parport                35349  3 parport_pc,ppdev,lp
atl1e                  31620  0 
ums_realtek            17304  0 
uas                    17270  0 
usb_storage            35395  1 ums_realtek
```

---

### Post by jejeman on 2012-09-06
To list MIDI devices command is
```
amidi -l
```

---

### Post by jy_moustache on 2012-09-07
Here it is !
```
$ amidi -l
Dir Device    Name
IO  hw:1,0,0  USB Oxygen 8 v2 MIDI 1

```Thanks

jy

---

### Post by sgx on 2012-09-08
Hi, in qjackctl setup page, Input Device >

click the >  and look for for an item with v2,
or just type that v2 in the field, instead of hw:0, default, or whatever else is in there. That might work.
Cheers

---

### Post by jy_moustache on 2012-09-08
Isn't the input device supposed to be audio? 
I'll try that anyway...
thx
Jy

---

### Post by jejeman on 2012-09-08
Yes, that is for audio. No need to set that.
Since amidi displayed your device, you should see it in ALSA tab in Qjackctl.

---

