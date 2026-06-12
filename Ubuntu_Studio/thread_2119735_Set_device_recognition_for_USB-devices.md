---
title: "Set device recognition for USB-devices"
date: 2013-02-24
forum: Ubuntu Studio
---

### Post by sirriffsalot on 2013-02-24
Hi!

I have two USB-driven audio devices that I would love to have the Patchbay in QJackCtl route automatically as I please, but when I use the alsa_in -dhw:1 and alsa_in -dhw:2 commands for them to enter JACKD's routing-abilities, there is a problem in that they are never surely the alsa_in or alsa_in-01 names that I configured in the Patchbay the last time.. In other words I often get my microphone recording in the guitar tracks and vice versa..

Hence I wonder if there a way to have a set ID for these two devices so that one device always becomes alsa_in in the QJackCtl connections tab and the other always alsa_in-01?

I've tried these 

[http://alsa.opensrc.org/MultipleUSBAudioDevices](http://alsa.opensrc.org/MultipleUSBAudioDevices)

[http://alsa.opensrc.org/Udev](http://alsa.opensrc.org/Udev)

... but I can't work out how this can help my problem, even though someone in IRC suggested the first link to me. Tried what the Udev link suggests, but it doesn't get me anywhere, and the other link is outdated for my use; I have no /etc/modules.conf, or /etc/modprobe.conf files as my kernel is way newer than the one the guide handles.. Any suggestions?

Thanks for taking the time!

:guitar:

---

### Post by jejeman on 2013-02-24
Are you using both USB cards at the same time with JACK? I would like to see the JACKd command for that.

---

### Post by sirriffsalot on 2013-02-24
Hi!

There is no JACK command for that, but a terminal command rather, that I mentioned being 

```
 alsa_in -dhw:1 
``` 

and 

```
 alsa_in -dhw:2 
``` 

To be specific I have a Komplete Audio 6 audio interface and a Mustang I amplifier - both USB-driven.

I keybind those commands to alt + 1 and alt + 2 so I can get them both up quickly. Hope that helps you, and someone else reading this to help me! :D

Edit: alsa_in and alsa_out commands are jack clients.. If that makes the "... there is no JACK command for that" false or not I am not sure, hehe.

---

### Post by sirriffsalot on 2013-02-26
bump

No one on this yet? Someone has suggested that creating a script of some kind could do the trick, but was not sure how this would be done since the person cannot be here to actually show me. Anyone got any ideas?

Cheers.

---

### Post by sirriffsalot on 2013-02-27
bump:)

I don't mind the solution approach, as long as it is a solution!

---

### Post by sirriffsalot on 2013-02-28
So many bumps ... so little time

---

### Post by sirriffsalot on 2013-03-03
Alright, I finally got it!alsa_in is one way to go, in which case you do the following:**The udev** rules are mostly intended for situations whereby two USB-devices have the same ID's (this is not exactly true, but for the purposes of this issue it makes sense to say), at which point you really have to get into the nitty-gritty of things. As far as my problem is concerned, that is not the case. If you do alsa_in --help, you will see many options, but the one we are interested in is -j; which sets the client name for the device/usb you are "alsa_inning", if you like. When you have the capability to do that, you can from there configure the Patchbay to grab the name you have already set with the -j command, and connect it anywhere you like. However in order to get the right device set, with the desired name, by the use the command we will be seeing soon, it is important that you get the name/ID of the device you want to use the -j command on. To find out what your USB-device has as ID, do```
 cat /proc/asound/cards/ 
```and find your device name. In my case it is this: 2 [K6             ]: USB-Audio - Komplete Audio 6. What we are after is what is in the "[ ]" brackets. This is the information (ID) you will use with the -j command. The reason for using the -j command is that when you boot your computer up, either with or without the USB-devices already plugged, the USB-bus order in which they are registered in on your hardware may change from boot to boot, so sticking to "alsa_in -dhw:1" (standing for device hardware:1) will not suffice if you want reliable Patchbay automation. Secondly, therefore, when you change the -dhw: value from a number, to the IDs we saw earlier, you are always assured that what you are routing now is always, in my case, the Komplete Audio 6, or whatever device you wish to route with the ID you find when running the "cat" command. So:For alsa_in, the command will be as follows```
 alsa_in -j (desiredname) -dhw:(deviceID) 
```in my case, since I use my Komplete Audio 6 mostly for microphone recording, this would be```
 alsa_in -j Microphone -dhw:K6 
```If you're still with me so far, congratulations, now all you have to do is get things sorted out in the Patchbay and you can have your studio ready in one tenth of the time you normally spend hooking everything up!-----------------------**Another option** was brought to my attention however, which apparently is much better both in terms of audio quality and configuration abilities. For more information, read: [http://kokkinizita.linuxaudio.org/linuxaudio/zita-ajbridge-doc/quickguide.html](http://kokkinizita.linuxaudio.org/linuxaudio/zita-ajbridge-doc/quickguide.html) The procedure for this is basically the same, but you will have to get it installed yourself as it is as of this writing not a part of the official Ubuntu release, however Debian has it in it's package lists, along with Ubuntu, which means it is legit. As of writing, I got the packages for zita-ajbridge, and all it's dependencies here: [http://packages.ubuntu.com/quantal/zita-ajbridge](http://packages.ubuntu.com/quantal/zita-ajbridge).Once you have zita-ajbridge (zita-a2j) installed, you go with the same info I mentioned earlier with the "cat /proc/cards/asound/cards" command, and do the following command```
 zita-a2j -c (numberofchannels) -j (desiredname) -dhw:(deviceid) 
```in my case this would then be  ```
 zita-a2j -c 6 -j Microphone -dhw:K6 
```If you are unsure how many channels your device actually should output, find out with alsa_in first which does this automatically, then use zita-a2j, but I think it works out to just leave out the -c command in most cases, unless of course you want to exclude certain frivolous channels.Note that sometimes it will be necessary to include the -r (rate) command for the sample rate value your device is running on - where (rate) is replaced by the desired rate; e.g. 44100. The default for zita-ajbridge is 48000, whereas my devices are all 44100. Read more about additional settings by doing```
 man zita-a2j 
```in a terminal.Hope this helped someone not forget their riffs!

---

