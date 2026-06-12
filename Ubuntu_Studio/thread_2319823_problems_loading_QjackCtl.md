---
title: "problems loading QjackCtl"
date: 2016-04-07
forum: Ubuntu Studio
---

### Post by guitarlayton on 2016-04-07
When I try to configure QJackCtl I get with following message. using Ubuntu Studio 14.04 32 bit on a Dell Inspiron 9400 laptop

 [COLOR=#999999]14:50:25.796 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]14:50:25.836 Statistics reset.[/COLOR]
 [COLOR=#cccc99]14:50:26.264 ALSA connection change.[/COLOR]
 [COLOR=#999999]14:50:26.477 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 [COLOR=#66cc99]14:50:26.543 ALSA connection graph change.[/COLOR]
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#999999]14:50:58.839 Statistics reset.[/COLOR]
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 [COLOR=#ff0000]15:01:58.191 D-BUS: JACK server could not be started. Sorry[/COLOR]
 Thu Apr  7 15:01:56 2016: Starting jack server...
 Thu Apr  7 15:01:57 2016: JACK server starting in realtime mode with priority 10
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Thu Apr  7 15:01:58 2016: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Thu Apr  7 15:01:58 2016: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
 Thu Apr  7 15:01:58 2016: ERROR: Audio device hw:0 cannot be acquired...
 Thu Apr  7 15:01:58 2016: ERROR: Cannot initialize driver
 Thu Apr  7 15:01:58 2016: ERROR: JackServer::Open failed with -1
 Thu Apr  7 15:01:58 2016: ERROR: Failed to open server
 Thu Apr  7 15:01:58 2016: Saving settings to "/home/guitarlayton/.config/jack/conf.xml" ...
 [COLOR=#ff0000]15:02:14.967 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed
 (qjackctl:22370): Gtk-CRITICAL **: IA__gtk_widget_get_direction: assertion 'GTK_IS_WIDGET (widget)' failed

can anyone help me out here?

---

