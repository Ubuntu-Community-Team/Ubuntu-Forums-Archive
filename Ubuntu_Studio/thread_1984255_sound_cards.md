---
title: "sound cards"
date: 2012-05-21
forum: Ubuntu Studio
---

### Post by animaguy on 2012-05-21
I have a desktop with Ubuntu Studio 12.04.

I mainly do animation with blender, however,

I am interested in purchasing a sound card to take advantage of the audio software pre-installed in Ubuntu Studio.

Can anyone offer advice as to what is on the market and what to look for in a Linux suppported sound card.

BTW, I can afford to purchase a high end/expensive sound card and the supported hadware and software if I can justify the expense. I just need to know what to look for.

Thanks.

---

### Post by sgx on 2012-05-21
Hi, m-Audio pci cards are probably the simplest to configure,
the ice_1712 kernel module they use is standard fare.

You can get an mAudio Audiophile 24/96 with midi, digital, and analog i/o, many people have used them for years,
or cards with many more input/output connectors, like delta 1010,
are handy for recording drumkits, ,live performances/sessions.
Cheers
(lots of other brands too, have one or more models known
to work right away, focusright, alesis, presonus, yamaha, etc
Not every model, so google each prospect.)

---

### Post by x371322 on 2012-05-22
For what it's worth, ever since the update to 12.04 my M-Box 3 has worked flawlessly. Never have been able to get it to work with Jack, until now. I should say I'm running a standard Ubuntu setup. Not studio.

---

### Post by sgx on 2012-05-22
Thats pretty cool! Do lsmod and arecord -l output
mention a chipset?

Cheers

---

### Post by x371322 on 2012-05-23
Never checked.

Here's my arecord output:

```
**** List of CAPTURE Hardware Devices ****
card 0: Mini [Avid Mbox Mini], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And here's what I get with lsmod:

```
Module                  Size  Used by
snd_seq_dummy          12686  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52365  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  12 
bnep                   17830  2 
binfmt_misc            17292  1 
arc4                   12473  2 
snd_hda_intel          32765  3 
snd_usb_audio         101566  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_pcm                80845  6 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_hwdep              13276  2 snd_usb_audio,snd_hda_codec
thinkpad_acpi          73942  0 
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_seq_midi           13132  0 
joydev                 17393  0 
iwlwifi               291847  0 
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
mac_hid                13077  0 
mac80211              436455  1 iwlwifi
snd_seq                51567  6 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
i915                  414603  4 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  2 iwlwifi,mac80211
snd                    62064  28 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm,snd_hwdep,thinkpad_acpi,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 41906  0 
drm_kms_helper         45466  1 i915
hid                    77367  1 usbhid
drm                   197692  5 i915,drm_kms_helper
btusb                  17912  2 
i2c_algo_bit           13199  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
soundcore              14635  1 snd
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
bluetooth             158438  23 rfcomm,bnep,btusb
psmouse                72919  0 
wacom                  42914  0 
serio_raw              13027  0 
video                  19068  1 i915
tpm_tis                18308  0 
nvram                  14029  1 thinkpad_acpi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
wmi                    18744  0 
e1000e                140005  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci

```

---

