---
title: "USB Audio Interface (E-MU Tracker Pre)"
date: 2012-10-26
forum: Ubuntu Studio
---

### Post by ZoxX on 2012-10-26
I installed Ubuntu Studio 12.10 from DVD on brand new computer, I had 12.10 on my old computer initially installed from DVD as 9.04 and upgraded gradually to 12.10.
From 11.04 (if I'm not wrong) Ubuntu Studio has Unity GUI. And it was like that up to (and including) 12.10. My brand new installation has old fashion GUI (which is OK but I wonder why).
Back then when I installed my first Ubuntu Studio my Audio Interface E-MU Tracker Pre USB 2.0 worked right from the beginning. I was able to play audio in any player, record and play in Audacity and Ardour. When I was installing the software on-board audio was disabled in BIOS. On my brand new computer it was enabled (I forgot to disable it). Now if I disable on-board audio there is no sound at all.
Terminal 'lsusb' lists Tracker Pre as USB device.
Ardour recognise USB AUDIO and ALC889 Analog. But if I start audio engine with any of them I get:
Ardour could not start JACK
1) You requested audio parameters that are not supported
2) JACK is running as another user
Audacity recognise USB Tracker Pre and a lot of analog and digital inputs and outputs. The playback is fine with Analog Output. But USB Tracker Pre output gives me:
Error while opening sound device. Please check the output device settings and the project sample rate.
I reinstalled all JACK and ALSA packages in no avail.
Does anyone has any idea how to overcome the problem without reinstalling the entire Ubuntu Studio.

---

### Post by sgx on 2012-10-26
jackd -d alsa -r 44100

This should start jackd, then start qjackctl,
and choose the desired devices on the Setup page.

Input Device >
Output Device >

If jackd won't start, use sudo jackd -d alsa -r 44100
and sudo qjackctl.

If desired, you can blacklist the intel chip,
use lsmod to see its name, and make a
textfile named blacklist in /etc/modprobe.d
containing a line like

blacklist snd_intel8x0

Cheers

---

### Post by ZoxX on 2012-10-27
> **sgx said:**
> jackd -d alsa -r 44100

This should start jackd, then start qjackctl,
and choose the desired devices on the Setup page.

Input Device >
Output Device >


Thank you. I did it. Obviously JACK wasn't installed at all. So I installed JACK via apt-get. Now I was able to start jackd. In QjackCtl Setup I changed Input and Output device to USB Tracker Pre. QjackCtl [Start] worked smoothly but I still have just motherboard audio. Furthermore Chromium browser has no sound until I stop jackd. Audacious plays well via motherboard audio.
After reboot I must start jackd manually. In my old set-up everything was fine from the beginning.

> **sgx said:**
> If jackd won't start, use sudo jackd -d alsa -r 44100
and sudo qjackctl.

If desired, you can blacklist the intel chip,
use lsmod to see its name, and make a
textfile named blacklist in /etc/modprobe.d
containing a line like

blacklist snd_intel8x0


Everything worked without sudo. I found snd_hda_intel but didn't create blacklist. I will try this later.

---

### Post by ZoxX on 2012-10-28
I tried the following:
[FONT="Courier New"]zoxx@zoxx-Z68AP-D3:~$ jackd -d alsa -d hw:1 -r 41000
jackdmp 1.9.9
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2012 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:1
control device hw:1
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|1024|2|41000|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 41000Hz, period = 1024 frames (25.0 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 2 periods for capture
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
[/FONT]
My USB Tracker Pre is device hw:1. Everything seems fine until the last step.

---

### Post by sgx on 2012-10-28
Hi, qjackctl Setup page, Periods/Buffer should be 3, for usb
and firewire interfaces. In the Misc tab, is
'Enable D-bus interface', try this both ways,
reboot between tries.

Also on the Misc tab, you can tick the
'Start Jack audio server' box,
handy if you use mainly just one configuration.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

links 4 and 8 at the wiki have screenshots and tips
to configure jackd and qjackctl.

top, htop, and the command

ps ux

will show what is running on your system. If anything
named pulse is running, command

killall pulseaudio

then restart jackd, and qjackctl.
Cheers

also, alsa-firmware package may need installing, using synaptic,
and some e-mu user info is at these links

[http://www.waveguide.se/?article&tag=alsa](http://www.waveguide.se/?article&tag=alsa)

[http://timhodson.com/e-mu-1820-and-ubuntu/](http://timhodson.com/e-mu-1820-and-ubuntu/)

---

### Post by ZoxX on 2012-11-03
I tried everything suggested.
JACK Messages:
[FONT="Courier New"]16:20:45.588 Patchbay deactivated.
16:20:45.595 Statistics reset.
16:20:45.648 ALSA connection change.
16:20:45.657 JACK is starting...
16:20:45.657 /usr/bin/jackd -P1 -dalsa -r44100 -p512 -n3 -D -Chw:1 -Phw:1
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
16:20:45.684 ALSA connection graph change.
jackdmp 1.9.9
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2012 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 1
16:20:45.733 JACK was started with PID=2672.
control device hw:1
control device hw:1
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|512|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
configuring for 44100Hz, period = 512 frames (11.6 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: cannot set hardware parameters for capture
ALSA: cannot configure capture channel
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
16:20:45.765 JACK was stopped with exit status=255.
16:20:47.863 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started[/FONT]

I said I wouldn't like to reinstall Ubuntu Studio. But I did. And I did it several times with 12.10 on the other HDD. This time on-board sound disabled in BIOS. Tried different USB ports as well. In no avail.
Remembering how easy it was with Ubuntu Studio 9.04 I tried my old DVD. It was in bad state so it didn't work. Then I downloaded old version 11.04 It took much more time to install than 12.10.
No sound at all. I upgraded to 11.10, which brings Unity along. No sound. Then 12.04. No sound. And finally 12.10. No sound. It looks completely different (Unity) from 12.10 installed via DVD.
I'm noob to Linux and I lived without terminal for years with Ubuntu. The only thing I needed terminal for was to start
[FONT="Courier New"]sudo vi /boot/grub/grub.cfg[/FONT] 
to set Windows as default boot partition. I know it sounds weird, a noob is preferring vi over GUI editors, but I spent 14 years with Unix.
I was recording and mixing using Ardour without knowing what JACK is. Now I read those articles and have some idea.
Would someone please explain me the above JACK messages.

---

### Post by ZoxX on 2012-11-03
Maybe this can help just to show that Ubuntu is aware of Tracker Pre.
[FONT="Courier New"]zoxx@zoxx-Z68AP-D3:~$ cat /proc/asound/cards
 1 [USB            ]: USB-Audio - E-MU Tracker Pre | USB
                      E-MU Systems, Inc. E-MU Tracker Pre | USB at usb-0000:02:00.0-2, high speed
[/FONT]

---

