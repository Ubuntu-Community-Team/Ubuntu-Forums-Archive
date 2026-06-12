---
title: "Lexicon Omega doesn't work in ubuntu studio 10.10"
date: 2011-05-18
forum: Ubuntu Studio
---

### Post by BcRich on 2011-05-18
Hi
I have a Lexicon Omega external sound interface which has worked fine in ubuntu 9.04 and 10.04 (both 32bit). I recently installed ubuntu studio 10.10 64 bit and my sound is no longer working. the device does however show up in /proc/asound/cards
```
 0 [Omega          ]: USB-Audio - Lexicon Omega
                      Lexicon Lexicon Omega at usb-0000:02:00.0-4, full speed
 1 [U0x46d0x8b2    ]: USB-Audio - USB Device 0x46d:0x8b2
                      USB Device 0x46d:0x8b2 at usb-0000:00:16.0-1, full speed
 2 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe024000 irq 16
 3 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfdefc000 irq 45
```
it is also available for selection in JACK under interfaces, but when i choose it and restart JACK I get the following message
```
 p, li { white-space: pre-wrap; } [COLOR=#999999]21:48:03.262 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:48:03.310 Statistics reset.[/COLOR]
 [COLOR=#999999]21:48:03.354 Startup script...[/COLOR]
 [COLOR=#990099]21:48:03.355 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66CC99]21:48:03.364 ALSA connection graph change.[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]21:48:03.760 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]21:48:03.761 JACK is starting...[/COLOR]
 [COLOR=#990099]21:48:03.761 /usr/bin/jackd -t1000 -dalsa -dhw:0 -r44100 -p128 -n3[/COLOR]
 [COLOR=#999999]21:48:03.780 JACK was started with PID=10664.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.6
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2010 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|32bit
 Using ALSA driver USB-Audio running on card 0 - Lexicon Lexicon Omega at usb-0000:02:00.0-4, full speed
 configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 3 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: use 3 periods for capture
 ALSA: cannot set hardware parameters for capture
 ALSA: cannot configure capture channel
 Cannot initialize driver
 JackServer::Open() failed with -1
 Failed to start server
 [COLOR=#999999]21:48:03.923 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]21:48:03.924 Post-shutdown script...[/COLOR]
 [COLOR=#990099]21:48:03.924 killall jackd[/COLOR]
 [COLOR=#CCCC99]21:48:03.962 ALSA connection change.[/COLOR]
 jackd: no process found
 [COLOR=#999999]21:48:04.333 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]21:48:05.965 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#FF0000]21:48:10.447 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot connect to server socket err = No such file or directory[/COLOR]
 [COLOR=#999999]Cannot connect to server socket[/COLOR]
 [COLOR=#999999]jack server is not running or cannot be started[/COLOR]
 
```
/proc/asound/pcm looks like this
```
00-00: USB Audio : USB Audio : playback 1 : capture 1
00-01: USB Audio : USB Audio #1 : playback 1 : capture 1
01-00: USB Audio : USB Audio : capture 1
02-00: ALC889 Analog : ALC889 Analog : playback 1 : capture 1
02-01: ALC889 Digital : ALC889 Digital : playback 1 : capture 1
02-02: ALC889 Analog : ALC889 Analog : capture 2
03-03: ATI HDMI : ATI HDMI : playback 1
```
and lsusb looks like this 
```
Bus 008 Device 003: ID 1210:0002 DigiTech 
Bus 008 Device 002: ID 1e3d:2095  
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 005: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 007 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 003: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 007 Device 002: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 12d1:1464 Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
i would really appreciate it if someone could point me in the right direction.
thank you :)

---

### Post by sgx on 2011-05-19
Try starting up with:

jackd -d alsa -r 44100

If that does not work, try

sudo jackd -d alsa -r 44100

Then start a gui like qjackctl or patchage afterwards, if there is no error.

These will eliminate some basic config and permissions issues
by means of simplicity. 

[http://www.linuxdsp.co.uk/download/jack/index.html](http://www.linuxdsp.co.uk/download/jack/index.html)

jp1 is another jackd patchbay you can download at the above url,
to see if it works with the lexicon. Just start it by name in a terminal,
with full path, like

/home/user/jp1_i586

Check Lexicon manual for default settings that may need to be matched in
your jackd command, or jumpers/switches/buttons that control settings.

Using 10.04 may be best, if newer ones are buggy.

Akso, if there are any other usb devices, I would unplug them, and test the Lexicon in each connection

Cheers

---

### Post by BcRich on 2011-05-19
hi sgx
thanks for the suggestions :)
the problem seems to be partly fixed as I now have audio again yay! it was actually something to do with my onboard soundcard not being disabled in bios. unfortunately JACK is still causing a bit a a problem to get started, but i'lll give what you suggested another try and see how things go.
thanks again :)

---

### Post by Pablo_F on 2011-05-19
Hi,

Beginning with ubuntu 10.10, the jack server is jack2 and that can make a difference with respect to previous US versions which featured the original jack or jack1.

Sometimes jack2 does not behave very well in the default asynchronous mode.  I suggest you should try the asynchoronous mode by appending *-S* to the jackd command, in the server path field of qjackctl setup window. 

Alternatively, the original jack is available in the repos and you can test it very easily: "sudo apt-get install jackd1" will uninstall jackd2 and install jackd1.  

Cheers, Pablo

---

### Post by BcRich on 2011-05-19
hi Pablo_F
you're right about jack2 being installed on my system. I didn't even know that there was a jack2 let alone the fact that it was installed on my system. So thanks for the heads up :)
strangely enough JACK(2) seems to be working again (without the -S modification as suggested). I don't know what exactly I did to make it work (if it was anything that I did) but it seems to be working fine. The only thing I have done since I last tried to get JACK to work was install ubuntu-restricted-extras but I have no idea if this is related to getting JACK to working again or not. Nonetheless I'm glad that it working and thanks again for the help :)

---

