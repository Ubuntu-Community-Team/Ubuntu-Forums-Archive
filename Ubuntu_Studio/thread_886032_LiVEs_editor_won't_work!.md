---
title: "LiVEs editor won't work!"
date: 2008-08-10
forum: Ubuntu Studio
---

### Post by higashi on 2008-08-10
I installed LiVEs video editor [i dont even remember what version it is and i can't really check anymore]. It used to open fine and i was able to cut and paste and do simple video editing, but the effects were missing [which is what i came to ask about in the first place] .. .  but, this time, when i tried opening it to mention what the pop-up would say, it didn't open at all. The terminal opened and said:

> 
LiVES 0.9.9.1
Copyright 2002-2008 Gabriel Finch (salsaman@xs4all.nl) and others.
LiVES comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.


(lives:19417): Gtk-CRITICAL **: gtk_bin_get_child: assertion `GTK_IS_BIN (bin)' failed

(lives:19417): Gtk-CRITICAL **: gtk_label_get_text: assertion `GTK_IS_LABEL (label)' failed

(lives:19417): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(lives:19417): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(lives:19417): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(lives:19417): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
all 32 bit float mono audio port buffers in use!
cannot assign buffer for port
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns



and i have a little pop-up window entitled "[LiVES]",, but it's blank.

Help?  :confused:

---

### Post by salsaman on 2008-08-26
The 0.9.9.1 builds on getdeb.net were broken for a while. This has now been fixed. Please try downloading and installing again, this should fix the problem.


Salsaman,
[http://lives.sourceforge.net](http://lives.sourceforge.net)

---

### Post by salsaman on 2008-08-26
Also, it seems that some other application is blocking your soundcard. You should find out what it is and shut it down before starting LiVES.

Alternately you can start LiVES with:

lives -aplayer sox -jackopts 0

to use the sox audio player in LiVES instead.


Salsaman.
[http://lives.sourceforge.net](http://lives.sourceforge.net)

---

