---
title: "Cannot get Canon i70 printer to work"
date: 2010-05-24
forum: Ubuntu Studio
---

### Post by bannaomar on 2010-05-24
I already tried installing i450, generic and i80, and nothing. It is connected through the USB, and I can print directly from camera, but not from Computer

I have Ubuntu studio

Here is my uname -a command (really don't know what it is for):

```
Linux OPERAUbuntu 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```And my lsmod command:```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
nls_utf8                1069  1 
udf                    78785  1 
crc_itu_t               1371  1 udf
sha256_generic         11191  2 
aes_i586                7268  61 
aes_generic            26863  1 aes_i586
dm_crypt               11331  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_analog    58566  1 
joydev                  8708  0 
arc4                    1153  2 
snd_hda_intel          21877  3 
snd_usb_audio          75765  1 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  5 snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss
snd_usb_lib            15658  1 snd_usb_audio
uvcvideo               56990  0 
pcmcia                 33024  0 
snd_hwdep               5412  2 snd_usb_audio,snd_hda_codec
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121792  0 
videodev               34361  1 uvcvideo
yenta_socket           20408  1 
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
snd                    54148  21 snd_hda_codec_analog,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13251  2 uvcvideo,videodev
usblp                  10481  0 
rsrc_nonstatic         10015  1 yenta_socket
asus_laptop            17008  0 
ricoh_mmc               2923  0 
psmouse                63245  0 
serio_raw               3978  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
lp                      7028  0 
cfg80211              126485  3 ath5k,mac80211,ath
led_class               2864  3 ath5k,asus_laptop,sdhci
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usb_storage            39425  1 
i915                  282354  2 
drm_kms_helper         29297  1 i915
drm                   162471  3 i915,drm_kms_helper
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
intel_agp              24177  2 i915
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
video                  17375  1 i915
output                  1871  1 video

```

---

