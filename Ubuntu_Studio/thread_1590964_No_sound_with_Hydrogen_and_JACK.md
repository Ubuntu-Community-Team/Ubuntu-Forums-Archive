---
title: "No sound with Hydrogen and JACK"
date: 2010-10-08
forum: Ubuntu Studio
---

### Post by Dorian17xD on 2010-10-08
Hi, 

I am having this issue, basically I want to record on Ardour my electro-acoustic guitar and Hydrogen at the same time.

When I connect my guitar pedal to use it as a sound interface JACK and ALSA detects it and works fine with it, however Hydrogen only gives me output on ALSA.

The system has 2 sound cards, an Intel HDA sound card and a Genius PCI Sound Card, when I connect my guitar pedal it's being detected as a sound card too.

I use by default the Genius PCI Sound Card and I don't know any way to disable the Intel HDA sound card on my Ubuntu 10.04 box.

Returning back to Hydrogen, when I switch it to JACK, Jack recognizes that hydrogen is running but I don't have any audio on it.

Any ideas?

---

### Post by Pablo_F on 2010-10-08
I suggest disabling the onboard card form the BIOS. 

What it is not clear to me is the hardware configuration. You want to capture the guitar sound through what soundcard and you want to play the audio through what soundcard? The guitar pedal? The Genius? The guitar pedal for input and the genius for output? What kind of guitar pedal is it, and can you give the output of the following command?

aplay -l

Cheers! Pablo

---

### Post by Dorian17xD on 2010-10-09
Hi Pablo, let me clarify this, I want to record my guitar using the Guitar Pedal, it's a Zoom A2.1u, it works fine on ALSA because I was able to record with it on Jokosher.

My main issue here it's the onboard card cannot be disabled on the BIOS, I already tried that since on previous versions of Ubuntu I had to do it to get my Genius sound card working.

My main problem here is Hydrogen, when I switch it from ALSA to JACK, Jack recognizes that Hydrogen it's running but I don't get any output from it using my Genius sound card or the guitar pedal that when it's connected it behaves as a sound card in a obvious way so I can hear when I am recording.

I know, on old versions of Ubuntu there was one alsa package that was able to disable the onboard card but on Ubuntu 9.10 and 10.04 that package was removed, don't know why.

This is what I obtain when I connect my guitar pedal to the computer and I run aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Hope this is what you are looking for, even though I will look again on the BIOS to see if maybe there's something I didn't see before.

My motherboard is a Intel D946GZIS. I am going to look for any BIOS update if available and install it.

Thank you :)

---

### Post by Pablo_F on 2010-10-09
Hi!

Disabling the onboard card from the BIOS is a good idea as long as you don't intend to use it, but it is not strictly necessary.

The "alsa" term is very tricky. It means a lot of things depending on the context.

As a proof of concept:

Launch qjackctl (Jack Control gui). In the setup choose the audio card that jack will use. The best thing is write it down. In your case:

hw:CMI8738

if you want to use the Genius, or:

hw:default

for the guitar pedal

Start the server with the Start button and then launch hydrogen and set it to use the jack audio system.

In the connection window of qjackctl, make sure that the audio of hydrogen is connected to the system: playbacks (representing your card's outputs). Look at the audio tab. The alsa tab refers to midi (alsa midi).

Of course, make sure that your speakers are connected to the card that you selected as your interface in Jack Control.

If you don't run jack, before launching hydrogen, it is normal that hydrogen does not make sounds when set to jack audio.

Cheers! Pablo

---

### Post by Dorian17xD on 2010-10-09
Hi again, 

> **Pablo_F said:**
> 
The "alsa" term is very tricky. It means a lot of things depending on the context.


Yeah sorry 'bout that didn't think about it.

Well I got news now I just turned off the onboard card, because the BIOS update that I just installed from Intel was the way to get that option, it seems by default Intel disabled that option to be available in my mother board.

Well now the thing is that on qtjackctl I am receiving this list of errors:

```
10:23:30.983 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

And then, if I switch from the Genius sound card to the guitar pedal, or vice versa, on the Sound Preferences window for Gnome I am getting this list of errors:

```
10:25:34.080 Startup script...
10:25:34.082 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
10:25:34.488 Startup script terminated with exit status=32512.
10:25:34.489 JACK is starting...
10:25:34.489 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2 -Xraw
10:25:34.497 JACK was started with PID=7115.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control open "hw:0" (No such file or directory)
control open "hw:0" (No such file or directory)
audio_reservation_init
Acquire audio card Audio-1
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control open "hw:0" (No such file or directory)
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
10:25:34.829 JACK was stopped with exit status=255.
10:25:34.831 Post-shutdown script...
10:25:34.832 killall jackd
jackd: no process found
10:25:35.254 Post-shutdown script terminated with exit status=256.
10:25:36.523 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:25:40.933 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:25:49.748 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:26:07.368 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:26:42.619 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
```

I already reinstalled Jack just to let you know.

Thank you again.

---

### Post by Pablo_F on 2010-10-09
Hi, 

The card you choose in the gnome sound preferences is completely irrelevant for jack. That is a front-end for pulseaudio.

The messages say that jack cannot find hw:0. So it must be a non-existing interface. Probably, hw:0 WAS the onboard, but it is not there anymore.

Check in a terminal:

cat /proc/asound/cards

I guess you will have something like (simplifying):

1 Genius
2 guitar pedal

If this is the case, in the setup, you have to select or write down either:

hw:1
or
hw:CMI8738

if you want jack to use the Genius, or:

hw:2
or
hw:default

for the guitar pedal

I recommend using the names because alsa can mix up the numerical card ID's. 

Cheers! Pablo

---

