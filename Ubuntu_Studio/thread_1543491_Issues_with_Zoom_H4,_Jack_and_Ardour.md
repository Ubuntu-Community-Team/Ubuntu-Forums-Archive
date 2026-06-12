---
title: "Issues with Zoom H4, Jack and Ardour"
date: 2010-08-01
forum: Ubuntu Studio
---

### Post by Rockmonster on 2010-08-01
Hello!

I've been trying to use my Zoom H4 with Jack and Ardour but not success. I have gone through [this post]("http://ubuntuforums.org/showthread.php?t=1362010") tried the suggestions but still can't get the H4 to act as an input. 

Output of lsusb is: 

Bus 002 Device 004: ID 1686:0045 ZOOM Corporation H4 Digital Recorder
Bus 002 Device 003: ID 046d:c52f Logitech, Inc. 
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 003: ID 04a9:263c Canon, Inc. Smartbase MP360
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Output of iplay -l is: 

**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 ZS [SB0350]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: H4 [H4], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


So Ubuntu can see it. And Jack does as well. It is hw:1 which I've selected as an input device. And if I choose the output to be hw:1 then I can hear the output on Ardour on the H4. But the H4 will not act as an input for Ardour. I can't hear it nor does it record any guitar. 

So I figure I've missed one small step but be buggered if I can work out what it is. Any suggestions?

---

### Post by cchhrriiss121212 on 2010-08-01
Did you try using hw:H4 instead of hw:1?
Also open up alsamixer and check your capture level is not muted.

---

### Post by sgx on 2010-08-01
lsmod

run the lsmod command, and look in the output for something like

snd_usb_audio

If nothing like that is there, try

sudo modprobe snd_usb_audio

Is there a Creative Labs sound device in your system, or does the H4
utilize their chips? Remove the device if it exists, then test again.
Put a constant sound source into the H4 so you will hear it when you find the mystery kabucki port;)

---

### Post by Rockmonster on 2010-08-02
Thanks for the tips. 

lsmod showed all the right output so decided to try and see if the H4 worked with Audacity, which it did. So that lead me to believe that Ardour was the issue. 

So some more experimenting and I stumbled onto the idea that the sampling rate could be the problem. Ardour was running at 48k and Jack and the H4 at 41K., Set everything to 48k and whadya know? It started working. 

Appreciated the help and thanks again.

---

