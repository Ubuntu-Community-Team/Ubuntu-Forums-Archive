---
title: "Tried all the fixes, QJackctl still not working..."
date: 2015-10-30
forum: Ubuntu Studio
---

### Post by myrrdinoftheforest on 2015-10-30
I have been very unsuccessful in getting Jack to work. I just want it to work... I don't care what levels of hell I have to trek through... Here are the error codes I'm getting:

 [COLOR=#999999]17:15:31.263 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:15:31.264 Statistics reset.[/COLOR]
 [COLOR=#cccc99]17:15:31.281 ALSA connection change.[/COLOR]
 [COLOR=#999999]17:15:31.307 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]17:15:31.313 ALSA connection graph change.[/COLOR]
 (qjackctl:3637): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3637): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]17:15:33.195 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl:3637): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3637): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 Fri Oct 30 17:15:33 2015: Starting jack server...
 Fri Oct 30 17:15:33 2015: JACK server starting in realtime mode with priority 10
 Fri Oct 30 17:15:33 2015: Acquired audio card Audio0
 Fri Oct 30 17:15:33 2015: creating alsa driver ... -|hw:0|1024|2|192000|0|0|nomon|swmeter|-|32bit
 Fri Oct 30 17:15:33 2015: ERROR: ALSA: Cannot open PCM device alsa_pcm for capture. Falling back to playback-only mode
 Fri Oct 30 17:15:33 2015: ERROR: Cannot initialize driver
 Fri Oct 30 17:15:33 2015: ERROR: JackServer::Open failed with -1
 Fri Oct 30 17:15:33 2015: ERROR: Failed to open server
 Fri Oct 30 17:15:34 2015: Saving settings to "/home/ken/.config/jack/conf.xml" ...
 [COLOR=#ff0000]17:15:38.259 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started

---

### Post by myrrdinoftheforest on 2015-10-31
Figured it out. Turns out the culprit all along was the driver for my audio interface. If I chose my Tascam US-122 as my input device, it crashed. When i choose my on board sound it does not.

---

