---
title: "Ubuntu Studio MIDI setup"
date: 2016-08-14
forum: Ubuntu Studio
---

### Post by viayner2 on 2016-08-14
Hi,
I am new on the forum.
I have been looking on the forum but I did not found such problem as is mine.
I am trying to setup MIDI on Studio 14.04 and now also 16.04. Both do not work as I wish.
I have SB Live 5.1 card with MIDI interface what I would like to use.
I setup all in JACK and it seems to work, there is sound and all port appear in "connect" but I can not connect any "device" or application to SB5.1 MPU-401 port, it just not allow me to make such connection, when I drag nothing happens, no connection is made. All other ports what I have as Midi Trough or WaveTable are OK and allow me to connect just UART do not allow me to do that.
Is there any step what I maybe forgot with MIDI settings. I am not interested to play MIDI files (maybe later) I need to connect MIDI devices trough MIDI interface to Ubuntu Studio and be able to control them.
Second my problem also related to MIDI is midi to serial. I have Opcode Studio 64X midi interface which do not work straight with Linux, I was thinking to connect it trough his RS232 port to the PC as it was originally done under win98. I was trying ttyMidi and similar but there is no response from 64x. Does anybody have experience with Opcode path bay and Linux connection?
Thank you for your help.
Regards

---

### Post by jejeman on 2016-08-15
Give here output from
```
amidi -l
```
use aconnect to connect MIDI ports. See available ports
```
aconnect -i
aconnect -o
```
And do connection e.g.
```
aconnect 20:0 21:1
```

---

### Post by deanpeters2 on 2016-08-22
If I'm reading the ALSA-Project '[Vendor Creative Labs page]("http://alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs")' correctly, I think you may to check if you have a driver for the emu10k1 chipset.


I'm using USB to MIDI controllers, so I can't give you much guidance on how to do that, other than direct you to the Ubuntu Studio Preparations page under the subsection titled "[specific supported hardware]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Specific_supported_hardware")."


You may also find some relief via the same community in the page titled '[HowToSetupSoundCards]("https://help.ubuntu.com/community/HowToSetupSoundCards").'


As for your Studio 64x. I've got its successor, the Studio 128x. What I've opted to do is simply drive a MIDI-THRU broadcast into the front-facing port 8 jack, effectively using the device as a secondary patch bay.


Instead, I picked up an emagic AMT8 off of Craigslist, which while it doesn't support SMPTE like the Studio 128x, gets the job done for now. I suppose if I ever work with film, I'll look for an inexpensive USB to RS232 interface with which to experiment.

---

