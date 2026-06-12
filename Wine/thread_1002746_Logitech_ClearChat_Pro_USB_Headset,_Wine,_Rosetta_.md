---
title: "Logitech ClearChat Pro USB Headset, Wine, Rosetta Stone, and a Headache"
date: 2008-12-05
forum: Wine
---

### Post by abclemons on 2008-12-05
I'll preface this with the fact that I know several others have posted this same issue, but there have been no breakthroughs. 

Here is my issue. The headset works in all native Ubuntu apps. Wine 1.1.9, specifically Rosetta Stone, is my problem. I have the headset configured in my .asoundrc as the pcm default for playback and capture. I have Ubuntu 8.04 x86_64; so I know Wine may just not like my 64 system. Here some more details:

```
$lsusb
Bus 002 Device 003: ID 0c45:62c0 Microdia
Bus 002 Device 002: ID 0bc2:3110 Seagate RSS LLC
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 011: ID 046d:0a0b Logitech, Inc.
Bus 001 Device 010: ID 03f0:5511 Hewlett-Packard
Bus 001 Device 001: ID 0000:0000 
```

```
$ arecord -l
 **** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

.asoundrc is set up as follows:

```
pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:1,0"
}
capture.pcm {
type plug
slave.pcm "hw:1,0"
}
}
```

Now, here is the output when I start an exe in Wine (This instance was Rosetta Stone) :
```
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Logitech USB Headset, disabling mixer
```

Rosetta Stone pushes sound to the headset; thus there is not a complete malfunction. The issue seems to be with the microphone itself. I have attempted to point RS to the mic (via the internal settings in RS), but the mic does not even show up. Additionally, the error occurs with other programs, but those programs interface with the headset without problem.
 
The final thing I have attempted is to put a registry key into Wine's regedit for the ALSA Driver. I included only one string to make Wine detect all PCM devices. That was the last attempt I made with no results to show.

At this point, I believe I may need the modules for the headset or may need to do some configuration on the asound.conf or asound.state(?). Any advice/guidance would be thoroughly appreciated.



Cheers,
-Aaron

---

### Post by Vargas on 2009-01-08
Hey.
Unfortunately I do not have an answer for you but rather a question.
I've been looking into getting this headset for myself but it's rather important that it works both on Vista and Ubuntu.
I know it obviously works in Vista but I wanted to ask you if you've had any issues getting it to work on Ubuntu (8.10 specifically).
I'm specially interested in music playback and skype. thanks!!

---

### Post by minispalla on 2009-01-25
Yeah, i am about to buy this same headset but i would also like to know if this will work in ubuntu 8.10 and how the skype quality is? 

thank you for your time :)

---

### Post by Vargas on 2009-01-25
> **minispalla said:**
> Yeah, i am about to buy this same headset but i would also like to know if this will work in ubuntu 8.10 and how the skype quality is? 

thank you for your time :)

Seeing this many questions I can't help to think how sad it is that Logitech refuses to provide any kind of support for Linux.
One might wonder if they'd loose something if they did.

---

### Post by minispalla on 2009-01-25
So there is absolutely NO WAY to get this to work in ubuntu 8.10?

---

### Post by Vargas on 2009-01-26
> **minispalla said:**
> So there is absolutely NO WAY to get this to work in ubuntu 8.10?


The first post on that thread says it does on Ubuntu native apps
But doesn't say to what extent.
Still, I'm waiting to see if anyone posts a more straightforward answer

---

### Post by minispalla on 2009-01-26
I picked up the logitech ClearChat Pro USB 
[http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3296232&csid=ITD&body=MAIN](http://www.tigerdirect.com/applications/searchtools/item-details.asp?EdpNo=3296232&csid=ITD&body=MAIN)

and i would have to say the plug and play is great for all native apps works great in skype and i havent tested wine but i can if the person would like me to

---

### Post by OrbJinzo on 2009-01-26
you can always try to get it configured in pulseaudio but as to how id have no clue. You prolly gonna have to get head with a headphone and mic input as i had to do.

---

### Post by Vargas on 2009-01-27
> **OrbJinzo said:**
> you can always try to get it configured in pulseaudio but as to how id have no clue. You prolly gonna have to get head with a headphone and mic input as i had to do.

Is it only me who thinks this shouldn't have to be this hard to get these kind of things working??
I gotta say, I LOVE Linux and specially Ubuntu but I wish there was a way to make the industry more supportive.

---

### Post by OrbJinzo on 2009-01-27
> **Vargas said:**
> Is it only me who thinks this shouldn't have to be this hard to get these kind of things working??
I gotta say, I LOVE Linux and specially Ubuntu but I wish there was a way to make the industry more supportive.

its not the support problem is a problem with drivers and USB headsets have really bad support in general. I always remove pulseaudio in any ubuntu install by default and i have never used it so i dont know how to use it. 

I can give a suggestion on getting a non usb headset but thats all i can say.

---

### Post by Xzilalnx2 on 2009-05-14
Sound Preferences:(window)
   Devices(tab)
      Sound Events:
         -Sound playback: Autodetect
       Music and Movies:
          -Sound playback: Autodetect
       Audio Conferencing:
          -Sound playback: C-Media USB Audio Device USB Audio (OSS)
          -Sound capture: C-Media USB Audio Device USB Audio (ALSA)
       Default Mixer Tracks:
          Device: C-Media USB Audio Device   (Alsa mixer)



I have tried the .asoundrc to my home directory, and the wine config tool still does not detect any alsa USB.

In the wine config tool under the "audio" tab I have alsa checked, but all the sub-directories are "default"

I tried editing the regestry using the old windows regedit in /home/user/.wine/dosdevices/c:/windows to add the alsa drive to wine. This seems a failure.

The Rosetta Stone detection always fails, though I can get the "sound recorder" in ubuntu to record my voice.

---

### Post by jcb081584 on 2009-05-15
I read somewhere several months ago that wine does not support audio input, only output.  I'm running into a similar problem in that I'm using Rosetta Stone but can't get the mic on my pc to work.  I don't think it's a Linux problem just a feature that Wine currently does not support.  Perhaps if there is a new version down the road we'll be able to have it but I think that until then we're out of luck.  My next try is to use a Virtual Machine running Windows to try and get it to work.  Using Virt-Manager I have gotten it installed and the audio out works it's just a little buggy and has a tendency to scratch and skip a bit.  I have not yet tested the audio input to see if it works.  I'll post when i do. Hope this helps.

---

### Post by Xzilalnx2 on 2009-05-15
There does appear to be a few successes with people who have tried to fix the problem. I'm not sure if it is because I have a dif version of: Ubuntu, rosetta stone, or wine. The options in wine look like they were meant to have the ability for audio in and out. So I'm thoroughly confused.

---

### Post by Kmus on 2009-08-20
Hi, 

I have also a Logitech ClearChat Pro USB Headset and this is what I did to make it work under wine (I'm under Ubuntu 9.04 but should work the same in any other version):

1. From a linux shell run "arecord -l" this will give you the list of your capture devices, search for 
...
card X: Headset [Logitech USB Headset], device Y: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
...

Write somewhere your "card X" and "device Y" values.

2. From a linux shell run "aplay -l" this will give you the list of your playback devices,
search for
...
card A: Headset [Logitech USB Headset], device B: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
...

Write somewhere your "card A" and "device B" values.


Then create the following file in your home directory as .asoundrc
Code:
pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:A,B"
}
capture.pcm {
type plug
slave.pcm "hw:X,Y"
}
}

NOTE: A,B,X,Y are digits so change them with yours.

3. From a linux shell run "winecfg", go to Audio tab and select Alsa and test sound (it should work).

Hope it helps!! :P

---

### Post by Norri on 2009-08-24
That helped a lot! Thanks!

---

### Post by Cypher1101 on 2009-11-27
On the topic of USB headsets and which work well with ubuntu and windows, I use a Microsoft Lifechat headset and with pulseaudio, and it works great. Now, I had to use pulseaudio because alsa didn't work with it all. I don't use WINE, so I don't know how well my set up works for that. However I wanted to help out people looking for a usb headset that works with ubuntu itself, as well as mention that pulseaudio is actually pretty nice, since a lot of people seem to hate it. If you have multiple audio devices, ie a headset and speakers, Pulse makes switching between them much easier.

edit: using the pulse audio device chooser applet (padevchooser) wine and my usb headset work together fine now.

---

