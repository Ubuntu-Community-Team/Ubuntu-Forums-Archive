---
title: "Audio configuration for Edirol SD-90"
date: 2010-04-21
forum: Ubuntu Studio
---

### Post by Lomedhi on 2010-04-21
I've just installed Ubuntu Studio 9.10, and am trying to get audio configured for my Edirol SD-90. I have tried to make sense of the information at the locations below, but it seems to be out of date:

[INDENT][http://georgia.ubuntuforums.org/showthread.php?t=887929](http://georgia.ubuntuforums.org/showthread.php?t=887929)

[http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio](http://www.alsa-project.org/main/index.php/Matrix:Module-usb-audio)[/INDENT]

Where I'm at right now:

No devices are listed on the Hardware tab in Sound Preferences.

cat /proc/asound/cards returns:

>  1 [SD90           ]: USB-Audio - SD-90
                      EDIROL SD-90 at usb-0000:00:1d.1-1, full speed

I'm an IT pro, but relatively new to Linux. I would really like to switch from Windows to Ubuntu for audio and video editing, because that's where all the best tools seem to be. Any help would be greatly appreciated. Let me know what other information you need.

---

### Post by AutoStatic on 2010-04-21
Hello Lomedhi, the card is being recognised but it seems PulseAudio (Sound Prefences is part of PulseAudio) doesn't pick it up. That shouldn't be a problem because editors like Audacity should work with your card anyway. If you add the device toolbar in Audacity (View - Toolbars - Device Toolbar) you should be able to select your card as the input and/or output device.
Do you have any other plans with the card? You might want to take a look at JACK: [https://help.ubuntu.com/community/What%20is%20JACK](https://help.ubuntu.com/community/What%20is%20JACK)

---

### Post by Lomedhi on 2010-04-21
Thanks for the suggestion.

In Audacity, my choices for input and output devices are "ALSA: default" and "ALSA: pulse", neither of which produces any output on my SD-90.

---

### Post by Lomedhi on 2010-04-23
Can anyone help me out here? I'm sure the solution is not complicated; I'm just not familiar with Linux sound architecture and what belongs in which configuration files.

---

### Post by AutoStatic on 2010-04-24
Could you please also post the output of **aplay -l** and **arecord -l** ? And in Audacity - Edit - Preferences - Devices - Interface - Host you probably set OSS, that should be ALSA. [OSS (Open Sound System)]("http://www.opensound.com/") is not installed on Ubuntu, it's a backend like ALSA also, but Ubuntu uses ALSA, not OSS, so it's no use using OSS in Audacity.
And concerning Linux's audio architecture: [ALSA]("http://www.alsa-project.org/main/index.php/Main_Page") is the backend, the driver stack that talks directly to the kernel and produces the actual sound.
Then there are several frontends, sound servers/daemons like PulseAudio and JACK. PulseAudio is a day to day "consumer" daemon that allows different apps producing sound work together nicely (like your browser, VLC, music player). JACK is the "professional" daemon that allows low latencies and is more suited for music software.
Unfortunately there are a gazillion of other, more or less uncommon sound daemons like PortAudio, used by Audacity.

---

### Post by Lomedhi on 2010-04-24
Thanks for responding again.

aplay -l and arecord -l show no devices (below), even though cat /proc/asound/cards shows that the SD-90 was detected. You can also view my output of the ALSA Information Script at [http://www.alsa-project.org/db/?f=7c8f52674140e2512c5095ff2c03e2f258280819](http://www.alsa-project.org/db/?f=7c8f52674140e2512c5095ff2c03e2f258280819) if that helps.

Do I need to add different options for snd_usb_audio? I can't seem to find any information on what they should be for the SD-90. I'm not sure if I have all the right device nodes either.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****

arecord -l
**** List of CAPTURE Hardware Devices ****

cat /proc/asound/cards
 1 [SD90           ]: USB-Audio - SD-90
                      EDIROL SD-90 at usb-0000:00:1d.1-1, full speed

cat /proc/asound/modules
 1 snd_usb_audio
```

Thanks for sharing your expertise. I really appreciate it.

---

### Post by AutoStatic on 2010-04-24
I think the MIDI part is correctly being handled but not the audio part. This is probably because the audio part is being handled by a different sound module (ICE1712). So you could try to load that one with **sudo modprobe snd-ice1712** and try **aplay -l** to check if ALSA recognises your SD-90 this time.

Source where I got this info from: [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg09030.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg09030.html)

---

### Post by Lomedhi on 2010-04-24
I'm afraid I still see no playback devices.

I didn't mention clearly before that this is an external USB device. Does that make a difference in the approach to troubleshooting?

---

### Post by AutoStatic on 2010-04-24
Yup, I know it's an USB device, got the manual right in front of me :) And what if you unplug and plug in the device with the ice1712 module loaded?
And is it possible to open a terminal and have **dmesg | tail -f** running in that terminal window? And then unplug and plug in the SD-90? Could you post the output that appears in the terminal window?

---

### Post by Lomedhi on 2010-04-24
aplay -l still shows no playback devices after loading snd-ice1712 and disconnecting/reconnecting the device. Here is the dmesg output (I disconnected/reconnected a few times):

```
[ 2043.460589] usbcore: registered new interface driver snd-usb-audio
[ 3996.501072] usb 3-1: USB disconnect, address 2
[ 4030.740050] usb 3-1: new full speed USB device using uhci_hcd and address 3
[ 4030.914190] usb 3-1: configuration #1 chosen from 1 choice
[ 4065.251073] usb 3-1: USB disconnect, address 3
[ 4085.307047] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 4085.531213] usb 3-1: configuration #1 chosen from 1 choice
[ 4221.251077] usb 3-1: USB disconnect, address 4
[ 4232.039043] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 4232.214198] usb 3-1: configuration #1 chosen from 1 choice

```

---

### Post by AutoStatic on 2010-04-24
Gee, that isn't very helpful :(
I'm running out of options. Info on your card is scarce, it's quite an exotic beast and the manual states it's from 2001. But it should work. Maybe you could post a request for help on the Alsa User mailinglist? Afaik Clemens Ladisch is still one of the main USB ALSA dev's so maybe he could help you out.

---

### Post by Lomedhi on 2010-04-24
I will do that. Thanks very much for all your help.

---

### Post by Lomedhi on 2010-04-28
Clemens really helped me out. He had me download ALSA 1.0.23, make a change to the usb/quirks-table.h file and compile it. I now have sound, but it is strange. It's distorted; there's a lot of static, it's only on the left channel, and it sounds like it's being modulated by a low frequency. Are there parameters somewhere that I should play with?

---

### Post by Lomedhi on 2010-04-28
Once I at least had distorted sound, I explored the options available from the front panel of the SD-90. I changed "USB Driver" from "Vender" [sic] to "Generic", and my sound is now working perfectly! Many thanks to AutoStatic and Clemens Ladisch.

See this thread for details:
[http://thread.gmane.org/gmane.linux.alsa.user/34251](http://thread.gmane.org/gmane.linux.alsa.user/34251)

---

### Post by AutoStatic on 2010-04-28
So it works? Awesome! Glad I could help!

---

