---
title: "Trying to use wineasio in Mixcraft...jackd, qjackctl troubles"
date: 2013-05-26
forum: Ubuntu Studio
---

### Post by gargoyles on 2013-05-26
Hey guys, I'm pretty new to Ubuntu, but I've tried to do a fair bit of searching on this and am still having trouble.

I'm running 13.04, completely upgraded. 
Installed wine and wineasio to run with Mixcraft

Followed this guys instructions to get it running - [http://forum.cockos.com/showthread.php?t=107106](http://forum.cockos.com/showthread.php?t=107106)

Opened mixcraft and tested and it was working great. Then, I try to lower my latency by lowing the frames/period (don't actually know this does... I'm just messing with stuff) and I haven't been able to get it to work since.

Now when I try to start Qjackctl I get this
> 
 [COLOR=#999999]12:32:09.931 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:32:09.931 Statistics reset.[/COLOR]
 [COLOR=#cccc99]12:32:09.979 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:32:09.996 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#ff0000]12:32:10.400 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]12:32:10.450 ALSA connection graph change.[/COLOR]
 (qjackctl:10043): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl:10043): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Sun May 26 12:32:10 2013: Starting jack server...
 Sun May 26 12:32:10 2013: JACK server starting in non-realtime mode
 Sun May 26 12:32:10 2013: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio1": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1
 Sun May 26 12:32:10 2013: ERROR: Failed to acquire device name : Audio1 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1
 Sun May 26 12:32:10 2013: ERROR: Audio device hw:CODEC cannot be acquired...
 Sun May 26 12:32:10 2013: ERROR: Cannot initialize driver
 Sun May 26 12:32:10 2013: ERROR: JackServer::Open failed with -1
 Sun May 26 12:32:10 2013: ERROR: Failed to open server
 Sun May 26 12:32:11 2013: Saving settings to "/home/narg/.config/jack/conf.xml" ...
 [COLOR=#ff0000]12:32:13.761 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started



So, I started manually starting jackd in terminal with 

jackd -R -d alsa

terminal reads

> narg@Narg:~$ jackd -R -d alsa
jackdmp 1.9.9.5
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2012 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA Intel at 0xe0a00000 irq 45
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

And now upon opening qjackctl, it appears to be working.. I get 

 > [COLOR=#999999]12:42:06.371 Patchbay deactivated.[/COLOR]

 [COLOR=#999999]12:42:06.378 Statistics reset.[/COLOR]
 [COLOR=#cccc99]12:42:06.407 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:42:06.424 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#9999cc]12:42:06.469 JACK connection change.[/COLOR]
 [COLOR=#999999]12:42:06.493 Client activated.[/COLOR]
 (qjackctl:10407): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl:10407): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed



Don't know what those last two lines mean...

I go back into Mixcraft, I can choose the wineasio driver, it even shows system and mixcraft being properly connected in qjackctl, but for some reason I get no audio actually coming through.

I hope someone can follow this and that it makes sense.

Any help is greatly appreciated!

---

