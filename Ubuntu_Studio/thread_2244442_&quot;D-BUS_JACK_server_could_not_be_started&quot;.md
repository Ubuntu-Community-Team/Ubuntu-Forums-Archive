---
title: "&quot;D-BUS: JACK server could not be started&quot; after clean install"
date: 2014-09-16
forum: Ubuntu Studio
---

### Post by alb2 on 2014-09-16
[B]Hello there!

I am relatively new to Ubuntu (I have used it for about a year without ever needing to do any fancy stuff) and have now looked into Ubuntu Studio to engage myself in the production of music. It works fine on my laptop but on my stationary PC after a clean install I can't get Jack to function properly.
I've seen a few threads with this particular Jack startup error, yet no solutions, as the OPs all seemingly figured it out for themselves at some point.

When starting Jack using qjackctl I get the following message:[/B]

 D-BUS: JACK server could not be started.

 Sorry

**followed by this one:**

"Could not connect to JACK server as client.

 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info."

**Checking the messages, this is what I see:**

15:46:53.502 Patchbay deactivated.
15:46:53.522 Statistics reset.
15:46:53.562 ALSA connection change.
15:46:53.908 D-BUS: Service is available (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
15:46:53.917 ALSA connection graph change.
(qjackctl:2069): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2069): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
15:46:55.328 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:2069): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2069): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
Tue Sep 16 15:46:55 2014: Starting jack server...
Tue Sep 16 15:46:55 2014: JACK server starting in realtime mode with priority 10
Tue Sep 16 15:46:55 2014: Acquired audio card Audio0
Tue Sep 16 15:46:55 2014: creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Tue Sep 16 15:46:55 2014: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
Tue Sep 16 15:46:55 2014: ERROR: Cannot initialize driver
Tue Sep 16 15:46:55 2014: ERROR: JackServer::Open failed with -1
Tue Sep 16 15:46:55 2014: ERROR: Failed to open server
Tue Sep 16 15:46:56 2014: Saving settings to "/home/alb/.config/jack/conf.xml" ...
15:47:01.087 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

[B]I have tried killing and removing pulseaudio, all the packages ensuring jack/alsa-compatibility are installed by default, I am part of the audio group and it doesn't seem to work in either 32 or 64 bit Ubuntu Studio.
Would one of You kindly help me?[/B]

---

### Post by jejeman on 2014-09-16
Give
```
aplay -l
```

---

### Post by alb2 on 2014-09-17
**Thank You for answering so swiftly. This is what I get:**

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by jejeman on 2014-09-17
Looks like you need to use Card1 (hw:1).

---

### Post by alb2 on 2014-09-17
[B]That sadly didn't work, neither did any of the other options Jack presents me with.
 This is what I get:[/B]

 [COLOR=#999999]21:01:41.351 Patchbay deactivated.[/COLOR]

 [COLOR=#999999]21:01:41.351 Statistics reset.[/COLOR]
 [COLOR=#cccc99]21:01:41.364 ALSA connection change.[/COLOR]
 [COLOR=#999999]21:01:41.373 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]21:01:41.382 ALSA connection graph change.[/COLOR]
 (qjackctl:12067): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:12067): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]21:01:49.887 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl:12067): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:12067): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 Wed Sep 17 21:01:49 2014: Starting jack server...
 Wed Sep 17 21:01:49 2014: JACK server starting in realtime mode with priority 10
 Wed Sep 17 21:01:49 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio1": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1
 Wed Sep 17 21:01:49 2014: ERROR: Failed to acquire device name : Audio1 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio1
 Wed Sep 17 21:01:49 2014: ERROR: Audio device hw:Generic_1 cannot be acquired...
 Wed Sep 17 21:01:49 2014: ERROR: Cannot initialize driver
 Wed Sep 17 21:01:49 2014: ERROR: JackServer::Open failed with -1
 Wed Sep 17 21:01:49 2014: ERROR: Failed to open server
 Wed Sep 17 21:01:51 2014: Saving settings to "/home/alb/.config/jack/conf.xml" ...
 [COLOR=#ff0000]21:01:59.180 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started

---

### Post by jejeman on 2014-09-18
Looks like the card was already in use. Try turning off jackdbus, to use just jackd. Basically you are on your own, thats how it is with JACK.

---

### Post by alb2 on 2014-09-19
Okay, thank You!

---

