---
title: "Digidesign Eleven Rack - Any chance?"
date: 2013-10-31
forum: Ubuntu Studio
---

### Post by aidan.schurr on 2013-10-31
Hi all

I have a hybrid install of Ubuntu Gnome 13.04 64 bit with Studio packages added after the fact (due to some install challenges which I won't go in to here...).  Am /this/ close to having it as my daily driver, save for one last thing - I can't get my Eleven Rack to work...

It's not on the Alsa list, and I also know it's not utilising a standard implementation of the generic USB audio system (or so I've read).  But, Alsa does seem to recognise it, and that gives me hope!!

Here's what Alsamixer shows me:

[IMG]https://lh6.googleusercontent.com/-LpIN2mIsPik/UnIefKn97dI/AAAAAAAABX0/lvYtfjQwN6I/w895-h605-no/Screenshot+from+2013-10-31+19%253A53%253A02.png[/IMG]

But, when I select the Eleven Rack, it just tell me "This sound device does not have any controls"

Is there hope, or is this a lost cause?!
Thanks

---

### Post by jejeman on 2013-10-31
Give
```
lsusb
aplay -l
arecord -l
lsmod | grep -i snd
```

---

### Post by aidan.schurr on 2013-10-31
Thanks jejeman:

```
axis@GruntrUbunut:~$ lsusbBus 001 Device 006: ID 0dba:b011  
Bus 003 Device 002: ID 0c45:602a Microdia Meade ETX-105EC Camera
Bus 003 Device 003: ID 045e:0059 Microsoft Corp. Wireless IntelliMouse Explorer
Bus 004 Device 002: ID 04b4:4100 Cypress Semiconductor Corp. 
Bus 005 Device 002: ID 08bb:2900 Texas Instruments Japan PCM2900 Audio Codec
Bus 008 Device 002: ID 088e:5036 iLok Portable secure storage for software licenses
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```

```
axis@GruntrUbunut:~$ aplay -l**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

```
axis@GruntrUbunut:~$ arecord -l**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC889A Analog [ALC889A Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

```
axis@GruntrUbunut:~$ lsmod | grep -i snd
snd_usb_audio         140732  2 
snd_usbmidi_lib        24938  1 snd_usb_audio
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  3 
snd_hda_codec         136498  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  3 snd_usb_audio,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  21 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd



```

The ALC889A is going to be the onboard sound (which I can't switch off in the BIOS), the USB Audio is my Alesis M1 Active USB monitors. So, no Eleven Rack there that I can see. Note that "Card 1" is missing; I have restarted since the above screenshot and just checked Alsamixer - it's now showing the Eleven Rack as HW1, so this corresponds...

---

### Post by jejeman on 2013-10-31
It obviosly need a different description on the driver level.
It has to have it's own ALSA driver, as you said device is not generic.
I think the only way for this to work is for you to try to help (somehow) ALSA developers to make the driver.

---

### Post by aidan.schurr on 2013-10-31
> **jejeman said:**
> It obviosly need a different description on the driver level.
It has to have it's own ALSA driver, as you said device is not generic.
I think the only way for this to work is for you to try to help (somehow) ALSA developers to make the driver.

Damn, was hoping you wouldn't say that :-\

---

### Post by jejeman on 2013-10-31
You should troubleshoot this with ALSA developers, maybe it needs just different configuration not the "whole" new driver.

That is my opinion. Wait for others to say theirs.

---

### Post by aidan.schurr on 2013-10-31
Thanks, appreciate the help and feedback. Have dropped a note to the Alsa dev mailing list - will see what comes of that...

In the meantime, any additional thoughts are very much appreciated.

---

