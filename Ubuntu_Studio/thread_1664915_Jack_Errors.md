---
title: "Jack Errors"
date: 2011-01-11
forum: Ubuntu Studio
---

### Post by james_r_lucas on 2011-01-11
Hello Guys

I'm having issues with the Jack Server not starting in Ubuntu Studio 10.10

It keeps coming up with the following log. on rare occasions, it works fine, but those occurances are few and far between. 

```
21:02:47.906 Patchbay deactivated.
21:02:47.956 Statistics reset.
21:02:47.977 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
21:02:48.112 Startup script...
21:02:48.113 artsshell -q terminate
21:02:48.118 ALSA connection graph change.
sh: artsshell: not found
21:02:48.566 Startup script terminated with exit status=32512.
21:02:48.719 D-BUS: JACK server could not be started. Sorry
21:02:48.941 ALSA connection change.
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: driver "alsa" selected
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Saving settings to "/home/james/.config/jack/conf.xml" ...
Tue Jan 11 21:02:48 2011: Starting jack server...
Tue Jan 11 21:02:48 2011: JACK server starting in realtime mode with priority 5
Tue Jan 11 21:02:48 2011: [1m[31mERROR: can't load "/usr/lib/jack/jack_alsa.so": /usr/lib/jack/jack_alsa.so: undefined symbol: _jack_get_microseconds[0m
Tue Jan 11 21:02:48 2011: [1m[31mERROR: Cannot initialize driver[0m
Tue Jan 11 21:02:48 2011: [1m[31mERROR: JackServer::Open() failed with -1[0m
Tue Jan 11 21:02:48 2011: [1m[31mERROR: Failed to start server[0m
21:02:51.291 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
21:02:55.725 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
21:03:04.553 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
21:03:22.205 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
21:03:57.568 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
21:05:08.061 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
21:07:29.234 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

I have no clue as to why it is doing this, when It used to work fine 

I'm using the lowlatency kernel, but it used to do this before I installed it, and I ahd the same errors. I don't currently have a firewire interface, I'm just using jack to connect my MIDI keyboard to ZynAddSubFX, then connecting the output of that to the sound card on the laptop (for some reason, my external USB soundblaster has never been recognised by Jack, but I aint too bothered)

Thanks

---

### Post by argoson on 2011-01-11
within the error output, there is a line saying something about JACK and ALSA...

open Synaptic (the software installation manager) and search for "ALSA" (without the quotes). see if you can find something that say alsa-jack library (or something similar). Install it and any dependencies it's saying it will install.

Restart JACK and see if it solves the problem.

Also, start without the realtime option and see what happenes

---

### Post by AutoStatic on 2011-01-12
```
apt-file search jack_alsa.so
libjack0: /usr/lib/jack/jack_alsa.so
```So jack_alsa.so is part of the package libjack0. You could try reinstalling that package.

---

### Post by james_r_lucas on 2011-01-12
I have tried reinstalling it several times, but I'll check that it was actually that package that I was reinstalling
 
And how do I start without realtime? - I'm just clicking the button on the main menu lol

---

### Post by yoni1 on 2011-01-12
[see below]

---

### Post by yoni1 on 2011-01-12
[see below]

---

### Post by yoni1 on 2011-01-12
It doesn't look related to realtime or not, but rather to two different components not being compatible with each other.  I would search around for "jack_alsa.so: undefined symbol: _jack_get_microsecond"

This post might help you:
[http://ubuntuforums.org/showthread.php?t=503298](http://ubuntuforums.org/showthread.php?t=503298)

But so you know, to start without realtime, click on "setup" in qjackctl and remove the check mark from Realtime

---

### Post by james_r_lucas on 2011-01-12
Right, I've tried everything suggested to no avail

I removed all the of the jack related packages / libraries etc using Synaptic, rebooted, reinstalled everything and rebooted, but still nothing. Although the error log has changed, so I've included a copy

```
[COLOR="Silver"]17:37:07.639 Patchbay deactivated.
17:37:07.678 Statistics reset.
17:37:07.734 D-BUS: Service not available (org.jackaudio.service aka jackdbus).
17:37:07.768 Startup script...[/COLOR]
[COLOR="DarkOrchid"]17:37:07.768 artsshell -q terminate[/COLOR]
[COLOR="PaleTurquoise"]17:37:07.772 ALSA connection graph change.[/COLOR]
sh: artsshell: not found
[COLOR="Silver"]17:37:08.256 Startup script terminated with exit status=32512.
17:37:08.256 JACK is starting...[/COLOR]
[COLOR="DarkOrchid"]17:37:08.256 /usr/bin/jackd -P5 -dalsa -dhw:0 -r44100 -p1024 -n3 -Xraw[/COLOR]
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
[COLOR="Silver"]17:37:08.262 JACK was started with PID=2564.[/COLOR]
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1536657
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
[COLOR="#c0c0c0"]17:37:08.270 JACK was stopped with exit status=255.
17:37:08.270 Post-shutdown script...[/COLOR]
[COLOR="DarkOrchid"]17:37:08.271 killall jackd[/COLOR]
[COLOR="Silver"]17:37:08.459 ALSA connection change.[/COLOR]
jackd: no process found
[COLOR="#c0c0c0"]17:37:08.679 Post-shutdown script terminated with exit status=256.[/COLOR]
1[COLOR="Red"]7:37:10.470 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
17:37:14.920 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
17:37:23.778 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
17:37:41.425 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
17:38:16.684 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
```

This line seems to be saying something is wrong but I've no idead what it means (wtf are xruns :confused:). I've tried finding the file it mentions, but it isn't there. The only file by that name that appears in search is a security one


```
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
```

---

### Post by Pablo_F on 2011-01-12
Hi, 

Raise the priority. 60 or 70 is OK. I think 5 is too low.

Anyway, what are the terminal outputs of 

```
cat /etc/security/limits.conf /etc/security/limits.d/audio.conf |grep -v "#"

ulimit -r -l

groups
```

?

---

### Post by james_r_lucas on 2011-01-13
I thought the Priority (nice value) was between -20 for highest and 20 for lowest? - or are they actually different things?

Anyway, here are the results 

```
@audio - rtprio 100
@audio - nice -20
@audio - memlock 1536657


@audio   -  rtprio     95
@audio   -  memlock    unlimited

```

```
real-time priority              (-r) 99
max locked memory       (kbytes, -l) unlimited
```

```
james adm dialout fax cdrom floppy tape audio dip video plugdev fuse netdev lpadmin admin sambashare

```

I literally just tried again, and it suddenly worked :confused: I'll have a play around and see if it stops again. Only difference this time is that the USB soundcard is unplugged - maybe it doesn't like it. I'll be back :)

---

### Post by Pablo_F on 2011-01-13
Hi, You have redundant limits.conf files.

Keep the configuration in one place only.

The jack priority has nothing to do with nice. You don't even need a nice line in limits.conf. See jackaudio FAQ. 

Hint: Use card names, not numbers. See *cat /proc/asound/cards* and you will see the card names in square brackets, then write down hw:name in the interface field instead of choosing a card number from the drop down menu. presets come handy

Cheers, Pablo

---

### Post by james_r_lucas on 2011-01-14
See below

---

### Post by james_r_lucas on 2011-01-14
It was working last night, but now it isn't again. I've deleted the duplicate audio conf files, so the only one there is now in /etc/security/limits.conf

Here is my current error log

```
19:46:05.855 Patchbay deactivated.
19:46:05.942 Statistics reset.
19:46:05.967 D-BUS: Service not available (org.jackaudio.service aka jackdbus).
19:46:06.038 Startup script...
19:46:06.039 artsshell -q terminate
19:46:06.045 ALSA connection graph change.
sh: artsshell: not found
19:46:06.492 Startup script terminated with exit status=32512.
19:46:06.492 JACK is starting...
19:46:06.493 /usr/bin/jackd -P5 -dfirewire -r44100 -p1024 -n3
19:46:06.498 JACK was started with PID=2879.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    1536657
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
19:46:06.510 JACK was stopped with exit status=255.
19:46:06.511 Post-shutdown script...
19:46:06.511 killall jackd
19:46:06.695 ALSA connection change.
jackd: no process found
19:46:06.919 Post-shutdown script terminated with exit status=256.
19:46:08.715 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
19:46:13.234 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
19:46:22.079 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
19:46:39.872 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
19:47:15.258 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

It looks to me as if the jackd server is starting, then getting shut down straight after :confused:

---

### Post by Pablo_F on 2011-01-14
I thought you didn't have a firewire interface. In that case, you want the alsa driver. 

Please look at the output of "cat /proc/asound/cards" (paste here for better help) and tell jack the interface to use. This is a key decision before starting the server.

Make one change at a time. Default settings are rather sane. 

Cheers, Pablo

---

### Post by james_r_lucas on 2011-01-16
No, I don't have a firewire interface. And I've just found the option th cahnge it to alsa, with no change to the output (except the -dfirewire is now changed to -dalsa)

Here is the output of cat /proc/asound/cards

```
james@James-PC:~$ cat /proc/asound/cards
 0 [Cable          ]: USB-Audio - USB Midi Cable
                      USB Midi Cable at usb-0000:00:1d.7-1.1.4, full speed
 1 [NX             ]: USB-Audio - SB Audigy 2 NX
                      Creative Technology Ltd SB Audigy 2 NX at usb-0000:00:1d.0-2, full speed
 2 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe300000 irq 48
29 [ThinkPadEC     ]: ThinkPad EC - ThinkPad Console Audio Control
                      ThinkPad Console Audio Control at EC reg 0x30, fw 7KHT24WW-1.08

```

I would prefer to use the Audigy sound card, but is it possible to use that and the Intel card to give four ins & four outs?

Thanks for your help so far ;)

EDIT:

I've been playing around with the options - and using the alsa driver option (which seems to show some life at some point

with realtime checked, it gets nowhere, as shown below 

```
13:04:40.204 Patchbay deactivated.
13:04:40.304 Statistics reset.
13:04:40.324 D-BUS: Service not available (org.jackaudio.service aka jackdbus).
13:04:40.413 Startup script...
13:04:40.414 artsshell -q terminate
13:04:40.424 ALSA connection graph change.
sh: artsshell: not found
13:04:40.824 Startup script terminated with exit status=32512.
13:04:40.824 JACK is starting...
13:04:40.825 /usr/bin/jackd -P5 -dalsa -dhw:0 -r48000 -p1024 -n3 -Xraw
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
13:04:40.831 JACK was started with PID=3561.
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
13:04:40.838 JACK was stopped with exit status=255.
13:04:40.839 Post-shutdown script...
13:04:40.839 killall jackd
13:04:41.027 ALSA connection change.
jackd: no process found
13:04:41.251 Post-shutdown script terminated with exit status=256.
```

But with realtime unchecked, I get this

```
13:36:43.730 Patchbay deactivated.
13:36:43.827 Statistics reset.
13:36:43.848 D-BUS: Service not available (org.jackaudio.service aka jackdbus).
13:36:43.976 Startup script...
13:36:43.976 artsshell -q terminate
13:36:43.980 ALSA connection graph change.
sh: artsshell: not found
13:36:44.380 Startup script terminated with exit status=32512.
13:36:44.380 JACK is starting...
13:36:44.381 /usr/bin/jackd -r -dalsa -dhw:0 -r48000 -p1024 -n3 -Xraw
13:36:44.390 JACK was started with PID=3639.
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:0|hw:0|1024|3|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
cannot load driver module alsa
13:36:44.412 JACK was stopped successfully.
13:36:44.412 Post-shutdown script...
13:36:44.413 killall jackd
13:36:44.583 ALSA connection change.
jackd: no process found
13:36:44.822 Post-shutdown script terminated with exit status=256.
```

---

### Post by Pablo_F on 2011-01-16
```
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
```

Strange. Can you give the output of *ulimit -r* again when you are logged in with the same user that tries to start the jack server?

The interface can be hw:NX  (Probably you have several "devices". Check *aplay -l*)

Use alsa_in / alsa_out to use an alternate audio interface with jack. For example, if you started jack with hw:NX try something like:

alsa_out -d hw:Intel

However, don't expect that this is the same as having one soundcard with regards to quality and synchronization.

Cheers, Pablo

---

### Post by james_r_lucas on 2011-01-16
Hello

*ulimit -r* comes up with the result 100

Also, in my previous post, I've added a couple more error reports with and without realtime

*aplay -l* gives this

```
**** List of PLAYBACK Hardware Devices ****
card 1: NX [SB Audigy 2 NX], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Following on from that, I've now been playing with the device options on the setup page. selecting hw:1 (which is the USB audigy card), it comes up with the following line in the error report ```
the playback device "hw:1" is already in use. Please stop the application using it and run JACK again
``` Which is probably cos I've been using it to listen to music with :D

selecting hw:2 (intel audio) it works fine :)

Thanks for your help. Basically i've been messing around in the setup page without knowing what I was doing ] (*,)

---

### Post by james_r_lucas on 2011-01-16
I've now installed the realtime kernel, and it works even better. 40ms latency, which is good enough. Beats the 600ms I had under windows, which is why I switched to Ubuntu in the first place.

I've swaped my sound card mapping around, so that Jack can use the Audigy 2 card, however when I start Jack, I now get these lines in the error log

```
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|512|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 2 periods for playback
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
```

Do you know if the Audigy 2 NX is even supported in Jack? - if not, it's time I actually bought the firewire card I've wanted for ages lol

---

### Post by Pablo_F on 2011-01-16
Afaik, jack does not support any soundcards. It talks to the alsa driver, not directly to the soundcards.

What probably happens here is that there is a USB hub controller that is spoiling things. Take a look at *lsusb* and *lspci | grep USB*

See if you can start jackd with the NX in playback only mode. 

By the way, you can name the cards *hw:NX* or *hw:Intel* instead of *hw: x* where x is a number. You will avoid card confusion completely. You can write it down in the interface field of qjackctl. Yes, even if it is not an option in the drop down menu.

Cheers, Pablo

---

### Post by james_r_lucas on 2011-01-23
*lsusb* gives

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 041e:3020 Creative Technology, Ltd SoundBlaster Audigy 2 NX
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 054c:00d5 Sony Corp. 
Bus 002 Device 008: ID 03ee:6437 Mitsumi 
Bus 002 Device 007: ID 15ca:0101 Textech International Ltd. 
Bus 002 Device 006: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 005: ID 057b:0000 Y-E Data, Inc. FlashBuster-U Floppy
Bus 002 Device 004: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 17ef:1004 Lenovo 
Bus 002 Device 002: ID 1a40:0201 TERMINUS TECHNOLOGY INC. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

*lspci | grep USB* gives

```
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)

```

It works fine in playback only mode

also, when I start jack (normally the third or fourth time) it causes something to mess up, so all my window borders disappear, as shown here
[[IMG]http://i1006.photobucket.com/albums/af190/james_r_lucas/th_Screenshot.png[/IMG]](http://s1006.photobucket.com/albums/af190/james_r_lucas/?action=view&current=Screenshot.png)
Any clues as to why this is?

Thanks for your help so far, It's much appreciated ;)

---

### Post by csumm101 on 2012-07-03
Hey. I thought I would just chime in here.

I had the "D-Bus: Jack server could not be started. Sorry" after installing lowlatency and realtime kernels. I spent a considerable amount of time trying to scour the internet for solutions. I tried many things to no avail...

Finally, I found the solution! And I hope it helps others who may be in the same boat.

Well... you see, it all started back with Ardour. Ardour gave me the typical memory lock warning many moons ago and I "fixed the problem by going into /etc/security/limits.conf" and "tweaking" it. All was just peachy until I tried running a low latency or real time kernel. It didn't like my settings.

Actually, I set my audio memlock to "unlimited".
This was my old setting:

*		- memlock	unlimited

Ardour seemed to like this setting so I thought all was good until a lowlatency/realtime kernels were run. This is the setting that caused the problem and Jack wouldn't start!

I removed the above line and added the following:

@audio rtprio 99
@audio nice -15
@audio memlock 250000 

rebooted, and Jack ran! And Ardour likes it too!

Hope that helps my fellow Ubuntu'ers

---

### Post by sgx on 2012-07-04
Good find. Now that many users have large ram collections,
the old traditional wisdom, can be extended!

I'm always shocked how little memory is actually used
in fairly complex linux recording sessions

:popcorn:

---

