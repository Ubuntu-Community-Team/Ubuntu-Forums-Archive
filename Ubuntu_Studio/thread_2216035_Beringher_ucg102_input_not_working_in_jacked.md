---
title: "Beringher ucg102 input not working in jacked"
date: 2014-04-09
forum: Ubuntu Studio
---

### Post by tokarustsc on 2014-04-09
i have browsed the forums and attempted many methods suggested by ubuntuforums users, but have still been unable to get my beringher ucg102 to work. i get this error message when i try to select the usb guitar link interface directly in input:

 [COLOR=#999999]12:09:17.213 Patchbay deactivated.[/COLOR]

 [COLOR=#999999]12:09:17.214 Statistics reset.[/COLOR]
 [COLOR=#cccc99]12:09:17.235 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:10:07.299 D-BUS: Service not available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot read socket fd = 22 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 [COLOR=#66cc99]12:10:12.316 ALSA connection graph change.[/COLOR]
 (qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#999999]12:10:32.973 JACK is starting...[/COLOR]
 [COLOR=#990099]12:10:32.974 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p256 -n3 -D -Chw:CODEC[/COLOR]
 Cannot read socket fd = 22 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 no message buffer overruns
 no message buffer overruns
 (qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#999999]12:10:33.044 JACK was started with PID=1958.[/COLOR]
 no message buffer overruns
 `default' server already active
 Failed to open server
 jackdmp 1.9.10
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2013 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]12:10:33.074 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]12:10:40.245 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 Cannot read socket fd = 22 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 (qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

and this error when trying to run it with the default settings suggested by various other ubuntu studio users 

 

[COLOR=#999999](qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
 [COLOR=#999999](qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
 [COLOR=#999999](qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
 [COLOR=#999999](qjackctl:1947): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed[/COLOR]
 [COLOR=#999999]12:15:39.157 JACK is starting...[/COLOR]
 [COLOR=#990099]12:15:39.158 /usr/bin/jackd -dalsa -dhw:0 -r44100 -p256 -n3[/COLOR]
 [COLOR=#999999]Cannot read socket fd = 22 err = Success[/COLOR]
 [COLOR=#999999]CheckRes error[/COLOR]
 [COLOR=#999999]JackSocketClientChannel read fail[/COLOR]
 [COLOR=#999999]Cannot open qjackctl client[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]12:15:39.211 JACK was started with PID=1973.[/COLOR]
 [COLOR=#999999]no message buffer overruns[/COLOR]
 [COLOR=#999999]`default' server already active[/COLOR]
 [COLOR=#999999]Failed to open server[/COLOR]
 [COLOR=#999999]jackdmp 1.9.10[/COLOR]
 [COLOR=#999999]Copyright 2001-2005 Paul Davis and others.[/COLOR]
 [COLOR=#999999]Copyright 2004-2013 Grame.[/COLOR]
 [COLOR=#999999]jackdmp comes with ABSOLUTELY NO WARRANTY[/COLOR]
 [COLOR=#999999]This is free software, and you are welcome to redistribute it[/COLOR]
 [COLOR=#999999]under certain conditions; see the file COPYING for details[/COLOR]
 [COLOR=#999999]12:15:39.243 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]12:15:46.219 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 [COLOR=#999999]Cannot read socket fd = 22 err = Success[/COLOR]
 [COLOR=#999999]CheckRes error[/COLOR]
 [COLOR=#999999]JackSocketClientChannel read fail[/COLOR]
 [COLOR=#999999]Cannot open qjackctl client


can anyone help me with this? i have recently switched from windows to ubuntu studio, and would like to at least be able to record some sort of sound. i have tried using different usb ports, and different hardware configs. nothing seems to work

[/COLOR]

---

### Post by jejeman on 2014-04-09
Don't mix soundcards, try 48000 samplerate.

---

### Post by tokarustsc on 2014-04-09
Ive tried everything but using 48000 samplerate. ive even used the methods described here [http://ubuntuforums.org/showthread.php?t=1457334](http://ubuntuforums.org/showthread.php?t=1457334) with no luck.
thanks by the way! ill give it a shot and see if that helps!

---

### Post by tokarustsc on 2014-04-09
heres my aplay -l info
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


heres the arecord -l 

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC888 Alt Analog [ALC888 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CODEC [USB Audio CODEC], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by tokarustsc on 2014-04-09
at 48000 i get this error message with all settings set to default

 [COLOR=#999999]12:37:16.436 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]12:37:16.437 Statistics reset.[/COLOR]
 [COLOR=#cccc99]12:37:16.451 ALSA connection change.[/COLOR]
 [COLOR=#999999]12:38:06.514 D-BUS: Service not available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot read socket fd = 22 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 [COLOR=#66cc99]12:38:11.531 ALSA connection graph change.[/COLOR]
 (qjackctl:3301): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3301): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3301): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3301): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3301): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3301): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#999999]12:41:02.598 JACK is starting...[/COLOR]
 [COLOR=#990099]12:41:02.599 /usr/bin/jackd -r -dalsa -dhw:0 -r48000 -p256 -n3[/COLOR]
 Cannot read socket fd = 22 err = Success
 CheckRes error
 JackSocketClientChannel read fail
 Cannot open qjackctl client
 no message buffer overruns
 no message buffer overruns
 (qjackctl:3301): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:3301): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#999999]12:41:02.658 JACK was started with PID=3317.[/COLOR]
 no message buffer overruns
 `default' server already active
 Failed to open server
 jackdmp 1.9.10
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2013 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 [COLOR=#999999]12:41:02.686 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#ff0000]12:41:09.669 Could not connect to JACK server as client. - Overall operation failed. - Server communication error. Please check the messages window for more info.[/COLOR]
 Cannot open qjackctl client

---

### Post by jejeman on 2014-04-09
Try just to run in terminal
```
killall -9 jackd
/usr/bin/jackd -r -dalsa -dhw:1 -r48000 -p256 -n3
```

---

