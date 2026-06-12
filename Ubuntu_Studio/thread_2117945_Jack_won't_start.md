---
title: "Jack won't start"
date: 2013-02-19
forum: Ubuntu Studio
---

### Post by CVarin on 2013-02-19
I'm running Ubuntu Studio 12.04 on my desktop computer.  All of a sudden, jack has stopped working.  Under the settings window, it no longer shows my usb devices, a Focusrite Scarlett 2i2 or an Art Dual Preamp, at least not by name. They both work fine until I try to start jack. Everything works fine from the live CD.  Under the installed system, jack won't start.   I get a series of 4 popups.  The only thing I've done recently other than normal updates that might have caused this is I installed the MATE shell/Desktop.  I uninstalled it, but nothing changed.  I'm stumped.  I really hate to think about reinstalling the whole system again, so I thought I'd see if anyone has any ideas first.  Thanks for any help.  Here's a copy of the messages:  

Popup 1:

D-BUS: SetParameterValue('driver:ignorehw', 'false'):

Invalid container address 'driver':'ignorehw':'(null)' supplied to method 'SetParameterValue'..
(org.jackaudio.Error.InvalidArgs)

popup 2:
D-BUS: SetParameterValue('driver:wordlength', '16'):

Invalid container address 'driver':'wordlength':'(null)' supplied to method 'SetParameterValue'..
(org.jackaudio.Error.InvalidArgs)

popup 3:
D-BUS: JACK server could not be started.

Sorry

popup 4:
Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.

Output of message window:
20:03:01.766 Patchbay deactivated.
20:03:01.773 Statistics reset.
20:03:01.784 ALSA connection change.
20:03:01.798 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:03:01.807 ALSA connection graph change.
20:03:07.166 D-BUS: SetParameterValue('driver:ignorehw', 'false'): Invalid container address 'driver':'ignorehw':'(null)' supplied to method 'SetParameterValue'.. (org.jackaudio.Error.InvalidArgs)
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

I then opened a terminal and entered the following command, which I found in another thread.  I have no idea what this command actually does, but it seems to be relevant.

chase@chase-GeForce6100PM-M2:~$ jackd -d alsa -r 44100
jackdmp 1.9.8
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control open "hw:0" (No such file or directory)
control device hw:0
control open "hw:0" (No such file or directory)
audio_reservation_init
Acquire audio card Audio-1
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
control open "hw:0" (No such file or directory)
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_hw.c:1401:(_snd_pcm_hw_open) Invalid value for card
ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Cannot initialize driver
JackServer::Open() failed with -1
Failed to open server
chase@chase-GeForce6100PM-M2:~$

---

### Post by DjRadu on 2013-02-19
In Ubuntu Software center there is somenthing called JACK TO ALSA BRIDGE or ALSA TO JACK BRIDGE it works for me hope it will work for you !

---

