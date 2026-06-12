---
title: "xruns with jackd and headset issue"
date: 2010-12-04
forum: Ubuntu Studio
---

### Post by c0rrupt0r on 2010-12-04
First off I had followed the steps from this thread [http://ubuntuforums.org/showthread.php?p=10191453#post10191453](http://ubuntuforums.org/showthread.php?p=10191453#post10191453) such as to running these tests and commands in terminal

    * cat /proc/interrupts
    * lspci | grep1394
    * [realTimeConfigQuickScan]("http://code.google.com/p/realtimeconfigquickscan/") (if possible, you need the packages mercurial and perl-tk for this)


I am using ALSA with Jackd and IDJC on Ubuntu Studio 10.10

I get xruns every 5 minutes but also it disconnects about every 30 Minutes, here is my info I have gathered.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177216&stc=1&d=1291324730[/IMG]

I have also fixed all issues that QuickScan has given me info on. thank you for that script for sure was great info.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177215&stc=1&d=1291324261[/IMG]

After all this testing and so on I have also come to find out. when I change my Sound card settings in qjackctl to "Default" (which is my Intel onboard soundcard), instead of using my Plantronics usb wireless 995H headset It all works with no xruns and no disconnections that im aware of. Please help here, I do not wish to use my default onboard sound card, I enjoy using my headset. Thank you in advanced.

---

### Post by c0rrupt0r on 2010-12-05
Bump. 

No one can help me ? 
Please I need help with this it has been doing this to me under several different versions of Ubuntu and also different versions of Jackd 
any Help would be appreciated
Thank you

---

### Post by Pablo_F on 2010-12-05
Hi, 

I don't know how many people in the world are using the Plantronics usb wireless 995H headset in Linux with alsa and jack, but I guess not too many... me neither. I wish I could test.

What jack version are you running?

("jackd -V" in a terminal)

Can you give the output of "arecord -l", "aplay -l", "lsusb" and "cat /proc/asound/modules" ?

Cheers, Pablo

---

### Post by c0rrupt0r on 2010-12-05
Hello Pablo thank you for your response

> **Pablo_F said:**
> Hi, 

I don't know how many people in the world are using the Plantronics usb wireless 995H headset in Linux with alsa and jack, but I guess not too many... me neither. I wish I could test.

What jack version are you running?

("jackd -V" in a terminal)

Can you give the output of "arecord -l", "aplay -l", "lsusb" and "cat /proc/asound/modules" ?

Cheers, Pablo

here is my results 

> jackd -V 
jackdmp version 1.9.6 tmpdir /dev/shm protocol 8


> arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Plantronics Wireless Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audio [Plantronics Wireless Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


> lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 047f:d955 Plantronics, Inc. 
Bus 001 Device 010: ID 0425:f102 Motorola Semiconductors HK, Ltd G-Tech U+P Wireless Mouse
Bus 001 Device 009: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 008: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 007: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


> cat /proc/asound/modules
 0 snd_intel8x0
 1 snd_usb_audio


Thank you

---

### Post by trulan on 2010-12-05
Try plugging your headset into another USB port and see if you can get it onto bus 2 or 3.  Having the headset on bus 1 with your mouse could be a potential problem.  You don't need USB 2.0 for a basic USB sound interface, USB 1.1 should be fine.  (Maybe that's not possible, it depends on the configuration of your ports.)

Another idea would be to try different buffering settings in Jack control - 3 periods instead of 2, more frames/period, or fewer.  What are your current Jack settings for the headset?

---

### Post by c0rrupt0r on 2010-12-06
Hello trulan

I have plugged in my Wireless headset doggle to another usb port and it attached to bus 3 from what I am seeing in terminal.



> lsusb
Bus 003 Device 009: ID 047f:d955 Plantronics, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 025: ID 1221:3234  
Bus 001 Device 005: ID 0425:f102 Motorola Semiconductors HK, Ltd G-Tech U+P Wireless Mouse
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I also changed some of my settings in qjackctl here is my settings at this moment.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177586&stc=1&d=1291624467[/IMG]

I have also noticed on Jackd it is stuck at sample rate 16000Hz even when changing it in qjackctl to 44100hz or what ever my desired sample rate is. it will not change no matter what I do if im using the Plantronic headset configured in qjackctl.

Here is a Screen shot to show it stuck at 16000 Hz on Jackd

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177588&stc=1&d=1291625254[/IMG]

Here is a Screen shot configurations in IDJC as it shows Jackd forcing it at 16000 Hz

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=177587&stc=1&d=1291625254[/IMG]

This is just info I have noticed that I am not sure could be the problem so figured I would post it

Thank you for your help

---

### Post by c0rrupt0r on 2010-12-06
No one can help me? please

---

### Post by cchhrriiss121212 on 2010-12-06
You could try checking soft mode and force 16bit, or installing a low latency kernel, just a shot in the dark though. Could you see if you are you getting Xruns without running IDJC?

---

### Post by c0rrupt0r on 2010-12-06
soft mode isn't always recommended from what I been told? But I will test it
all the newer kernals are already using RT I thought? But I will check this out
RT is enabled in Jackd and Jackd seems to be working with it just fine. 
With IDJC turned off and shut down I still am gathering xruns.

Thank you for your reply cchhrriiss

---

### Post by Pablo_F on 2010-12-06
Hi, 

What's the terminal output of "amixer -c1"?

Could it be that your headset does not support sample rate higher than 16 kHz ?

Some hints: I think the first two are rather useless though, but keep it as simple as possible:

Instead of using hw:1 for capture and playback, leave them default and use the interface hw:1. 

If jack insists on running at 16.000 Hz and you can't do anything about it, set to 16.000 Hz.

Try increasing frames per period.

Cheers, Pablo

---

### Post by c0rrupt0r on 2010-12-06
Hello Pablo Thank you for your Reply

> amixer -c1 output
Simple mixer control 'PCM',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 34
  Mono: Playback 17 [50%] [-29.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 28
  Mono: Capture 15 [54%] [-13.00dB] [on]


> Could it be that your headset does not support sample rate higher than 16 kHz ?

I did some searching on my headset and it claims it supports much higher. but I have now set the sample rate to 16000 and going to test it this way.

> Instead of using hw:1 for capture and playback, leave them default and use the interface hw:1.

Ok I set capture and playback to default and then changed interface to hw:1

> Try increasing frames per period.

I now set the frames per period higher to 4096

before all these changes I was gathering xruns and then it would give me a time out with no message. but this time it gave me a message in jackd when disconnecting and then 3 minutes after the disconnect is when I have gotten an xrun

> JackClientSocket::Read time out
17:26:56.774 JACK connection graph change.
17:26:57.064 JACK connection change.
17:26:57.067 JACK connection graph change.
alsa_driver_xrun_recovery
JackPosixMutex::Unlock res = 1
JackAudioDriver::ProcessAsync: read error, skip cycle
17:33:44.525 XRUN callback (1).


I have also noticed this message sent in jackd while loading IDJC 

> Unknown destination port in attempted (dis)connection src_name [idjc-mx:dsp_out_l] dst_name [jamin:in_L]
Unknown destination port in attempted (dis)connection src_name [idjc-mx:dsp_out_r] dst_name [jamin:in_R]
Unknown source port in attempted (dis)connection src_name [jamin:out_L] dst_name [idjc-mx:dsp_in_l]
Unknown source port in attempted (dis)connection src_name [jamin:out_R] dst_name [idjc-mx:dsp_in_r]

Then while closing IDJC I get this message from Jackd

> JackClientSocket::Read time out

---

### Post by c0rrupt0r on 2010-12-07
Friendly Bump

---

### Post by Pablo_F on 2010-12-07
Hi, 

As for the sample rate, I am sorry I cannot help. It seems like a driver issue. I suggest you ask in alsa users mailing list. 

I am not very familiar with jack2, (jackd versions 1.9.x) but I would try, in this order:

- Increase the time limit to 5000
- Run jackd in synchronous mode. For this, you have to append "-S" to the jackd command. This is, "/usr/bin/jackd -S" in the "server path" field.
- Switch to jackd1. For this you have to install jackd1 package from synaptic or "sudo apt-get install jackd1". This will uninstall jackd2 but it could uninstall some apps you need. Don't panic, write them down and install them later.

You can always check the jackd version with "jackd -V". jackd 0.xxx.x is jackd1. Don't forget to delete "-S" in the server path when running jack1. 

- Try Soft mode. 

By the way, are you running jamin? Do you need jamin? jamin is a tool for mastering and is very CPU hungry. 

Cheers, Pablo

---

### Post by c0rrupt0r on 2010-12-07
I have been messing with this for months now non stop and it always ends up the same way no matter what it seems. I have tried through sources and jack1 and jack2 and always the same outcome of disconnecting. even with different versions of Ubuntu. 

Is there any other software other then jackd?

---

### Post by c0rrupt0r on 2010-12-07
bump

---

### Post by oneindelijk on 2010-12-11
Hi, 

I've been running into the xruns problems as well rendering jackd useless, but I found a simple, but probably not recommended solution ;-)

I'm running Ubuntu 10.10 with a 11.04 (natty) realtime kernel
I've tried many things to fix jackd even running jackd as root, but eventually found out that ardour can't connect to jackd even iwhen they're both started as root.
So I switched to a console and issue the follow commands```
sudo -i
service gdm stop
startx
```
-become root
-stop displaymanager (causes all X services to be terminated)
-start X11 under root priviliges (cause logging in directly as root is mostly disabled)

Then when I let Ardour start jackd (instead of through the commandline or qjackctl) it runs as it should...

The only difference there is that has a realtime priority of 60, while with jackd it was -P 70

Hopefully this helps someone who desperately needs jack and finds no solution :D

---

### Post by AutoStatic on 2010-12-11
> **oneindelijk said:**
> I've been running into the xruns problems as well rendering jackd useless, but I found a simple, but probably not recommended solution ;-)It is highly discouraged to run a root desktop session. It doesn't help anyone so please, don't post 'solutions' like this. If you desperately need JACK and it doesn't run then ask. In your case for example a normal user isn't allowed to run JACK in realtime mode which can be easily fixed.

Best,

Jeremy

---

### Post by oneindelijk on 2010-12-11
> It is highly discouraged to run a root desktop session. It doesn't help anyone so please, don't post 'solutions' like this. If you desperately need JACK and it doesn't run then ask. In your case for example a normal user isn't allowed to run JACK in realtime mode which can be easily fixed.


I'm sorry you're right, let say it is a way to check out if your hardware can handle it.
Strange enough, this none-solution doesn't work for pure:dyne (which is a distro based on Ubuntu Karmic that comes with an realtime kernel as default).

I don't like running my box as root either, I understand (some of) the security risks involved, but then again, security is an illusion, is it not ? (a little of topic, I know) :D

---

