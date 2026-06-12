---
title: "USB Audio Problem"
date: 2008-08-12
forum: Ubuntu Studio
---

### Post by Pippinuk on 2008-08-12
Hi, I am having a problem getting my Edirol SD-90 to work with Ubuntu 8.04.  The SD-90 is a USB audio device and the OS can see it ok.  Below is a little info can anyone help me at all!!?
[B]
With the device detached from the PC:[/B]

phill@Pippin:~$ cat /proc/asound/cards
--- no soundcards ---
[B]
With the device attached to the PC:[/B]

phill@Pippin:~$ cat /proc/asound/cards
 0 [SD90           ]: USB-Audio - SD-90
                      EDIROL SD-90 at usb-0000:00:03.2-1, full speed


**gedit /etc/modprobe.d/alsa-base looks like this:**

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
#options snd-usb-audio index=2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

# USB
# options snd-usb-audio index=0 vid=0x0582 pid=0x0016

**When I try to open the volume control the following message appears:**

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Any assistance you can give would be great.  Many thanks in advance.
Cheers

---

### Post by pietjanjaap on 2008-08-14
asoundconf-gtk
Try this in the terminal, change your output to a different device.

---

### Post by Pippinuk on 2008-08-14
Thanks for the reply, I tried it but same thing.....when I test the sound I receive this message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

I have been messing around with this a lot so maybe I should reinstall the OS so I have clean install to start tinkering with......what do you think?

Thanks again for your help.

---

### Post by Lomedhi on 2008-08-25
Pippinuk, have you made any progress on this? I have the same device and problem. If I find a solution, I'll return and post it here.

---

