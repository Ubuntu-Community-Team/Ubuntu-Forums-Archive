---
title: "Problem with qjackctl &amp; calfjackhost"
date: 2012-07-10
forum: Ubuntu Studio
---

### Post by eversisi on 2012-07-10
when I run the calf audio plugin using jack host, there was no audio going in (while the audio in/out working well outside of jack. 
Later, even the calf were not working...
the error message:
 
jackd 0.121.2
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_dummy.so
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_alsa.so
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_net.so
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_oss.so
getting driver descriptor from /usr/lib/i386-linux-gnu/jack/jack_firewire.so
JACK compiled with System V SHM support.
`default' server already active
Could not initialize JACK subsystem
:confused::confused::confused::confused:
 
 
Besides, I run qjackctl to check. It turned out to be not connected to server.
Error message:
 
12:22:08.503 Patchbay deactivated.
12:22:08.508 Statistics reset.
12:22:08.568 ALSA connection change.
12:22:08.686 D-BUS: Service not available (org.jackaudio.service aka jackdbus).
12:22:08.747 ALSA connection graph change.
:confused::confused::confused::confused:
 
Anyone has the experience on it?

---

### Post by CrocoDuck on 2012-07-10
Hi. Not sure to have really understood your problem, but it seems that jack was not launched by Qjackctl. Can you post details about your distro and how you installed jack and Qjackctl?

---

