---
title: "Only 3 or 4 audio apps start"
date: 2010-05-18
forum: Ubuntu Studio
---

### Post by bannaomar on 2010-05-18
I just installed Ubuntu Studio and really need some help. I was about to list audio production apps that dont start, but, really, is easier if I just name those few that do work, which are Audacity,  Beast, LMMS and Jack Controls.... that is IT... no other audio app start from terminal or from the menu. 

What happens when trying to start one is the following: I click on the app (or command line) and in some of them like Drum Machine, the app start screen appears, only to dissappear a few moments later, and that's it, nothing opens. One that seems to really want to start is Freqtweak, even the program opens and I can get to see all the controls but then freezes the system and disappears with all my open windows be it firefox or explorer, etc. Like if nothing happened. Please Help, what can I do?

---

### Post by sgx on 2010-05-18
Maybe jackd needs to be started?

jackd -d alsa -r 44100

If its running and some apps still are failing, (not all use jackd)
people will need to know your soundcard, videocard, ram amount,
cpu details, lspci and lsmod command output, your .jackrc line
(its in /home/you) and will ask for a few more that I forget :)
cheers

---

### Post by bannaomar on 2010-05-18
Thanks for the quick and useful reply. I tried starting Jack with command line and with menu and it froze in the graphical, and on the commad line it did nothing and returned the following message:

Output when trying to start Jackd with the command (I also tried with sudo)

jackd -d alsa -r 44100

```

Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

no message buffer overruns
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
Error en el bus
```[SIZE=3]


lspci[/SIZE]


```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
05:01.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
05:01.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
05:01.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
 
```[SIZE=3]


lsmod [/SIZE]

```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
sha256_generic         11191  2 
aes_i586                7268  38 
aes_generic            26863  1 aes_i586
dm_crypt               11331  1 
joydev                  8708  0 
snd_hda_codec_analog    58566  1 
arc4                    1153  2 
uvcvideo               56990  0 
mmc_block               8258  2 
videodev               34361  1 uvcvideo
snd_usb_audio          75765  1 
snd_usb_lib            15658  1 snd_usb_audio
pcmcia                 33024  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  2 snd_usb_audio,snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  10 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121792  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54148  21 snd_hda_codec_analog,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126485  3 ath5k,mac80211,ath
lp                      7028  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
asus_laptop            17008  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
ricoh_mmc               2923  0 
psmouse                63245  0 
serio_raw               3978  0 
led_class               2864  3 ath5k,sdhci,asus_laptop
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
usbhid                 36110  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
hid                    67032  1 usbhid
i915                  282354  2 
drm_kms_helper         29297  1 i915
drm                   162471  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
8139too                18545  0 
8139cp                 16186  0 
intel_agp              24177  2 i915
agpgart                31724  2 drm,intel_agp
mii                     4381  2 8139too,8139cp
video                  17375  1 i915
output                  1871  1 video
```

And no .jackrc in my home folder.

---

### Post by sgx on 2010-05-18
If qjackctl is not installed by default,

sudo apt-get install qjackctl

Start it and press its  Start button, and click the Setup button on the right

On the panel that appears, on the right side you'll see

Output Device >
Input Device  >

Click the  >  widgets, and a list of the names, or hardware identity numbers will appear.
One of them will be your soundchip.  Something like HW:0 or HW:1

start zynaddsubfx, when it appears,
press the Connect button on the main qjackctl screen. A three tabbed panel opens, 
zynaddsubfx appears in the right and left tabs. The alsa tab
on the rightmost panel has your selected midi ports. Connect to zyn by selectingboth zyn,
and the midi port on the opposite side, and press the connect button on this same panel
 (not the one on the main qjackctl screen) so you can send midi from your keyboard

The Audio tab has your soundcard inputs and outputs, called 'System'. 
Connect zyn to the system audio port on the opposite side, so you can hear this instrument while you play. 
Zyn has a virtual keyboard you can use, with a button label abbreviated VK

You must stop and restart qjackctl each time you change settings, and press the Start button again, 
so choose the available possibilities from the   > widget
until you find the correct one.

When you save qjackctl settings, the file .jackrc should be created.

This might get things rolling :D

Error en el bus 

I looked briefly for this error in google, various opinions of python, perl, physical memory problem, or other possibilities. But its a common
error, perhaps nothing directly audio in nature. Have you installed anything requiring a python or perl update?
Cheers

---

### Post by bannaomar on 2010-05-19
:popcorn:

 YEI !! THANKS!  Alright it seems the problem was that in Jack Preferences i had the "Real Time" checked (in spanish "tiempo real") and "Do not block memory" (no bloquear memoria) unchecked. So, I guess what happened was that apps tried to get no-latency speed when starting and thus crashed for insuficient resources to perform so.  Thanks ! I also now know thanks to you how to connect things through Jack, still some doubts but will learn on the way.

Greetings!

---

