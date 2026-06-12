---
title: "Guitar Rig 3 + Guitar Control 2 in Maverick Meerkat + Wine"
date: 2010-12-12
forum: Ubuntu Studio
---

### Post by mvalente on 2010-12-12
I've been banging my head for the last couple of days trying to get GR3 (and the Kontrol hw) running on Ubuntu Maverick under wine. I know that it is possible, but I just cant seem to get it.

Drivers (caiaq) are already installed and working: in System/Preferences/Sound I can setup the HW as the default audio board and I get input and output.

The GR3 software is working already under Wine.

WineASIO is installed.

JACK is installed and I think I have the right settings.

Problems:

- whenever I connect the HW, the mouse starts going crazy jumping all around the screen

- even with the mouse jumping around I can start JackCtl, start G3 software under Wine and select and configure it.

- I strum the guitar and the Kontrol HW volume monitor lights up. But the volume monitor in the GR3 software doesnt light up.

I've tried everything I could think of, and I still cant get it to work. Its the only thing that still makes me go back to Windows once in a while.

Any help is apreciated

-- MV

PS - Here is the output of some of the relevant configurations

valente@DellPrecision530:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c504 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 17cc:1940 Native Instruments RigKontrol3
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


root@DellPrecision530:/proc# lsmod | grep caiaq
snd_usb_caiaq          19718  2 
snd_pcm                70694  4 snd_intel8x0,snd_ac97_codec,snd_usb_caiaq,snd_pcm_oss
snd_rawmidi            19056  2 snd_usb_caiaq,snd_seq_midi
snd                    54180  15 snd_intel8x0,snd_ac97_codec,snd_usb_caiaq,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device


root@DellPrecision530:/proc/asound# cat cards 
 0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                      Intel 82801BA-ICH2 with AD1885 at irq 17
root@DellPrecision530:/proc/asound# cat devices 
  2:        : timer
  3:        : sequencer
  8: [ 0- 1]: digital audio capture
  9: [ 0- 0]: digital audio playback
 10: [ 0- 0]: digital audio capture
 11: [ 0]   : control
root@DellPrecision530:/proc/asound# clear


root@DellPrecision530:/proc/asound# cat cards; cat devices 
 0 [I82801BAICH2   ]: ICH - Intel 82801BA-ICH2
                      Intel 82801BA-ICH2 with AD1885 at irq 17
 1 [RigKontrol3    ]: snd-usb-caiaq - RigKontrol3
                      Native Instruments RigKontrol3 (usb-0000:04:0f.2-3)
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: raw midi
  5: [ 1- 0]: digital audio playback
  6: [ 1- 0]: digital audio capture
  7: [ 1]   : control
  8: [ 0- 1]: digital audio capture
  9: [ 0- 0]: digital audio playback
 10: [ 0- 0]: digital audio capture
 11: [ 0]   : control

[IMG]http://www.flickr.com/photos/mfvalente/5255156116/lightbox/[/IMG]

---

### Post by sgx on 2010-12-12
Hi, try installing Reaper, and use it for your vst host. Currently,
and for a long tome, it has been the best and easiest way to use vsts
in wine. You will need a folder path like this:
/hpme/username/.wine/drive_c/Profram Files/Steinberg/VstPligins

Put the GR3 .dll file in VstPlugins.

The mouse and interface may need to be experimented with, is it a usb mouse?
if so, try starting the computer with the interface unplugged, then plug it in and see if the mouse is dancing, and try different usb ports, don't use a hub with the interface, maybe try a keyboard containing a trackball,
whatever it takes, victory will be yours soon.. A PS2 mouse might help if you have such a connector.

Google the brand and type of mouse with xorg.

Cheers

---

### Post by Nareto on 2010-12-27
Hello, I have a rig kontrol 2. The pedal and the buttons actually act like a keyboard and mouse- if you press button 1 when the cursor is somewhere where you would normally enter text (gedit for example) you'll see a 1 appear. The pedal instead somehow acts as a mouse.

That's actually written into the driver "caiaq" to make it possible to use the pedal even under linux. I for example have made a supercollider program that outputs midi when you press buttons and move the pedal - the program also "grabs" the pedal so that it doesn't act as a keyboard+mouse thing anymore.

Do you want me to post this somewhere? You'll need supercollider (not too much of a hassle)

On the software thing can't help you. Only now I'm looking into using guitar rig under wine - till now used the excellent open software avaiable (rakarrack especially).

---

