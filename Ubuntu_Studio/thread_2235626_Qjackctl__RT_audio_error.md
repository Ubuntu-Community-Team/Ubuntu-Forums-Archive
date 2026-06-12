---
title: "Qjackctl  RT audio error"
date: 2014-07-22
forum: Ubuntu Studio
---

### Post by davstar on 2014-07-22
Hello i have pored over the Google, and everywhere on the internet searching for answers on how to fix Qjackctl D-bus error can't connect  to server i am lost on how to fix this problem and i do not know what any of the error data means if anyone in the world out there can point me in the right direction i will pass on the favor i promise. I just started using Linux/Ubuntu like a month ago when i finally got tired of Windows/Microsoft so i still a newbie. Please Help :confused:

 [COLOR=#999999]21:39:19.850 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]21:39:19.858 Statistics reset.[/COLOR]
 [COLOR=#cccc99]21:39:19.879 ALSA connection change.[/COLOR]
 [COLOR=#999999]21:39:19.940 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = Connection refused
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]21:39:19.952 ALSA connection graph change.[/COLOR]
 (qjackctl:8711): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:8711): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]21:39:55.639 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Mon Jul 21 21:39:30 2014: Starting jack server...
 Mon Jul 21 21:39:30 2014: JACK server starting in realtime mode with priority 10
 Mon Jul 21 21:39:30 2014: Acquired audio card Audio0
 Mon Jul 21 21:39:30 2014: creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|32bit
 Mon Jul 21 21:39:30 2014: configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
 Mon Jul 21 21:39:30 2014: ALSA: final selected sample format for capture: 32bit integer little-endian
 Mon Jul 21 21:39:30 2014: ALSA: use 3 periods for capture
 Mon Jul 21 21:39:30 2014: ALSA: final selected sample format for playback: 32bit integer little-endian
 Mon Jul 21 21:39:30 2014: ALSA: use 3 periods for playback
 Mon Jul 21 21:39:35 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Mon Jul 21 21:39:35 2014: ERROR: Driver is not running
 Mon Jul 21 21:39:35 2014: ERROR: Cannot open client name = dbusapi
 Mon Jul 21 21:39:35 2014: ERROR: failed to create dbusapi jack client
 Cannot connect to server socket err = Connection refused
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl:8711): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:8711): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]21:40:05.336 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 Cannot open qjackctl client
 Mon Jul 21 21:40:05 2014: ERROR: JackPosixProcessSync::LockedTimedWait error usec = 5000000 err = Connection timed out
 Mon Jul 21 21:40:05 2014: ERROR: Driver is not running
 Mon Jul 21 21:40:05 2014: ERROR: Cannot create new client

here is the error messages if someone out there in the world could help me read this and figure it out it would be Much Appreciated thanks in advance ;)

---

### Post by davstar on 2014-07-22
**[SOLUTION ]**

here's a solution that worked for me to get Qjackctl RT Active again :


Go to home 
press ctrl+H to show hidden files 
then Please delete **~/.jackdrc**, **~/.config/jack/conf.xml**, **~/.config/rncbc.org/QjackCtl.conf**. 
[U][B]
then do these: below[/B][/U]
[B]
ps -aux | grep jackd  [/B]
[B]
kill -9 "PID# of Jackd"[/B]

or if you're using Ubuntu studio you 
can just use Task Manager to kill processes

**jack_control start** >>>> [from terminal]
[B]
qjackctl& >>>>>[from terminal][/B]
or 

start Qjackctl from the Menu
that's it ... hope this helps ):P

Ubuntu Studio 14.04

---

