---
title: "UM-1G usb MIDI interface stopped working"
date: 2011-03-17
forum: Ubuntu Studio
---

### Post by Roel123 on 2011-03-17
Hi,

I bought a usb MIDI interface last week. It's a Cakewalk UM-1G. 

I tried it on Debian first and I got it to work with Rosegarden. Then the next day it did no longer show up in the jack list of midi connections. I installed Ubuntu Studio yesterday and it also does not recognize the UM-1G.

I booted my Windows XP laptop and installed the driver and it worked so the UM-1G is not broken.

Can someone help me troubleshoot this thing please?

dmesg:
...
usb 2-2: new full speed USB device using ohci_hcd and address 4
....

# lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="SeaGreen"]Bus 002 Device 004: ID 0582:0104 Roland Corp. [/COLOR]
Bus 002 Device 002: ID 046d:c040 Logitech, Inc. Corded Tilt-Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by sgx on 2011-03-17
Hi, the system will assign IDs based on what hardware is connected,
and this can change easily since usb items are made to come and go easily. Check in qjackctl setup page,

Input Device  >
Output Device  >

Click the > widgets

If the device is shown both numerically, and with a name,
try choosing the named entry.

Some folks have several usb devices, and do a lot of juggling,
but flexibility is a good thing.

In qjackctl, in the 'periods' selector, choose 3 for most usb devices, avoid using secondary usb hubs, and if the 'dongle' is
for another OS, I would remove it when booting linux.

Cheers

---

### Post by Roel123 on 2011-03-21
Thanks for answering!

My device does not show up in the list, only my onboard soundcard.

The dongle is for bluetooth, it works fine and I do not have any other OS on this machine.

I ran some commands I found on the internets:

aplay -l
```
aplay -l
**** Lijst van PLAYBACK hardware-apparaten ****
kaart 0: SB [HDA ATI SB], apparaat 0: ALC888 Analog [ALC888 Analog]
  Sub-apparaten: 0/1
  Sub-apparaat #0: subdevice #0
kaart 0: SB [HDA ATI SB], apparaat 1: ALC888 Digital [ALC888 Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

```

No usb MIDI listed :(

```
root@roel-desktop:~# modprobe snd-usbmidi-lib 
root@roel-desktop:~# modprobe snd-usb-audio 
root@roel-desktop:~# cat /proc/asound/modules
 0 snd_hda_intel
```

Do I need to see snd-usb-audio in use?

I think there is something wrong in alsa. 

This is a fresh install of Ubuntu Studio.

---

### Post by sgx on 2011-03-22
Hi, the lsmod command will show the kernel modules loaded,
and groups of them that are related, like this:

snd_pcm_60719---3--------snd_usb_audio,snd_ice1712,snd_ac97_code

so snd_pcm is used by the other three.

If you have those modules mentioned in the lsmod output, they are already in place.

What is the result when you boot with no usb devices, then hotplug
the Roland unit? And try in all the usb ports, some computers ship
with ports that are blanks, in place for expansion from headers on the motherboard. And check the  > widgets in qjackctl each time.

How about the MIDI Check Switch and MIDI Through Switch?
Have you tried these in different positions?

Cheers

---

### Post by Roel123 on 2011-03-22
The lsmod output:

```
roel@roel-desktop:~$ lsmod
Module                  Size  Used by
parport_pc             30086  0 
ppdev                   6804  0 
rfcomm                 40787  4 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42304  16 rfcomm,bnep
snd_hda_codec_realtek   300173  1 
tuner_simple           15137  1 
tuner_types            18715  1 tuner_simple
wm8775                  3861  1 
snd_hda_intel          26147  2 
tuner                  23302  1 
snd_hda_codec         100951  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
cx25840                31895  1 
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
ivtv                  158941  0 
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  3 snd_seq_midi,snd_seq_midi_event
cx2341x                13689  1 ivtv
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_common            20635  5 wm8775,tuner,cx25840,ivtv,cx2341x
videodev               49359  5 wm8775,tuner,cx25840,ivtv,v4l2_common
v4l1_compat            15519  1 videodev
radeon                910067  2 
lp                     10201  0 
v4l2_compat_ioctl32    12614  1 videodev
snd                    64181  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    68212  1 radeon
drm_kms_helper         32836  1 radeon
soundcore               1240  1 snd
drm                   206198  4 radeon,ttm,drm_kms_helper
btusb                  12929  2 
tveeprom               14098  1 ivtv
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
k8temp                  4128  0 
amd64_edac_mod         24459  0 
edac_core              46822  3 amd64_edac_mod
edac_mce_amd            9387  1 amd64_edac_mod
parport                37032  3 parport_pc,ppdev,lp
i2c_algo_bit            6208  2 ivtv,radeon
shpchp                 34910  0 
i2c_piix4              10047  0 
usbhid                 42030  0 
hid                    84710  1 usbhid
r8169                  42254  0 
ahci                   22210  4 
libahci                26148  1 ahci
mii                     5261  1 r8169
pata_atiixp             4405  0 

```

Booting and then inserting the unit does not make a difference.

I tried different usb ports but I see no result. All usb ports are connected, I have build this box myself.

The midi check button plays a note on my synth but I don't know if the pc receives it as I do not know how to check. As my unit does not show up in the jack connect screen, I can not connect it to a softsynth.

Toggling the midi trough switch does also nothing.

Can it be that it is an alsa problem?

I don't know what to try anymore, it worked one full day and then the next day it no longer showed up.

---

### Post by Pablo_F on 2011-03-22
I suggest you ask in the alsa users mailing list or in their channel at IRC. Or report a bug in launchpad. Most of us helpers in this forum are mere users and this problem seems rare. Developers will know better but they don't normally reply to the forums. My 2C.

Cheers, Pablo

---

### Post by sgx on 2011-03-23
I have the E-mu midi interface, a nice 2x2, built like a tank,
and always shows up where it should. The 1x1 model is $30.
I'd sell/trade your Roland to a windows musician, rather than
more mud wrestling.
Cheers

---

### Post by AutoStatic on 2011-03-23
Hello Roel123, could you post the outcome of **amidi -l** with the UM-1G attached? It should work, virtually all Roland/Edirol sound devices should be supported, especially the lesser complex ones.

Best,

Jeremy

---

### Post by Roel123 on 2011-03-23
I bought this because it is supposed to work with Linux!

Anyway, I'm trying to get some help from the Alsa folks. If I get it fixed I'll let you know here.

---

