---
title: "lash jack-rack problem"
date: 2008-06-16
forum: Ubuntu Studio
---

### Post by idran2 on 2008-06-16
Hi to all.
I'm a newbie of ubuntu with a problem with my sound card. I've kubuntu 8.04 with ubuntu desktop installed, the Hercules Game Theater Xp sound card that ubuntu recognize it as CS46xx.
I've a problem using jack audio connection kit. I try to find help in some IRC channel and they help me telling me that is a lash problem but no one can resolve my problem.:(
This is the logs of lashd, jack-rack and jack control from terminal:

-jack-rack-
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Status update: jack_rack_6049
fabio@casa:/home$ jack_mgr_init_jack: could not connect to jackd, exiting
loader_run: server closed socket; exiting

-lashd-
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
jack_mgr_init_jack: could not connect to jackd, exiting
loader_run: server closed socket; exiting

-jack control output-
11:00:34.648 Patchbay deactivated.
11:00:34.749 Statistics reset.
11:00:34.760 Startup script...
11:00:34.760 artsshell -q terminate
11:00:34.865 ALSA connection graph change.
sound server terminated
11:00:35.448 Startup script terminated successfully.
11:00:35.448 JACK is starting...
11:00:35.449 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
11:00:35.481 JACK was started with PID=7505.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
11:00:35.522 JACK was stopped successfully.
11:00:35.523 Post-shutdown script...
11:00:35.523 killall jackd
11:00:35.677 ALSA connection change.
jackd: nessun processo terminato
11:00:35.981 Post-shutdown script terminated with exit status=256.
11:00:37.684 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

I see that there are some parameter that doesn't match with my sound card: 48000hz and 32bit; my sound card specification are max 44100 and 16bit. It's important this?:confused:

I must using multitrak editor like qtractor or rosegarden to do a work but this program need jack server to act!
Thanks for the help! :)

---

### Post by Stochastic on 2008-06-17
First, don't worry about getting LASH or Jack-Rack running until Jack can successfully run (either from command line, or through qjackctl/jack control).  Can you post the output of Jack Control after a fresh reboot (don't open firefox or any other programs before attempting to start jack).  Also can you open the settings section of jack control, and post a screenshot of that?

---

### Post by idran2 on 2008-06-17
Ok: I have reboot the PC and turn off my dsl-router. After this, i start up the system and the first thing that I do is running jack control. This is the output and above the screenshot of the configs! 

09:26:20.772 Patchbay deactivated.
09:26:20.900 Statistics reset.
09:26:20.911 Startup script...
09:26:20.912 artsshell -q terminate
09:26:21.036 ALSA connection graph change.
09:26:21.381 Startup script terminated with exit status=256.
09:26:21.382 JACK is starting...
09:26:21.382 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n3
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
09:26:21.396 JACK was started with PID=6702.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
09:26:21.461 JACK was stopped successfully.
09:26:21.462 Post-shutdown script...
09:26:21.462 killall jackd
09:26:21.592 ALSA connection change.
jackd: nessun processo terminato
09:26:21.869 Post-shutdown script terminated with exit status=256.
09:26:23.598 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Here my jack control settings. (I try also to select some different settings but they doesn't work; now the settings are as showed here)
[IMG]http://img292.imageshack.us/img292/5117/jackcontrol1xr1.png[/IMG]

[IMG]http://img142.imageshack.us/img142/4585/jackcontrolmiscrn8.png[/IMG]

N.B: sorry for my English!

---

### Post by Stochastic on 2008-06-17
try going into System -> Administration -> Synaptic Package Manager and do a search for ALSA
then look for all the green boxes found, right-click them and choose "mark for re-installation" then select apply.

Could you then post the output of Jack again?  If you get the same message, try turning on "Force 16-bit" and "Verbose" options in jack control's settings, then re-post the output.

---

### Post by idran2 on 2008-06-17
I've get jack stated changing my changing frames period into 16!:lolflag:
But after this, I can't hear well the output. My output was as a robot. A voice was like a "tr tr tr..." 
I change some configs like buffer and latency and the sound now is ok!

---

