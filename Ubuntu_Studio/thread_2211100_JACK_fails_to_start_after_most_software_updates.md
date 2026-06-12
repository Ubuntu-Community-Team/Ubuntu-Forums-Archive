---
title: "JACK fails to start after most software updates"
date: 2014-03-14
forum: Ubuntu Studio
---

### Post by weichiko on 2014-03-14
Hi,

I can normally get jack working fine from qjackctl or gladish. However, after most 'automatic' software updates then JACK fails to start. Also I use JACK2 because I found that is the only version of JACK that I can get gladish to work with. I have found that I can get JACK working again by going to synaptic package manager, installing jackd1, which automatically removes jackd2. I then reinstall jackd2 (again automatically removing jackd1) and restart the system. After doing all that JACK will then start.

Here are the error messages following a recent software update, after trying to start JACK from qjackctl:

--
D-BUS: JACK server could not be started.


Sorry
--


[COLOR=#999999]09:21:08.322 Patchbay deactivated.[/COLOR]
[COLOR=#999999]09:21:08.327 Statistics reset.[/COLOR]
[COLOR=#cccc99]09:21:08.410 ALSA connection change.[/COLOR]
[COLOR=#999999]09:21:08.454 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#66cc99]09:21:08.470 ALSA connection graph change.[/COLOR]
(qjackctl:2218): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2218): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
[COLOR=#ff0000]09:21:09.783 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
(qjackctl:2218): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2218): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
Fri Mar 14 09:21:09 2014: Starting jack server...
Fri Mar 14 09:21:09 2014: JACK server starting in realtime mode with priority 10
Fri Mar 14 09:21:09 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Fri Mar 14 09:21:09 2014: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Fri Mar 14 09:21:09 2014: ERROR: Audio device hw:0 cannot be acquired...
Fri Mar 14 09:21:09 2014: ERROR: Cannot initialize driver
Fri Mar 14 09:21:09 2014: ERROR: JackServer::Open failed with -1
Fri Mar 14 09:21:09 2014: ERROR: Failed to open server
Fri Mar 14 09:21:10 2014: Saving settings to "/home/***/.config/jack/conf.xml" ...
(qjackctl:2218): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
(qjackctl:2218): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
[COLOR=#ff0000]09:29:32.327 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started

---

Is there a better way to fix this, without having to keep uninstalling and reinstalling jackd2 after most software updates?

---

### Post by weichiko on 2014-03-14
Any tips for how to go about troubleshooting would also be greatly appreciated, e.g. files to save and compare etc. Thanks in advance.

---

### Post by jejeman on 2014-03-15
>  09:21:09.783 D-BUS: JACK server could not be started. SorryFirst, I would disable dbus service in Qjackctl.
> after most 'automatic' software What software? Knowing what exactly, could lead you to solution.
>  Fri Mar 14 09:21:09 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Fri Mar 14 09:21:09 2014: ERROR: Audio device hw:0 cannot be acquired...Find out why is this, who is taking over the audio card.

---

### Post by weichiko on 2014-03-15
> **jejeman said:**
> First, I would disable dbus service in Qjackctl.
Thanks. I will try that next time it happens.
> What software? Knowing what exactly, could lead you to solution.
I can't remember, that is something I need to take note of next time the system updates. I think every update where this has happened had some reference to "ubuntu studio base" or something like that. But I could be wrong about that, and I can't remember exactly what it was called.
> Find out why is this, who is taking over the audio card.
I was drawn to these lines myself, but I don't have the technical knowledge to find this information. Maybe over time as my knowledge increases, I will acquire the necessary knowledge to find out about this. In the mean time I would appreciate any tips about how I can go about troubleshooting this issue.

Also, I forgot to mention before, that the problem has just gone away by itself a couple of times, including not long after this last time it happened.

Thanks for your suggestions, I will look into your suggestions and see how it goes. Much appreciated.

---

### Post by weichiko on 2014-03-21
Well I seem to have fixed the problem. It just required clicking on the ">" button on the Settings tab of [COLOR=#000000]qjackctl setting, and selecting an option from there:

[/COLOR]Setup --- Settings --- Interface --- ">"  (Select PCM device name)
From here I chose the option hw:CMI8768,0

It all seems to be working fine again now.

---

### Post by Simon_Boyer on 2014-04-29
Hi,

I have the same problem.
It works if I disable D-bus, but can I use the low-latency kernel with this configuration ?

The only way to fix this is install jackd1, then re-install jackd2 and reboot, as explain in first post.

---

### Post by jejeman on 2014-04-29
> **Simon_Boyer said:**
> Hi,It works if I disable D-bus, but can I use the low-latency kernel with this configuration ?If you boot lowlatency kernel - then you are using it.
JACK D-bus is not important.

---

