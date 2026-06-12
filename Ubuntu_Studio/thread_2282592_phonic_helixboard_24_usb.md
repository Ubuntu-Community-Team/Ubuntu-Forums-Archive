---
title: "phonic helixboard 24 usb"
date: 2015-06-15
forum: Ubuntu Studio
---

### Post by dave185 on 2015-06-15
hey guys!

i'm a linux noob an new to ubuntu studio. 
the last couple of years i was using mac osX and logic8 for my recordings.
now it's time to try something new!

the problem is:
i've plugged my phonic helix board 24U via USB into my laptop but JACK is not willing to start.

here's the output:

 [COLOR=#999999]17:07:50.146 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]17:07:50.164 Statistics reset.[/COLOR]
 [COLOR=#cccc99]17:07:50.224 ALSA connection change.[/COLOR]
 [COLOR=#999999]17:07:50.605 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 [COLOR=#66cc99]17:07:50.611 ALSA connection graph change.[/COLOR]
 (qjackctl:2493): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:2493): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]17:08:20.441 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl:2493): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:2493): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 Mon Jun 15 17:08:20 2015: Starting jack server...
 Mon Jun 15 17:08:20 2015: JACK server starting in non-realtime mode
 Mon Jun 15 17:08:20 2015: Acquired audio card Audio1
 Mon Jun 15 17:08:20 2015: creating alsa driver ... hw:H24U|hw:H24U|16|2|22050|0|0|nomon|swmeter|-|32bit
 Mon Jun 15 17:08:20 2015: ERROR: ALSA: Cannot open PCM device alsa_pcm for playback. Falling back to capture-only mode
 Mon Jun 15 17:08:20 2015: ERROR: Cannot initialize driver
 Mon Jun 15 17:08:20 2015: ERROR: JackServer::Open failed with -1
 Mon Jun 15 17:08:20 2015: ERROR: Failed to open server
 Mon Jun 15 17:08:22 2015: Saving settings to "/home/dave/.config/jack/conf.xml" ...
 [COLOR=#ff0000]17:08:29.402 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl:2493): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:2493): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:2493): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:2493): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed


i know that there is a way to get the helix board working via firewire with ffado but i only have a usb bus. 
do you guys think there is hope for me?

---

### Post by Bucky Ball on 2015-06-15
Welcome. Firstly, with your USB audio device plugged in, open a terminal and type:

```
lsusb
```

Hit enter. Do you see your audio device there in the output? If so, good start.

Secondly, have you tweaked Jack in any way or are you using the bog standard Jack that comes default in Ubuntu Studio? You haven't changed any config files or tweaked with the code?

PS: Which release of UStudio are you using? 14.04, for instance?

---

### Post by dave185 on 2015-06-15
hi Bucky Ball! thnx for the quick response!

yes, i'm using 14.04

lsusb doesn't recognize the helix board but dmesg does...

the only thing i did was switching the "Interface" in the JACK setup menu to the helix board (hw:H24U)

---

