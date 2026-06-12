---
title: "no audio at all in Precise"
date: 2013-01-30
forum: Ubuntu Studio
---

### Post by youWho on 2013-01-30
Installed Ubuntu Studio precise pangolin and I have no audio output from speakers (VIAO laptop, "F series"). Sound was fine on Natty, which I was using prior to this. Actually meters move in various apps, just no sound comes out.

This restores audio temporarily:
1. delete the ~/.pulse directory
2. in terminal do: sudo killall pulseaudio

I notice that in the deleted .pulse folder there's a file called "ddb53084c78e0e4e52a1655800000011-default-sink" which contains only this (no quotes): "alsa_output.pci-0000_00_1b.0.analog-stereo". Also, if I open the "Sound Settings..." window from the speaker icon in the notification area, under the "Output Devices" tab, the output "Port" has no setting for internal speakers; the only option there is for HDMI output, and I think that this is somehow the problem: that the analog output to the internal speakers is somehow not being loaded/included/?. Beyond that I'm stuck.

If I try to start Jack using qjackctl it complains that another process is using the device and fails to start. It lists pulseaudio as the culprit.

I'd like to be able to use Jack, but also to have audio in general. I'm even nostalgic for vim's "beep mode" ;-). Any help would be really appreciated!!

If this helps:
lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

---

### Post by CrocoDuck on 2013-01-31
Hi. When an "NVIDIA Corporation High Definition Audio Controller" is present some similar issue is common. Have a look at this: [http://askubuntu.com/questions/176659/only-hdmi-audio-since-installing-nvidia-card-onboard-audio-device-has-disappear](http://askubuntu.com/questions/176659/only-hdmi-audio-since-installing-nvidia-card-onboard-audio-device-has-disappear) , maybe you can solve it with a BIOS setting. If not, repost the output of

```
aplay -l
```

and

```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by ttoine on 2013-01-31
install pulseaudio-module-jack

It may solve the problem between pulse audio and jack.

---

### Post by youWho on 2013-02-03
Thanks both of you, and sorry for the delay before I wrote back.

CrocoDuck: I have a Sony Viao VPCF116FX and when I rebooted with the F2 key down to get into the BIOS settings there seemed to be no settings dealing with sound cards; indeed the only settings I got were for very basic stuff like whether to boot from a CD, whether to use a password, etc. Is there another layer of settings pertaining to things within Ubuntu?? How would I access that?

The ooutput of aplay -l is:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC275 Analog [ALC275 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC275 Digital [ALC275 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The output of cat /etc/modprobe.d/alsa-base.conf is:
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

I'm wondering: could it be in the last couple of lines there?? Where it says:
# Keep snd-pcsp from being loaded as first soundcard
If so, how would I change that?

Or do you have a better understanding of what the problem is??? I didn't have audio problems until installing precise, and there was no BIOS change in between.

BTW I'm using Ubuntu Studio and I tried logging into an xfce session instead of ubuntustudio and there was still no sound  (for example no system beeps).


ttoine: I'll install that. The odd additional problem I have is that I don't have interwebs access in ubuntu here, and am at the moment writing this through Windows (dual boot) and a USB dongle that for unknown reasons isn't working with ubuntu. Anyway as soon as I have a chance to walk down to the cafe where thay have wifi I'll install that package and let you know.

---

### Post by CrocoDuck on 2013-02-03
In the BIOS you can navigate the options with the instructions provided usually in a section of the screen. If you didn't found nothing to configure of the kind we was searching for, probably there's nothing like this. The HDA intel should be the device designed to handle analog inputs and outputs (i.e. stereo jack connectors and speakers). In a friend's computer we managed to solve a similar issue by adding a line to /etc/modprobe.d/alsa-base.conf . Have a try by acting like this: 
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```be carefull, don't erase or modify no one line and add at bottom of the file

```
options snd-hda-intel model=vaio
```save and reboot.

Im' not really sure on what to give to the model option. If this don't go, try with sony or toshiba-s06. When you are editing configuration files, as alsa-base.conf is, remember: **never erase lines**. Is better to put a # at the beggining of a line to comment that line. This say to the program that will read the conf file to don't read that line at all. If you want to test what happen commenting the lines you said you can do it (I don't think they are the problem, this conf file looks standard), any modification should be effective after reboot. Any modification you do commenting (uncommenting) a line and rebooting should be reversible uncommenting (commenting) the line and rebooting. As always, one step at a time and carefully try to add the line.

---

### Post by youWho on 2013-02-03
I tried adding that line to /etc/modprobe.d/alsa-base.conf but unfortunately it didn't work. As you said I might have to research whether there's a different model to use instead of "vaio". I'll check that out and post back.

Re the BIOS: I checked every section/screen/menu that was offered and none had any settings for sound cards.

Thanks again, and if you have an other ideas I'd appreciate it. Or if anybody else has...

---

### Post by CrocoDuck on 2013-02-04
I found that we could find what is the right parameter to use for model by looking at codecs. Repost the output of:

```
cat /proc/asound/card0/codec#* | grep Codec
```Consider to have a look at alsamixer too after the reboots you do. In a terminal:

```
alsamixer
```You will find the instructions to use the program prompted in the window. Look if you can select your HDA intel and have a look on levels.

---

### Post by youWho on 2013-02-12
thanks again, and sorry again for the long delay before I reply.

It appears that my audio is now mostly working, but unfortunately I'm not in a position to offer helpful info to anybody else having similar problems because what fixed it in my case was that I ended up re-installing the OS from scratch (Ubuntu Studio precise). It happened somewhat by accident: in addition to the audio problem I also had a situation where it was impossible to get online with this USB dongle I have (a Huawei E303) and in trying every sort of thing to try to fix that, somehow I installed something that conflicted with the OS so much that the window manager was pretty much hosed---window title bars and borders disappeared and windows could no longer be moved around. I ended up re-installing and huh, I've got audio from Audacious playing through the internal speakers, and significantly, the internal speakers are listed in the "output" tab of the PulseAudio control window that is accessed through the speaker icon up in the notification area (sorry I have to be vague here because I write this through Windows :-( since the network problem has resurfaced). The internal speakers were not listed there at all before. Probably I had installed something originally that had messed up PulseAudio's configuration, but I don't know what it was.

I should say though that I still have no "system sounds" at all---no beep, no way to even choose a preferred sound, as had been the case with previous versions of Ubuntu Studio. Having an app beep at me is not a high priority, but it would be nice to fix it if possible. So if anybody has any thoughts on that I'd appreciate it. I'll mark this as [SOLVED} anyway though, since the main problem seems to be fixed.

So sorry not to be of much help to others in resolving the general no-audio issue. But thanks especially to CrocoDuck.

---

