---
title: "Jack - QJackCtl - Interface and Messages Issue"
date: 2012-09-20
forum: Ubuntu Studio
---

### Post by jomarip on 2012-09-20
The heart of the issue is that I am trying to use Ardour to make a audio tape for my Grandma and I am not getting any sound in the editing portion.  I am using Ubuntu 12.04 and I have my HDMI cord hooked up to my Vizio television. 

My hardware is as below


j@j:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfcffc000 irq 44
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe87c000 irq 16
jp@j1:~$ aplay -l  
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
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
 

In the set up of Jack, I am using Driver ALSA and I have tried all the Interface setting hw:0 hw:1 hw;1:3, default, etc.  However, I am not getting any sound from Ardour. In addition I am getting 
QSpiAccessible::accessibleEvent not handled: "8008" obj: QObject(0x0) "invalid interface!" 
or 
QMenu(0x7fff730ffd00)

in the message portion of Jack.

Finding proper documentation is difficult and any assistance and guidance would be appreciated


By the way the readable clients and writable clients only have Ardour and Midi Through

---

### Post by sgx on 2012-09-20
Hi, install timemachine for basic high quality recording

download here:

[http://packages.debian.org/unstable/sound/](http://packages.debian.org/unstable/sound/)

install with  sudo dpkg -i name-of.deb

timemachine appears in the audio tab of qjackctl to connect your
device or software from the left side. Play the w64 files with vlc, import, edit, and export to common formats using audacity.
I think command
timemachine -f wav will start it and change the .w64 recording
default to standard .wav format

In Ardour you must
set device preferences for your hda_intel device,
have jackd chosen as audio server
set qjackctl to also use hda_intel
connect your instrument output in qjackctl to the ardour input,
create an ardour project
create a track
arm the track for recording
then press record and play buttons

Cheers

---

### Post by jomarip on 2012-09-21
Thank you.  I did work around it. I was actually working with playback .wav files and they were not playing in an audible manner in Ardour. The lights were moving and I could edit, but couldn't hear anything. Sorry that there was some confusion

---

### Post by jejeman on 2012-09-21
I don't know what your project is, but if you can't work with JACK you can use Traverso witch works with only ALSA. Maybe Traverso will be enough for your project.

---

