---
title: "Yet Another Can Not Connect To Jack Thread"
date: 2011-10-19
forum: Ubuntu Studio
---

### Post by Precipitous on 2011-10-19
I am running UbuntuStudio 10.10 and no longer able to connect to Jack. When I try to the message window displays the following:
```
p, li { white-space: pre-wrap; }  17:20:19.769 Patchbay deactivated.
 17:20:19.797 Statistics reset.
 17:20:19.802 ALSA connection change.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 17:20:24.239 Startup script...
 17:20:24.240 artsshell -q terminate
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 17:20:24.642 Startup script terminated with exit status=32512.
 17:20:24.642 JACK is starting...
 17:20:24.643 /usr/bin/jackd -p128 -t1000 -dalsa -dhw:0 -r44100 -p256 -n2
 17:20:24.646 JACK was started with PID=7746.
 no message buffer overruns
 no message buffer overruns
 17:20:24.690 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2011 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:0
 control device hw:0
 audio_reservation_init
 Acquire audio card Audio0
 creating alsa driver ... hw:0|hw:0|256|2|44100|0|0|nomon|swmeter|-|32bit
 control device hw:0
 configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 32bit integer little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 32bit integer little-endian
 ALSA: use 2 periods for playback


```I am a member of the Audio group.


The output of aplay -l is:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```The output of lspci is:
```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
```Anyone have any suggestions?

---

### Post by sgx on 2011-10-20
The last four lines indicate jackd is running, does it show as
active in qjackctl?

Is the mixer muted?

Is skype or a web browser using the audio?

Are the speakers/headphones in the right connector?

:popcorn:

---

### Post by Precipitous on 2011-10-20
> **sgx said:**
> The last four lines indicate jackd is running, does it show as
active in qjackctl?

Is the mixer muted?

Is skype or a web browser using the audio?

Are the speakers/headphones in the right connector?

:popcorn:
Jackctl does not show active, mixer is not muted, nothing else is using audio, speakers/headphones are connected properly...

---

### Post by sgx on 2011-10-20
> **Precipitous said:**
> Jackctl does not show active, mixer is not muted, nothing else is using audio, speakers/headphones are connected properly...try this command, but look in the
qjackctl setup page by

Input Device >
Output Device >  and click the  > widgets to choose
your detected Chw: and Phw:

jackd -dalsa -r44100 -p512 -n2 -D -Chw:0,0 -Phw:0,0

were there any recent software or hardware changes?
What were you using when it was working OK?

Cheers

---

### Post by Precipitous on 2011-10-20
> **sgx said:**
> try this command, but look in the
qjackctl setup page by

Input Device >
Output Device >  and click the  > widgets to choose
your detected Chw: and Phw:

jackd -dalsa -r44100 -p512 -n2 -D -Chw:0,0 -Phw:0,0

were there any recent software or hardware changes?
What were you using when it was working OK?

Cheers
Thank you for taking the time to help me!

I was able to connect to Jack Server running your suggested command in a terminal. Because of this I tried entering it in the "Execute This Script On Startup" section of the Jack Audio Connection Kit setup options. This seems to work fine. 

I am curious as to whether it is "proper" to do this, and if it is, why I am suddenly having to do so since I have not had any recent sw or hw changes...

Any further help would be greatly appreciated.

---

### Post by sgx on 2011-10-21
Hi, the textfile .jackdrc is saved in your user folder by
qjackctl. It can be used as a command to start jackd. Some folks
use different interfaces, typically those with a mic, or guitar,
in addition to a keyboard. Unplugging usb or other devices, may
change the Chw/Phw assignments. I use a Mustang usb amp as input
for guitar, but it has no output, so I use the soundcard for that,
so it, usually is Chw:1,0 Phw:0,0 but I also have a usb modem, and
sometimes boot an OS from a usbstick, so it's not shocking anymore
if I forget to change things in qjackctl. 

[http://linux.die.net/man/1/jackd](http://linux.die.net/man/1/jackd)

 this page details all the jackd options, some are never or rarely needed, but it's good to know the
commonly used ones, to craft a special command.

It's also lucky to have live CD/dvd and usbstick installs of other
linux versions, as some hopscotching takes place with available
features and software, and we have the freedom to use them all :D
And sometimes a great software is available as an rpm or deb
but not both. An Maudio pci card, and slightly older nvidia card,
are often the best hardware basis for trouble free audio production in linux.

Cheers

---

### Post by Precipitous on 2011-10-21
> **sgx said:**
> Hi, the textfile .jackdrc is saved in your user folder by
qjackctl. It can be used as a command to start jackd. Some folks
use different interfaces, typically those with a mic, or guitar,
in addition to a keyboard. Unplugging usb or other devices, may
change the Chw/Phw assignments. I use a Mustang usb amp as input
for guitar, but it has no output, so I use the soundcard for that,
so it, usually is Chw:1,0 Phw:0,0 but I also have a usb modem, and
sometimes boot an OS from a usbstick, so it's not shocking anymore
if I forget to change things in qjackctl. 

[http://linux.die.net/man/1/jackd](http://linux.die.net/man/1/jackd)

 this page details all the jackd options, some are never or rarely needed, but it's good to know the
commonly used ones, to craft a special command.

It's also lucky to have live CD/dvd and usbstick installs of other
linux versions, as some hopscotching takes place with available
features and software, and we have the freedom to use them all :D
And sometimes a great software is available as an rpm or deb
but not both. An Maudio pci card, and slightly older nvidia card,
are often the best hardware basis for trouble free audio production in linux.

Cheers
@sgx:

Thank you for all of your help. It is really appreciated...

---

### Post by sgx on 2011-10-21
> **Precipitous said:**
> @sgx:

Thank you for all of your help. It is really appreciated...
My pleasure! :)

---

