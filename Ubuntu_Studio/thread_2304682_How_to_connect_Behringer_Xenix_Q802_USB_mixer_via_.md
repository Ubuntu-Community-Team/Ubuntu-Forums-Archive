---
title: "How to connect Behringer Xenix Q802 USB mixer via JACK?"
date: 2015-11-29
forum: Ubuntu Studio
---

### Post by charlessmall18 on 2015-11-29
Can anyone explain in terms a not very computer literate PR-agency person can understand (if it is possible to accomplish at all) how to connect a Behringer Xenix USB audio mixer to the JACK-compatible programs in Ubuntu Studio using QjackCtl? I am running the latest version of Ubuntu Studio and my PC has an i7 processor and lots of RAM.
The roster of Ubuntu Studio supported hardware lists, among others, the functionally very similar Focusrite Scarlett 2i2. Compatibility seems to have something to do with a "snd-usb-audio module." But that sort of thing is WAY over my pay grade.
If it's no go with the Behringer, I'll get a PO cut for the Scarlett. But I would prefer not to if the Behringer can be made to work. 
I did try as hard as I could to figure out how to do this on my own. For example, I did manage to wade my way through the documentation to the point where I figured out what the "card number" for my mixer is and that it has a Texas Instruments DAC:
card 4: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
I checked and my user is indeed in the "audio" group. At one point, I attempted a brute force solution by methodically trying all combinations of inputs in QjackCtl's Preferences. No joy. Much of the advice I could find said to use a Sound wizard in Settings. I can find no such wizard in Settings Manager.
Here are some - to me - puzzling clues: When I start Audacity under Ubuntu Studio, just like when I run it under Windows, the choice of input from my Behringer mixer is offered in the box by the little mic icon  as well as, I might mention, in the box next to the little speaker icon, the output to my Topping USB Class D audio amplifier is offered as well (which amp powers my JPL passive monitor speakers). Audacity works perfectly, no problems. Ditto for Audacious. Right out of the box, when I play MP3s with Audacious, the sound comes out via my Topping amp's DAC. With JACK, I have been unable to convince route inputs from my mixer or to send sound to my USB Topping audio amplifier's DAC. Luckily, my amplifier has a front panel switch that shifts the input to the amp from the USB to a cable running to that little green socket on the back of my PC. So I can at least listen to the output of JACK-compatible programs with my JBLs instead of my cheesy powered computer speakers.
I suspect that Pulse Audio and ALSA are a factor in my difficulties but the more I read about them, the more confused I got.
It's not all bad news. Connecting my M-Audio MIDI controller was a snap! That worked exactly as advertised. Thanks!

---

### Post by charlessmall18 on 2015-12-01
Problem Solved.

I ran the following command line queries:

chuck@HP-700-Ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: 92HD89E2 Analog [92HD89E2 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: 92HD89E2 Digital [92HD89E2 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: DAC [USB Audio DAC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
chuck@HP-700-Ubuntu:~$ 


chuck@HP-700-Ubuntu:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: 92HD89E2 Analog [92HD89E2 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: 92HD89E2 Alt Analog [92HD89E2 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: CinemaTM [Microsoft® LifeCam Cinema(TM)], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


chuck@HP-700-Ubuntu:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7310000 irq 45
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 17
 2 [DAC            ]: USB-Audio - USB Audio DAC
                      Burr-Brown from TI USB Audio DAC at usb-0000:00:14.0-2.3, full speed
 3 [CinemaTM       ]: USB-Audio - Microsoft® LifeCam Cinema(TM)
                      Microsoft Microsoft® LifeCam Cinema(TM) at usb-0000:00:14.0-2.4, high speed
 4 [CODEC          ]: USB-Audio - USB Audio CODEC
                      Burr-Brown from TI USB Audio CODEC at usb-0000:00:14.0-10.1.4, full speed


chuck@HP-700-Ubuntu:~$ cat /proc/asound/devices
  1:        : sequencer
  2: [ 0]   : control
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 2]: digital audio capture
  7: [ 0- 0]: hardware dependent
  8: [ 1]   : control
  9: [ 1- 3]: digital audio playback
 10: [ 1- 7]: digital audio playback
 11: [ 1- 8]: digital audio playback
 12: [ 1- 0]: hardware dependent
 13: [ 2]   : control
 14: [ 2- 0]: digital audio playback
 15: [ 3]   : control
 16: [ 3- 0]: digital audio capture
 17: [ 4]   : control
 18: [ 4- 0]: digital audio playback
 19: [ 4- 0]: digital audio capture
 33:        : timer

Then in QjackCtl I changed Interface from (default) to hw:CODEC from among the choices offered when I clicked on the right arrow next to the Interface field.

hw:CH
hw:CH,0
hw:CH,2
hw:Nvidia
hw:DAC
hw:CinemaTM
hw:CionemaTM,0
hw:CODEC.............USB Audio CODEC (hw:4)
hw:CODEC,0..................USB Audio (hw:4,0)

Then I changed Audio from (default)  to Capture Only from the selections offered in the Audio field.

Then I saved that setup. "Always backup." Right!

And now the Behringer mixer, which has all the usual analog mixer controls that we know and love, comes out of System, Capture_1 and Capture_2 in the Readable Clients / Output Ports left-hand pane of the Audio tab of the Connections wizard and it connects just fine to other programs' inputs.

---

