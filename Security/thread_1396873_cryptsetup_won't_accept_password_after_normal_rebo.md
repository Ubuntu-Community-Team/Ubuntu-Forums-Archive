---
title: "cryptsetup won't accept password after normal reboot"
date: 2010-02-02
forum: Security
---

### Post by wucherpfennig on 2010-02-02
Hi,

Strange thing happend two days ago. I just wanted to reboot my computer and now I'm no longer able to boot o0. My system is runnig with a full encryption with luks/cryptsetup. I'm using a passphrase to unlock my first partition and it will unlock the others by itself. So far so good. But now it doesnt work anymore... I'm not sure what I did before, but what I know, I didn't change anything! about cryptsetup. I did only a little "update" with the recommended packages from the repositories (guess only 4-5 updated) :(

I already checked with live cd and same thing there. Not able to unlock any device (what seems strange to me, cause there are 4 of them and all corrupted at the same time...?)

I always get the error message: 
unlock failed, bad password or options? (on boot)
Command failed: No key available with this passphrase (live cd)

First thing I did was checking wheter all modules are loaded:
```
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
sha256_generic         11580  0 
cbc                     3516  1 
aes_i586                8124  2 
aes_generic            27484  1 aes_i586
cx88_blackbird         16608  0 
cx2341x                13440  1 cx88_blackbird
wm8775                  3660  1 
arc4                    1660  2 
ecb                     2524  2 
binfmt_misc             8356  1 
ppdev                   6688  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
snd_hda_codec_realtek   203328  1 
cx22702                 5760  1 
cx88_dvb               21088  0 
cx88_vp3054_i2c         2524  1 cx88_dvb
videobuf_dvb            7040  1 cx88_dvb
dvb_core               87364  2 cx88_dvb,videobuf_dvb
tuner_simple           14832  2 
tuner_types            14396  1 tuner_simple
snd_hda_intel          26920  2 
tda9887                10496  1 
tda8290                12960  0 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
tuner                  21540  2 
snd_seq_dummy           2656  0 
cx88_alsa              10596  1 
snd_seq_oss            28576  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_seq_midi            6432  0 
iptable_filter          3100  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_pcm                75296  4 snd_hda_intel,snd_hda_codec,cx88_alsa,snd_pcm_oss
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
cx8800                 30712  1 cx88_blackbird
ath9k                 258744  0 
cx8802                 15264  2 cx88_blackbird,cx88_dvb
mac80211              181236  1 ath9k
cx88xx                 77644  5 cx88_blackbird,cx88_dvb,cx88_alsa,cx8800,cx8802
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               16544  1 ip_tables
ir_common              48512  1 cx88xx
led_class               4096  1 ath9k
i2c_algo_bit            5760  2 cx88_vp3054_i2c,cx88xx
ath                     8060  1 ath9k
v4l2_common            17500  6 cx88_blackbird,cx2341x,wm8775,tuner,cx8800,cx88xx
videodev               36736  6 cx88_blackbird,wm8775,tuner,cx8800,cx88xx,v4l2_common
snd_timer              22276  2 snd_pcm,snd_seq
v4l1_compat            14496  1 videodev
tveeprom               11872  1 cx88xx
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videobuf_dma_sg        12544  6 cx88_blackbird,cx88_dvb,cx88_alsa,cx8800,cx8802,cx88xx
joydev                 10272  0 
psmouse                56180  0 
videobuf_core          17952  6 cx88_blackbird,videobuf_dvb,cx8800,cx8802,cx88xx,videobuf_dma_sg
cfg80211               93052  3 ath9k,mac80211,ath
btcx_risc               4740  4 cx88_alsa,cx8800,cx8802,cx88xx
serio_raw               5280  0 
snd                    59204  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,cx88_alsa,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
dm_crypt               12928  1 
i2c_piix4               9932  0 
squashfs               22912  1 
aufs                  149420  1 
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
hid_logitech            8412  0 
ff_memless              5188  1 hid_logitech
usbhid                 38208  1 hid_logitech
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
usb_storage            52544  1 
floppy                 54916  0 
r8169                  32064  0 
mii                     5212  1 r8169
ati_agp                 6760  0 
agpgart                34988  1 ati_agp
```

seems right to me. So I tried to unlock with
```
cryptsetup luksOpen /dev/sda8 crypt8
```
but that doesn't work...

i dunno wheter my header is corrupted
```
LUKS header information for /dev/sda8

Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1
Payload offset:	2056
MK bits:       	256
MK digest:     	7d 47 0e 87 a6 e2 4a 20 64 0c 3d d6 bb c5 5a 7e 6b 3d f3 02 
MK salt:       	c2 3f 69 b9 da 76 d9 36 49 f3 ad 4d 4b d5 e2 4e 
               	92 08 f6 0d ca 43 e7 e1 64 8f 8a 8d 67 03 e7 00 
MK iterations: 	10
UUID:          	3fea3f31-87f0-40c7-abc7-4d11759816fd

Key Slot 0: ENABLED
	Iterations:         	449263
	Salt:               	fe 79 7d 7c 77 3b 4b 47 4d b1 f0 50 62 e8 d8 e5 
	                      	33 30 52 28 45 84 2f 0b 23 67 80 c2 0d f1 21 ac 
	Key material offset:	8
	AF stripes:            	4000
Key Slot 1: ENABLED
	Iterations:         	422731
	Salt:               	e4 9e 6c e7 6b f2 91 63 4f 28 83 58 73 c0 17 0b 
	                      	9e 85 65 de 90 fa 90 cf 54 4d 48 ac 49 0c 6f 7e 
	Key material offset:	264
	AF stripes:            	4000
Key Slot 2: ENABLED
	Iterations:         	420163
	Salt:               	1c ef 1d 1a a5 94 2d c9 6b c2 21 0d be bc 63 78 
	                      	66 99 26 f9 a0 56 b1 91 15 3b 9d fb c1 8d fd d8 
	Key material offset:	520
	AF stripes:            	4000
Key Slot 3: DISABLED
Key Slot 4: DISABLED
Key Slot 5: DISABLED
Key Slot 6: DISABLED
Key Slot 7: DISABLED

```

Only thing I can imagine is that im using the wrong keyboard layout, but how could I check that? I never saw my input in the boot progress '^^.

I appreciate any help! ;)

---

### Post by wucherpfennig on 2010-02-03
New try with the daily live CD gives me sometimes this error:

device-mapper: remove ioctl failed: Device or resource busy

any suggestions?

---

### Post by DZ* on 2010-02-03
Perhaps you'd get more help here --
[http://news.gmane.org/gmane.linux.kernel.device-mapper.dm-crypt](http://news.gmane.org/gmane.linux.kernel.device-mapper.dm-crypt)

You can post to gmane.linux.kernel.device-mapper.dm with a newsreader by pointing it to news.gmane.org

---

### Post by FuturePilot on 2010-02-03
You mentioned the Daily Live CD. Are you using Lucid? It may be development cycle breakage. You might get more/better help in the [Lucid development forum]("http://ubuntuforums.org/forumdisplay.php?f=377").

---

### Post by wucherpfennig on 2010-02-03
nope, sorry for this misunderstanding. I tried lucid cause I wanted the latest version of cryptsetup...

---

### Post by wucherpfennig on 2010-02-03
It's me again. I don't know whether I have to check all languages (probably wrong keyboard layout causes problems) or anybody can explain what happened? (Probably a script could solve this time wasting exercise?)
Anyway, I don't think it's about keyboard settings. (Well I hope it is such a "little" error and nothing serious) I always use the settings german switzerland. I remember, while setting up ubuntu, that I checked my layout before I entered my password. So I know, what I wrote/write. Is there really no way to check my headers or whatever if they are broken? Or which languages do I have to check else? (I checked several usa, uk,german, swiss layouts...)

pls some help before I have to run over the whole disk...

---

