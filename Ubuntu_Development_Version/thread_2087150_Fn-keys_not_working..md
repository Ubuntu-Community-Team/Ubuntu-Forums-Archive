---
title: "Fn-keys not working."
date: 2012-11-22
forum: Ubuntu Development Version
---

### Post by serdotlinecho on 2012-11-22
After installing the latest updates(raring proposed enabled), Fn+up/down/left/right buttons not working(notify osd do not appear to show the indicator) to change the sounds volume and brightness on samsung n148 plus netbook. Anyone had a similar problem?

---

### Post by serdotlinecho on 2012-11-25
The latest dist-upgrade makes my fn keys up/down not working anymore to change the screen brightness on samsung n148 plus netbook. There is samsung_laptop module, but it is useless at the moment.

```
lsmod
Module                  Size  Used by
bnep                   17737  2 
rfcomm                 37421  0 
arc4                   12544  2 
binfmt_misc            17261  1 
brcmsmac              503493  0 
snd_hda_codec_realtek    63540  1 
cordic                 12519  1 brcmsmac
uvcvideo               71280  0 
brcmutil               14356  1 brcmsmac
mac80211              470993  1 brcmsmac
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
videobuf2_core         34625  1 uvcvideo
cfg80211              184762  2 brcmsmac,mac80211
videodev               95768  2 uvcvideo,videobuf2_core
snd_hda_intel          32761  3 
joydev                 17098  0 
snd_hda_codec         116443  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80891  2 snd_hda_codec,snd_hda_intel
gpio_ich               13237  0 
coretemp               13098  0 
snd_page_alloc         14231  2 snd_pcm,snd_hda_intel
i915                  504099  3 
snd_seq_midi           13133  0 
snd_seq_midi_event     14476  1 snd_seq_midi
snd_rawmidi            25383  1 snd_seq_midi
drm_kms_helper         45273  1 i915
snd_seq                51281  2 snd_seq_midi_event,snd_seq_midi
samsung_laptop         14101  0 
drm                   227450  4 i915,drm_kms_helper
btusb                  17951  0 
snd_seq_device         14138  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24412  2 snd_pcm,snd_seq
bluetooth             183825  11 bnep,btusb,rfcomm
i2c_algo_bit           13198  1 i915
snd                    62146  15 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
microcode              18287  0 
soundcore              14600  1 snd
psmouse                75804  0 
lpc_ich                16926  0 
serio_raw              13032  0 
bcma                   34750  1 brcmsmac
video                  18848  2 i915,samsung_laptop
mac_hid                13038  0 
lp                     13300  0 
parport                40754  1 lp
sky2                   52927  0 

```I have to edit grub config files to makes fn keys up and down for screen brightness to work. I added this lines:

```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```Then sudo update-grub and reboot to make it work. 
But now, after latest dist-upgrade, it's not working anymore. When i pressed fn+up/down, notify-osd indicator not show up at all and after that, notify-osd sound indicator also not working, i have to logout and login again. ](*,)
When I'm gonna get support for my fn keys samsung netbook working out of the box? [-o<

---

### Post by serdotlinecho on 2012-11-27
I've just finished dist-upgrade, reboot and it's working again. Thanks! 
But still no support for fn+keys screen brightness.

---

