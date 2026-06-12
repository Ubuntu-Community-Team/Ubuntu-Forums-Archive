---
title: "another jack audio connection problem"
date: 2016-11-02
forum: Ubuntu Studio
---

### Post by bulevardi on 2016-11-02
Hi all !

Since my wife took over my regular desk (with windows pc), I moved to my spare pc, where I freshly installed the Xenial Xerus Ubuntu Studio version.
I'm quite new to Linux btw.

I want to create music with a Midi Controller (akai mpk mini), and have a USB Plantronics headset to listen the music.

So I want to use LMMS or Rosegarden to begin with, or maybe Qtractor and Ardour later on. 
Anyway, first of all, it seems I need to use a Jack server to be able to route the sound right? 
I tried with QjackCtl, but always getting errors that he cannot connect to the server.

 > ALSA: cannot configure capture channel

 Cannot initialize driver
 JackServer::Open failed with -1
 Failed to open server
 [COLOR=#999999]19:52:05.199 JACK is gestopt[/COLOR]
 [COLOR=#ff0000]19:52:08.337 Kon niet verbinden als client met de JACK server. - Gehele toepassing gefaald. - Kan niet met de server verbinden. Gelieve het berichten venster te lezen voor meer info.[/COLOR]
 Cannot connect to server socket err = Bestand of map bestaat niet
 Cannot connect to server request channel
 jack server is not running or cannot be started
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock
 JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for 4294967295, skipping unlock



I already tried the instructions on the manual page:
[https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro)

I'm obviously doing stuff wrong. 
Below some screenshots:

[IMG]http://users.telenet.be/bulevardi/tmp/screen1.png[/IMG]

[IMG]http://users.telenet.be/bulevardi/tmp/screen2.png[/IMG]

Anyone can help me further?
Thanks in advance!

---

### Post by CrocoDuck on 2016-11-02
Hi! I don't understand the language of the interface (is that dutch?) but I have the feeling that jack it is not liking too much the way you specified the Input and Output Devices.

I get you want to use your akai as **MIDI** input and your headphones as **audio** output. You put akai in the Input field and your headphone in the Output field. This seems legit... but it is not. The fields in that picture are for **audio** only. MIDI does not need to be configured there. Once you launch jack you will see all your midi devices in the ALSA and MIDI tabs of the connection window.

You can either specify a full duplex audio interface for input and output or, if you don't need any audio input, just go playback only and select the headphones as output.

[This]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack") should help you further.

---

### Post by bulevardi on 2016-11-03
I see... changed a few things here, right now, still gave me the same error :(

I came up to this error: [SIZE=2]
[/SIZE]**[SIZE=2]"D-BUS: JACK server could not be started"[/SIZE]**

I read somewhere that I had to do the following command
"killall -9 jackdbus"
Now he runs ... without errors.
He now seems to record the signals from my midi keyboard in rosegarden, but** I still get no sound out of my headset.**

The language on the screenshots is Dutch indeed !

---

### Post by bulevardi on 2016-11-03
What I don't understand is... my audio output works perfect when e.g. playing a youtube video, sound comes out perfectly.
Until I want to use an audio/midi DAW/recorder, than it stops working as you suddenly need to run a jack server to get your connections right. And then that seems to produce problems.

Few years ago I tried to record guitar and came up with all same problems in Linux, finally I quit after spending weeks of tweaking, created a recording studio in Windows in a minute.

In Windows it all works perfect, even when running LMMS in Windows it works perfect, until I want to run it on a Linux system and then nothing seems to go in or out.
I'm sure Linux could be more easy and userfriendly somehow. 

Now my windows pc is occupied by my wife, I want to use the spare linux pc again to use as a music recording device.
Sorry for my rant ;)

---

### Post by CrocoDuck on 2016-11-03
> **bulevardi said:**
> What I don't understand is... my audio output works perfect when e.g. playing a youtube video, sound comes out perfectly.
Until I want to use an audio/midi DAW/recorder, than it stops working as you suddenly need to run a jack server to get your connections right. And then that seems to produce problems.


This is good, it means that your audio devices are working properly. Perhaps we are close to having it working correctly, there must be some configuration issue. The fact you need to kill dbus makes me think that pulseaudio cannot be integrated easily with jack when you launch it with those parameters. Let's make stuff clear: plug all your audio devices, open a terminal, paste these commands (one after the other) and copy back the output here:

```

aplay -l
arecord -l
amidi -l
cat .jackdrc

```

> **bulevardi said:**
> 
In Windows it all works perfect, even when running LMMS in Windows it  works perfect, until I want to run it on a Linux system and then nothing  seems to go in or out.
I'm sure Linux could be more easy and userfriendly somehow. 


Well, it is clear you cannot do that at the moment, but the golden rule is: if something work for you why to switch? If you like windows stick with it.

Anyway, to my reckoning you don't need to run jack to use LMMS, it should work directly with ALSA.

Linux audio is not straightforward: the device driver is ALSA and it is a kernel module. It is a big driver, making you system able to talk with many different devices. On top of that we typically use audio servers, like pulseaudio and jack, whose role is to stream data between audio applications and back to ALSA. If you have firewire devices it works the same, a part that instead of using the ALSA driver you deal typically with FFADO. ALSA is the most typical kernel module for audio under Linux but other exists, like OSS. As you can see, there are many more steps with respect a system like windows or mac os.

However, give love to Linux and Linux will love you back (eventually). Once you struggle at the beginning and take the time to learn you will see the results. In the past I believed audio on Linux was too hard to be practical. This was 10 years ago, when making it work was a real pain. Back in then I used windows for music. 7 years ago I finally took the time to learn how to do things properly. It paid so well that I never used windows again since. Actually, I struggle and get nuts on macs as well.. but let's keep it on topic.

---

### Post by bulevardi on 2016-11-03
aplay -l> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
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
card 3: DA40 [Plantronics DA40], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l
> **** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
 Subdevices: 1/1
 Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Alt Analog [ALC888 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: DA40 [Plantronics DA40], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


amidi -l
> Dir Device    Name
IO  hw:2,0,0  MPKmini2 MIDI 1





cat .jackdrc
> 
/usr/bin/jackd -nhw:2 -P25 -p128 -u -dalsa -dhw:DA40 -r44100 -p256 -n3 -S -P


I've put the system into English instead of Dutch, otherwise all the output was quite unreadable :)

> Well, it is clear you cannot do that at the moment, but the golden rule  is: if something work for you why to switch? If you like windows stick  with it.
Well yeah, the problem is my wife currently needs to use my windows pc a lot for school/job related stuff, and mostly on the moments I have my spare time too... grrr  for probably the next coming 2 years. Can't wait so long :)

And I like the open source idea, the nice community, etc... I already work with Gimp (linux photo editing) for a few years now instead of Photoshop and am very happy with it. Already shared some scripts I wrote for it.
For my photography hobby, I use a paid Raw Converter, but I want to get my whole workflow  with linux raw converters in the future too. So I can eventually do audio and imaging in the same 'creative ubuntu studio environment'.
As many people, I want to go the Linux way, however, the learning curve is a little higher than Windows, and maybe a little more time consuming, and time is a little scarce at the moment right now.

---

### Post by bulevardi on 2016-11-03
[IMG]http://users.telenet.be/bulevardi/tmp/screen3.png[/IMG]

I also don't really know which connections I have to make. 
In the MIDI and Audio tab, I don't have any options, only in the Alsa tab.
I sometimes see screenshots from Patchage with lots of wires... oh no...

---

### Post by bulevardi on 2016-11-03
Maybe it has something to do with PulseAudio interferring Alsa?  
Tried to kill pulseaudio already, and changing the config file to autospawn = no, but doesn't change anything.

---

### Post by CrocoDuck on 2016-11-03
Everything looks good to me. Open up LMMS. I think you have to enable the MIDI input for each instrument inside LMMS. Then they will show up in one of the tabs. If they show up in the MIDI tab you can use a2jmidid to bridge sockets in the ALSA tab to the MIDI tab. Connect the audio output of LMMS to system output (this would be your headphone). You are still using Duplex in the advanced tab. Apparently the plantronics has a duplex codec inside. If it works, no problems, but you might want to try Playback Only if you have any issue.

Pulseaudio has systemd socket activation now, so it is harder to kill, but if you are able to launch jack you should be alright.

---

### Post by CrocoDuck on 2016-11-03
Also, make sure LMMS is configured to use Jack. By default I think it will try to talk with ALSA, but when jack is running the applications streaming directly to ALSA have their queue blocked.

---

### Post by bulevardi on 2016-11-04
Hmm right now, LMMS plays and records like it should... even without Jack indeed.
Don't know what I've done wrong before, or what I've been changing... 

Now Rosegarden, seems to record, but no audio output. Grrr :)

---

### Post by CrocoDuck on 2016-11-04
I never used Rosegaren, not sure what to suggest here.

Anyway, believe it or not, I think your system is actually working correctly. You just need to understand how to make all the pieces to work together.

When you boot up pulseaudio is running and managing audio applications streams to ALSA.

There are many applications that can work or through pulseaudio or directly with ALSA. If you choose to do so you will probably have to mess with settings in each program and systemwise. pavucontrol can enable some more control over pulseaudio with respect the XFCE audio devices utility. Also, running alsamixer from console is a quick way to check whether you have muted channels and unmute them easily.

Many applications require jack to run (or they just work best with jack). In this case you need to launch jack. Once jack is up you need to make sure the applications are connected to the various places you want. Use the connections window in qjackctl for that. It might happen that pulseaudio gives problems. Here you can find some [up to date links]("https://linuxmusicians.com/viewtopic.php?f=27&t=15731") on how to kill it.

Perhaps, it is best to test simple software first. Your ubuntu should come with ZynAddSubFx or Yoshimi. Once you get jack running, try to open Zyn or Yoshimi. Check the connections window in qjackctl and connect the audio outputs of the synth to the audio outputs of the card (your headphone). Then, connect your midi controller to the synth. If the synth midi input does not show in the ALSA tab but in the MIDI instead, open the terminal and digit a2jmidid. Then, connect the midi controller to MIDI through and in the MIDI tab connect a2jmidid to the synth.

This is a sort of very brief guide to help you out. I strongly suggest to look at the tutorials on [Libre Music Productions]("http://libremusicproduction.com/tutorials") ([this]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack") especially). I feel you are pretty much almost there: you just need to learn how to use the software.

---

### Post by bulevardi on 2016-11-04
Hmm, interesting stuff.
Been busy already the whole evening testing stuff.

LMMS is working fine already. But need to work with the software, always new stuff to learn, want to be too quick with everything.
The problem is indeed getting the connections right in Qjackctl. Mostly in the Audio tab, I don't see anything to get output. 
Will try further later on, need to get some sleep right now.
Will catch up with you when I still have further questions. Just installed Yoshimi and Zyn (were not standard installed apparently) and will see if I can get the connections :)

Thanks for the efforts already !

---

