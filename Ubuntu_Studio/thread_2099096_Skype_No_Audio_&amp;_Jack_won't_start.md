---
title: "Skype: No Audio &amp; Jack won't start"
date: 2012-12-28
forum: Ubuntu Studio
---

### Post by bjoleniacz on 2012-12-28
Hi, I am new to Linux.  I just upgraded my Ubuntu 12.10 setup to the Ubuntu-Studio version.  Now I can't get Skype to work.  Firefix audio works just fine, but Skype has absolutely no sound.  It says when I try to do a Test Call it says "Problems with Audio-Playback".

I think the problem lies with Jack.  When I try to start it, I get this message:

>   p, li { white-space: pre-wrap; }  [COLOR=#999999]12:31:06.845 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:31:06.848 Statistics reset.[/COLOR]
 [COLOR=#cccc99]12:31:06.903 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:31:06.961 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]12:31:06.969 ALSA connection graph change.[/COLOR]
 (qjackctl.real:2902): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2902): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2902): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2902): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]12:31:08.691 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:2902): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2902): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 Fri Dec 28 12:31:08 2012: Starting jack server...
 Fri Dec 28 12:31:08 2012: JACK server starting in realtime mode with priority 10
 Fri Dec 28 12:31:08 2012: control device hw:0
 Fri Dec 28 12:31:08 2012: control device hw:0
 Fri Dec 28 12:31:08 2012: Acquired audio card Audio0
 Fri Dec 28 12:31:08 2012: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
 Fri Dec 28 12:31:08 2012: control device hw:0
 Fri Dec 28 12:31:08 2012: [1m[31mERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode[0m
 Fri Dec 28 12:31:08 2012: [1m[31mERROR: Cannot initialize driver[0m
 Fri Dec 28 12:31:08 2012: [1m[31mERROR: JackServer::Open failed with -1[0m
 Fri Dec 28 12:31:08 2012: [1m[31mERROR: Failed to open server[0m
 Fri Dec 28 12:31:09 2012: Saving settings to "/home/brian/.config/jack/conf.xml" ...
 [COLOR=#ff0000]12:31:12.219 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl.real:2902): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
 (qjackctl.real:2902): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion `GTK_IS_WIDGET (widget)' failed
Any help would be appreciated!

---

### Post by BrianSwatton on 2013-01-01
I'm no expert with this stuff, but it looks like the server itself isn't being found by the GUI QjackCtl. I presume that this what you are using.

In QjackCtl's setup dialogue (settings tab)  there is an entry for server path, here's what mine looks like.

```
pasuspender --server=/usr/bin/jackd
```I'm using pasuspender here to suspend pulseaudio because I had them conflicting on a previous setup (11.10),  you've probably got just the  "/usr/bin/jackd" part. That file needs to exist and be accessible.

What do you have set for server path?

---

### Post by bazsound on 2013-01-08
if a program is using the soundcard jack want be able to start, 

Also make sure your user is part of the audio group, i cant remember the commands but you should be able to find them by searching.

When i installed ubuntu 12.10 i wasnt in the audio group and jack wouldnt start without root, also it wont start if say firefox is open or another web browser or other program that is using the sound card.

I usually start jack first before any other program, once jack is started the pulse audio module should load and allow non jack aware programs to use sound through jack

---

