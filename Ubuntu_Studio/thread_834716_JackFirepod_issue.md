---
title: "Jack/Firepod issue"
date: 2008-06-19
forum: Ubuntu Studio
---

### Post by Thelonius on 2008-06-19
I am running Hardy, and want to use my firepod to record with ardour. I have read all posts concerning getting this setup up and running, and have changed the necessary permissions, settings, and whatnot. However, every time I start up Jack, it crashes immediately and I get this error message:

[I]15:41:17.710 Patchbay deactivated.
15:41:17.863 Statistics reset.
15:41:18.020 ALSA connection graph change.
15:41:18.308 ALSA connection change.
15:41:25.072 Startup script...
15:41:25.073 artsshell -q terminate
15:41:25.770 Startup script terminated with exit status=256.
15:41:25.771 JACK is starting...
15:41:25.771 /usr/bin/jackd -dfreebob -r44100 -p1024 -n3 -D
15:41:25.787 JACK was started with PID=6022.
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: No such file or directory
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
LibFreeBoB ERR: cannot create libfreebob handle
FreeBoB ERR: FREEBOB: Error creating virtual device
[0mcannot load driver module freebob
15:41:26.596 JACK was stopped successfully.
15:41:26.597 Post-shutdown script...
15:41:26.597 killall jackd
15:41:26.598 JACK has crashed.
jackd: no process killed
15:41:27.007 Post-shutdown script terminated with exit status=256.
15:41:28.646 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

Any ideas? Am I just missing something obvious? Do I need to install the realtime kernel for this to work? Thank you for any suggestions.

---

### Post by Thelonius on 2008-06-20
bump

---

### Post by Stochastic on 2008-06-20
It looks like you're missing your firewire drivers (do an "apt-cache search 1394" and see what comes up that looks like it might satisfy your iee1394 and raw1394 issues).  Also, double check that you've granted permissions to the user for raw1394 access.

You don't NEED the realtime kernel, but you'll notice a significant performance boost (less dropouts / xruns) with your audio apps.  I'd **highly recommend** installing the ubuntustuio-audio and ubuntustudio-audio-plugins meta packages if you've got a firepod and want to use it.  Chances are that those will fix the problems you're having too.

---

