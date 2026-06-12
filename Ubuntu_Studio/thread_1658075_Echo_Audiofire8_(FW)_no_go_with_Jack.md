---
title: "Echo Audiofire8 (FW) no go with Jack"
date: 2011-01-02
forum: Ubuntu Studio
---

### Post by adamgood on 2011-01-02
Hi all,
Ok I give in...I would love some ideas from anyone. I can't seem to get Jack to find my firewire interface (Echo Firewire8). Worked in the past under UbuntuStudio 9.x something. Kicking myself for not taking notes back then! Everything seems to be in place, including manually switching off the wifi card which did the trick years ago.

Here are my specs:
Running... Ubuntu-Studio 10.10 i386
on a...Lenovo T61

These look good:
%%%%%
/etc/security/limits.d/audio.conf
says:
@audio   -  rtprio     95
@audio   -  memlock    unlimited
@audio   -  nice      -19
%%%%%
/etc/modprobe.d/blacklist-firewire.conf

#blacklist ohci1394
#blacklist sbp2
#blacklist dv1394
#blacklist raw1394
#blacklist video1394

blacklist firewire-ohci
blacklist firewire-sbp2

and I ran:
sudo update-initramfs -k all -u
%%%%%

Long output from qjackctl:

10:36:53.551 Patchbay deactivated.
10:36:53.552 Statistics reset.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:36:53.581 ALSA connection graph change.
10:36:53.778 ALSA connection change.
10:36:57.724 Startup script...
10:36:57.725 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: artsshell: not found
10:36:58.126 Startup script terminated with exit status=32512.
10:36:58.126 JACK is starting...
10:36:58.126 /usr/bin/jackd -dfirewire -r44100 -p64 -n4
10:36:58.128 JACK was started with PID=2547.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
00862250855:  (ffado.cpp)[  92] ffado_streaming_init: libffado 2.999.0- built Aug 11 2010 00:12:04
firewire ERR: FFADO: Error creating virtual device
Cannot attach audio driver
JackServer::Open() failed with -1
no message buffer overruns
Failed to start server
10:36:58.348 JACK was stopped with exit status=255.
10:36:58.348 Post-shutdown script...
10:36:58.348 killall jackd
jackd: no process found
10:36:58.755 Post-shutdown script terminated with exit status=256.
10:37:00.187 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:37:09.529 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
10:37:20.211 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

---

### Post by AutoStatic on 2011-01-02
```
firewire ERR: FFADO: Error creating virtual device
```
You don't have sufficient rights to access */dev/raw1394* probably. Is the raw1394 module loaded? Are you a  member of the audio group? Did you go through the steps here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) ?
And you don't need the nice line in */etc/security/limits.d/audio.conf*.

Best,

Jeremy

---

### Post by adamgood on 2011-01-02
> **AutoStatic said:**
> 

Did you go through the steps here: [https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire) ?



Jeremy, wauw HEEL erg bedankt for your quick reply! No I had not been through those steps:

UbuntuStudioControl/
Enable memlock
and
Enable raw1394 access

Did the trick and I'm recording and it's Christmas again thanks!

So another question, What happens with distros other than UbuntuStudio, how does one enable memlock and raw1394 access?

Happy day

Adam

---

