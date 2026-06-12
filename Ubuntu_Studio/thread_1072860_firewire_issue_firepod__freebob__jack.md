---
title: "firewire issue? firepod / freebob / jack"
date: 2009-02-17
forum: Ubuntu Studio
---

### Post by cheapclouds on 2009-02-17
hmm. im flustered!

i have used my firepod successfully several times via freebob, jack, and ardour. however, very often it just inexplicably stops working. 

sometimes the solution is simply to unplug the firewire cable from one of the ports on the firepod and plug it into the other one, or back into the same one. both work for the same purpose. also, sometimes its as simple as rebooting. ive tried everything i normally try when this happens, to no avail. i think at this point that im just getting myself confused.

i have the line in /etc/udev/permissions changed to "audio" as described in several other posts of this nature. 

i was gonna try and get this FFADO driver i hear about, but i can't seem to for some reason. 

heres what happens when i try to start jack:

jacob@cloud:~$ jackd -d freebob
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: No such file or directory
Is ieee1394 and raw1394 driver loaded?
Fatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
Fatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
LibFreeBoB ERR: cannot create libfreebob handle
cannot load driver module freebob
no message buffer overruns
jacob@cloud:~$ 



any help would be much appreciated!

thanks
jacob

---

