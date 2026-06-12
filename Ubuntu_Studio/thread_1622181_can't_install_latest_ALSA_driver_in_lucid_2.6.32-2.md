---
title: "can't install latest ALSA driver in lucid 2.6.32-25 preempt"
date: 2010-11-15
forum: Ubuntu Studio
---

### Post by streamsanddragonflies on 2010-11-15
I have installed Ubuntu Studio 64 bits on an AMD system.

I first had alsa driver version that came with the 2.6.32-25 preempt kernel: ALSA driver 1.0.22, I believe. My maudio 2496 soundcard was detected but I couldn't get sound so I found a suggestion in ubuntu forum to install lucid backports. This created 2.6.32-25 generic kernel which I didn't want since I need low latency (and still had no sound). I tried at first to compile and install Alsa driver 1.0.23 (following Ubuntu Sound Troubleshooting Guide), having booted into the preempt kernel- but ALSA driver 1.0.23 only installed into the generic backport kernel. So I proceeded to remove the 2.6.32-25 backport generic kernel via synaptic.

I once again only have my original preempt kernel 2.6.32.25 and 2.6.32.21 in my grub list. I discovered that I had no soundcard detected and no more ALSA installed, according to 'aplay -l' & 'cat /proc/asound/version'

'cat: /proc/asound/version: No such file or directory'

so I proceeded to try to install Alsa driver 1.0.23 twice more but each time I get:

'bash alsa-info.sh --stdout
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
ls: cannot access /dev/snd/*: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1504: No soundcards found...
cat: /tmp/alsa-info.MBbsMbmpxU/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Nov 15 11:14:04 UTC 2010

!!Linux Distribution
!!------------------

Ubuntu 10.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

!!DMI Information
!!---------------

Manufacturer: Gigabyte Technology Co., Ltd.
Product Name: GA-790XTA-UD4

!!Kernel Information
!!------------------

Kernel release: 2.6.32-25-preempt
Operating System: GNU/Linux
Architecture: x86_64
Processor: unknown
SMP Enabled: Yes

!!ALSA Version
!!------------

Driver version:
Library version: 1.0.23
Utilities version: 1.0.23

!!Loaded ALSA modules
!!-------------------

!!Sound Servers on this system
!!----------------------------

Pulseaudio:
Installed - Yes (/usr/bin/pulseaudio)
Running - Yes

ESound Daemon:
Installed - Yes (/usr/bin/esd)
Running - No

Jack:
Installed - Yes (/usr/bin/jackd)
Running - No

!!Soundcards recognised by ALSA
!!-----------------------------

!!PCI Soundcards installed in the system
!!--------------------------------------

06:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

06:06.0 0401: 1412:1712 (rev 02)
Subsystem: 1412:d634

!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2

!!Loaded sound module options
!!--------------------------

!!ALSA Device nodes
!!-----------------

!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------

!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--

!!All Loaded Modules
!!------------------

Module
binfmt_misc
ppdev
fbcon
tileblit
font
bitblit
softcursor
joydev
psmouse
edac_core
serio_raw
edac_mce_amd
i2c_piix4
xhci
nvidia
vga16fb
vgastate
lp
parport
raid10
raid456
async_pq
async_xor
async_memcpy
async_raid6_recov
raid6_pq
async_tx
raid1
raid0
multipath
hid_logitech
linear
ff_memless
ohci1394
dm_raid45
usbhid
hid
floppy
xor
ieee1394
pata_atiixp
pata_jmicron
ahci
r8169
mii

!!ALSA/HDA dmesg
!!------------------

Somehow I can't install the driver, but the ALSA utilities and libraries are installed. What makes no sense is that I see the driver installed in /usr/src/alsa-driver-1.0.23.

I have / and /home in ubuntu software raid 0 and one of my drives has some bad sectors according to Disk Utility-even after I did a low level format; Can any quirks arise from such a set-up? I had problems with Ubuntu Studio Karmic on this computer (minus the 'bad' drive- Pulse audio would freeze up my system) -and I am still hoping that I can get better results with Lucid LTS...

Note: The 'bad' drive seems to be acceptable by gparted, I could still partition e.t.c... and I installed Win 7 and the 1/2 of my raid 0 for Ubuntu fine on it, but I couldn't use install any grub or windows bootloader to the mbr. Even though I changed the cable/port around and the boot order in bios- so if anyone thinks that this warrants chucking out the drive and replacing it - pls. advise.

Looking forward to suggestions!

---

### Post by Pablo_F on 2010-11-15
Hi, 

This looks very complicated... I can't help at this point, sorry. But you can always make a fresh install and try again. 

The m-audio 2496 works fine in ubuntu. Alsa module snd-ice1712 supports that card since years and you don't need to update drivers. However, there are a couple of crucial points you should take into account:

1. You need envy24control to access the internal mixer and levels. Above all, check the DAC and ADC levels in the Analog Volume tab.
. 
2. There is a problem with snd-ice1712 based cards and pulseaudio in ubuntu. See [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)

In my case (I also have an m-audio 2496) I was not seeing any analog outputs in gnome sound preferences or pavucontrol. I applied comment #30 and it worked like a charm. 

It was not until recently that I solved the pulseaudio issue, since I normally use jack and I didn't care too much about it.

Jack works very well on that card with the alsa driver, and out of the box. 

If you have problems with pulseaudio, you better kill it before starting jack (as a script on startup for example, "pulseaudio -k"), but then, you have to avoid that pulseaudio autospawns by something like:

echo autospawn = no > ~/.pulse/client.conf

Also, check your /dev/shm directory. If you have lots of pulse-shm* you have to delete them.  

Cheers! Pablo

---

### Post by streamsanddragonflies on 2010-11-17
Pablo_F, thanks for your help and the link to the long standing bug related to pulseaudio.  I haven't tackled it yet.  I am a little disappointed that a distro that is meant for audio production (U.Studio) still has driver issues with what I believe are popular soundcards. (And the maudio 2496 is one of the more straight forward ones).

Honestly the fact that Disk Utility sees some bad sectors on my Sata drive where I installed part of the raid 0 on has me wondering... Any one knows if bad sectors can contribute to installation issues including the ALSA driver or am I looking at this wrong?  Or could I simply have not removed all of the backport

...Anyways I'm hoping for confirmation that to replace this quirky Seagate drive with a WD that has 5 yrs warranty is worth the trouble.  I just hope that its not something else like possible IRQ issues with my MB (Gigabyte) and bios (although I have the most recent bios).

---

### Post by streamsanddragonflies on 2010-11-20
This is the latest; still using the same HDD & got sound working!

I managed to install the latest ALSA driver but had to install and boot into the generic kernel to do it.  I also got sound working after looking at posts from Bug #178442 which I thought was resolved: Comment #37, #52, #57, #63,#72 #110 #119 & 141#. 

Changing lines from #37 to :/etc/pulse/default.pa.  Also #64 applies more specifically to my card so I added lines to /lib/udev/rules.d/90-pulseaudio.rules. then saved as /etc/udev/rules.d/pulseaudio.rules

Also 
after reading #119:
replacing the maudio quickinstall file (can't remember the exact name right now; I`m not at home) with a a maudio-audiophile-2496.conf file in /usr/share/pulseaudio/alsa-mixer/profile-sets  from 
  ALSA  Ticket #624: pulseaudio-add-profile-sets-for-M_Audio-Audiophile-2496.patch that I slightly modified.

instead of the link from #63 [http://ubuntuforums.org/showpost.php?p=7965283&postcount=4](http://ubuntuforums.org/showpost.php?p=7965283&postcount=4).

Now I`m not sure if one of the 3 steps was unecessary or was I better off with the link from #63.  I will test audio editing apps soon and use qjackctl or pasuspend qjackctl if needed when using Jack.

I now wonder if this will all work in the preempt kernel and if I need the latest ALSA driver after all!

---

### Post by normr on 2010-11-21
The install method outlined in the "To a free world" blog has always worked for me:  [http://monespaceperso.org/blog-en/](http://monespaceperso.org/blog-en/)

Cheers!

---

### Post by streamsanddragonflies on 2010-11-25
Hello again! I went ahead and bought a new sata drive that checks out fine-no bad sectors.  I had to re-install some of my OSes and now in the process of figuring out how to boot back into U. Studio.  I had decided I would also install U. Desktop as a backup.  

So far I can confirm that is that the latest ALSA driver (see link from nomr 's post (thanks normr!) can definitely only be installed to the generic kernel, not the preempt. So when I can finally boot to my preempt kernel (U. Studio),  I will stick with the ALSA driver that it pre-installs and just stick with the instructions as per comments in bug   [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442)  as per Pablo_F 's post!


I will add a new post to update wether all sound works well with preempt kernel and test all audio apps and audio editing apps...

---

### Post by bluesscream on 2010-11-29
I never was lucky with 2.6.32 kernels >22 and my ice1712 (envy24).
I gave it up soon and went over to 2.6.33-29-realtime and 2.6.35 and 36 series, selfcompiled (generic and full preempt) as well as from repos which all let me do audio work sufficiently in a dualcore lucid amd64 environment. 
Sometimes I suffer from kernel testing and compiling addiction ;)

---

### Post by streamsanddragonflies on 2012-01-21
Just a footnote to this solved issue.  I have been succesfully using jack, Ardour and guitarix, jackrakk, and rackarack with my soundcard for some time. Very happy to have gotten familiar with recording in linux, finally, and quite happy with it.:D

Now I am testing a firewire interface(Focusrite Saffire Pro 40) because we need more channels, among other reasons.  I will keep the card in as an option, and perhaps have pulse audio linked to it, while jack is running with the firewire... The 2.6.33-29-realtime kernel may be necessary for this.

---

