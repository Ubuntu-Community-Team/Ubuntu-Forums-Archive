---
title: "Ubuntu 14.04 Server on Dell PowerEdge T110 II: Terminal server - no panels in any DE"
date: 2014-09-24
forum: Server Platforms
---

### Post by Bear_Ukraine on 2014-09-24
Colleagues, hello. Help pls. Have spent 3 days and still no result. 

What we have: 
Server Dell PowerEdge T110 II with Matrox video with 8MB of memory. For now this server has just power cord and network cable connected, ie no kb, mouse and monitor.

Server to be used for terminal access. 
At this point has already been installed: x2go and xrdp, xfce and lxde. 

What's the problem: 
When I connect to the server I can see just desktop with files\folders - there are no any panels. The same situation I see with x2go\xrdp and xfce\lxde. If I go through x2go, I can see that the top panel trying to start (blinking) and eventually disappears. 

Below attached the code from ~ / .xsession-errors when running xfce through xrdp
```
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256

** (process:6861): WARNING **: software acceleration check failed: Child process exited with code 1

** (x-session-manager:6861): CRITICAL **: We failed, but the fail whale is dead. Sorry....
Xsession: X session started for at &#1057;&#1088;&#1076; &#1057;&#1077;&#1085; 24 18:36:26 EEST 2014
X Error of failed request: BadValue (integer parameter out of range for operation)
 Major opcode of failed request: 109 (X_ChangeHosts)
 Value in failed request: 0x5
 Serial number of failed request: 6
 Current serial number in output stream: 8
localuser:antonio being added to access control list
X Error of failed request: BadValue (integer parameter out of range for operation)
 Major opcode of failed request: 109 (X_ChangeHosts)
 Value in failed request: 0x5
 Serial number of failed request: 6
 Current serial number in output stream: 8
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
xfce4-session-Message: ssh-agent is already running

(xfce4-session:7663): xfce4-session-WARNING **: Unable to launch "/usr/lib/tracker/tracker-miner-fs" (specified by autostart/tracker-miner-fs.desktop): Fai$

(polkit-gnome-authentication-agent-1:7727): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(polkit-gnome-authentication-agent-1:7727): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: Th$

(zeitgeist-datahub:7735): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(zeitgeist-datahub:7735): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

** (process:7778): WARNING **: killswitch.vala:103: Can't open /dev/rfkill for use as a killswitch backend: &#1054;&#1090;&#1082;&#1072;&#1079;&#1072;&#1085;&#1086; &#1074; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;

(xfce4-session:7663): xfce4-session-WARNING **: Unable to launch "/usr/lib/tracker/tracker-store" (specified by autostart/tracker-store.desktop): Failed to$

** (process:7778): CRITICAL **: bluez.vala:104: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 2 matched rules; type="method_c$
&#1053;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100;: &#1048;&#1085;&#1080;&#1094;&#1080;&#1072;&#1083;&#1080;&#1079;&#1072;&#1094;&#1080;&#1103; &#1084;&#1086;&#1076;&#1091;&#1083;&#1103; &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1072;&#1089;&#1100;

(process:7792): Indicator-Power-WARNING **: Fail to query backlight devices.

** (nm-applet:7782): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Rejected send message, 3 matched rules; type="method_call",$

** (xfce4-volumed:7809): WARNING **: Binding 'XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl>XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Alt>XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding '<Shift>XF86AudioRaiseVolume' failed!


** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl><Shift>XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl><Alt>XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding '<Alt><Shift>XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl><Shift><Alt>XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding 'XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Alt>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding '<Alt><Shift>XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl><Shift><Alt>XF86AudioRaiseVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding 'XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Alt>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding '<Shift>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl><Shift>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl><Alt>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding '<Alt><Shift>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Binding '<Ctrl><Shift><Alt>XF86AudioLowerVolume' failed!

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

** (xfce4-volumed:7809): WARNING **: Failed to map virtual modifiers

(xfwm4:7707): xfwm4-WARNING **: The display does not support the XRender extension.

(xfwm4:7707): xfwm4-WARNING **: The display does not support the XComposite extension.

(xfwm4:7707): xfwm4-WARNING **: The display does not support the XDamage extension.

(xfwm4:7707): xfwm4-WARNING **: The display does not support the XFixes extension.

(xfwm4:7707): xfwm4-WARNING **: Compositing manager disabled.

(xfsettingsd:7812): xfsettingsd-CRITICAL **: RANDR extension is too old, version 1.1. Display settings won't be applied.
Xlib: extension "XInputExtension" missing on display ":11.0".

(xfsettingsd:7812): xfsettingsd-CRITICAL **: XI is not present.

(xfsettingsd:7812): xfsettingsd-CRITICAL **: Failed to initialize the Xkb extension.

(xfsettingsd:7812): xfsettingsd-CRITICAL **: Failed to initialize the Accessibility extension.


(xfsettingsd:7812): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed

(xfwm4:7707): xfwm4-WARNING **: The display does not support the XRender extension.

(xfwm4:7707): xfwm4-WARNING **: The display does not support the XComposite extension.

(xfwm4:7707): xfwm4-WARNING **: The display does not support the XDamage extension.

(xfwm4:7707): xfwm4-WARNING **: The display does not support the XFixes extension.

(xfwm4:7707): xfwm4-WARNING **: Compositing manager disabled.

(xfsettingsd:7812): xfsettingsd-CRITICAL **: RANDR extension is too old, version 1.1. Display settings won't be applied.
Xlib: extension "XInputExtension" missing on display ":11.0".

(xfsettingsd:7812): xfsettingsd-CRITICAL **: XI is not present.

(xfsettingsd:7812): xfsettingsd-CRITICAL **: Failed to initialize the Xkb extension.

(xfsettingsd:7812): xfsettingsd-CRITICAL **: Failed to initialize the Accessibility extension.

(xfsettingsd:7812): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed

(xfwm4:7707): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed

(xfsettingsd:7812): xfsettingsd-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.

(xfwm4:7707): xfwm4-WARNING **: The property '/general/double_click_distance' of type int is not supported

** (process:7788): CRITICAL **: volume_control_set_volume_internal: assertion '_tmp1_ == PA_CONTEXT_READY' failed

** (process:7788): CRITICAL **: file /build/buildd/indicator-sound-12.10.2+14.04.20140401/obj-x86_64-linux-gnu/src/volume-control.c: line 1775: uncaught er$

(xfdesktop:7716): thunar-uca-WARNING **: Failed to load `/etc/xdg/Thunar/uca.xml': &#1054;&#1090;&#1082;&#1072;&#1079;&#1072;&#1085;&#1086; &#1074; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;
system-config-printer-applet: failed to start NewPrinterNotification service
system-config-printer-applet: failed to start PrinterDriversInstaller service: org.freedesktop.DBus.Error.AccessDenied: Connection ":1.83" is not allowed t$

(xfdesktop:7716): libxfce4util-CRITICAL **: Unable to open file /home/antonio/.config/xfce4/desktop/icons.screen0-1264x1008.rc.new.7716.tmp for writing: &#1054;&#1090;$

(xfdesktop:7716): libxfce4util-CRITICAL **: Unable to open file /home/antonio/.config/xfce4/desktop/icons.screen0-1264x1008.rc.new.7716.tmp for writing: &#1054;&#1090;$

(xfce4-panel:7711): GLib-GIO-CRITICAL **: g_file_new_for_path: assertion 'path != NULL' failed

(xfce4-panel:7711): liblauncher-CRITICAL **: launcher.c:517 (launcher_plugin_item_duplicate): expression 'G_IS_FILE (dst_file)' failed.

(wrapper-1.0:7937): Gdk-WARNING **: GdkWindow 0x2a00006 unexpectedly destroyed

(wrapper-1.0:7935): Gdk-WARNING **: GdkWindow 0x2e00006 unexpectedly destroyed
The program 'wrapper-1.0' received an X Window System error.
(xfwm4:7707): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed

(xfsettingsd:7812): xfsettingsd-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.

(xfwm4:7707): xfwm4-WARNING **: The property '/general/double_click_distance' of type int is not supported

** (process:7788): CRITICAL **: volume_control_set_volume_internal: assertion '_tmp1_ == PA_CONTEXT_READY' failed

** (process:7788): CRITICAL **: file /build/buildd/indicator-sound-12.10.2+14.04.20140401/obj-x86_64-linux-gnu/src/volume-control.c: line 1775: uncaught er$

(xfdesktop:7716): thunar-uca-WARNING **: Failed to load `/etc/xdg/Thunar/uca.xml': &#1054;&#1090;&#1082;&#1072;&#1079;&#1072;&#1085;&#1086; &#1074; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;
system-config-printer-applet: failed to start NewPrinterNotification service
system-config-printer-applet: failed to start PrinterDriversInstaller service: org.freedesktop.DBus.Error.AccessDenied: Connection ":1.83" is not allowed t$

(xfdesktop:7716): libxfce4util-CRITICAL **: Unable to open file /home/antonio/.config/xfce4/desktop/icons.screen0-1264x1008.rc.new.7716.tmp for writing: &#1054;&#1090;$

(xfdesktop:7716): libxfce4util-CRITICAL **: Unable to open file /home/antonio/.config/xfce4/desktop/icons.screen0-1264x1008.rc.new.7716.tmp for writing: &#1054;&#1090;$

(xfce4-panel:7711): GLib-GIO-CRITICAL **: g_file_new_for_path: assertion 'path != NULL' failed

(xfce4-panel:7711): liblauncher-CRITICAL **: launcher.c:517 (launcher_plugin_item_duplicate): expression 'G_IS_FILE (dst_file)' failed.

(wrapper-1.0:7937): Gdk-WARNING **: GdkWindow 0x2a00006 unexpectedly destroyed

(wrapper-1.0:7935): Gdk-WARNING **: GdkWindow 0x2e00006 unexpectedly destroyed
The program 'wrapper-1.0' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
 (Details: serial 225 error_code 3 request_code 2 minor_code 0)
 (Note to programmers: normally, X errors are reported asynchronously;
 that is, you will receive the error a while after causing it.
 To debug your program, run it with the --sync command line
 option to change this behavior. You can then get a meaningful
 backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'wrapper-1.0' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
 (Details: serial 180 error_code 3 request_code 18 minor_code 0)
 (Note to programmers: normally, X errors are reported asynchronously;
 that is, you will receive the error a while after causing it.
 To debug your program, run it with the --sync command line
 option to change this behavior. You can then get a meaningful
 backtrace from your debugger if you break on the gdk_x_error() function.)

(xfce4-panel:7941): GLib-GIO-CRITICAL **: g_file_new_for_path: assertion 'path != NULL' failed

(xfce4-panel:7941): liblauncher-CRITICAL **: launcher.c:517 (launcher_plugin_item_duplicate): expression 'G_IS_FILE (dst_file)' failed.

(wrapper-1.0:7949): Gdk-WARNING **: GdkWindow 0x2e00006 unexpectedly destroyed

(wrapper-1.0:7947): Gdk-WARNING **: GdkWindow 0x2a00006 unexpectedly destroyed
The program 'wrapper-1.0' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
 (Details: serial 182 error_code 3 request_code 18 minor_code 0)
 (Note to programmers: normally, X errors are reported asynchronously;
 that is, you will receive the error a while after causing it.
 To debug your program, run it with the --sync command line
 option to change this behavior. You can then get a meaningful
 backtrace from your debugger if you break on the gdk_x_error() function.)
```

From ~/.xsession-x2go-errors after trying to connect to lxde
```
XSession-x2go: X session started for antonio at &#1057;&#1088;&#1076; &#1057;&#1077;&#1085; 24 19:25:44 EEST 2014
localuser:antonio being added to access control list
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
xfce4-session-Message: ssh-agent is already running

(xfce4-session:15416): xfce4-session-WARNING **: Unable to launch "/usr/lib/tracker/tracker-miner-fs" (specified by autostart/tracker-miner-fs.deskto$

(xfwm4:15482): xfwm4-WARNING **: The display does not support the XComposite extension.

(xfwm4:15482): xfwm4-WARNING **: The display does not support the XFixes extension.

(xfwm4:15482): xfwm4-WARNING **: Compositing manager disabled.

(xfwm4:15482): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed

(xfce4-session:15416): xfce4-session-WARNING **: Unable to launch "/usr/lib/tracker/tracker-store" (specified by autostart/tracker-store.desktop): Fa$

** (process:15520): WARNING **: killswitch.vala:103: Can't open /dev/rfkill for use as a killswitch backend: &#1054;&#1090;&#1082;&#1072;&#1079;&#1072;&#1085;&#1086; &#1074; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;

(polkit-gnome-authentication-agent-1:15499): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(polkit-gnome-authentication-agent-1:15499): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnkn$

(zeitgeist-datahub:15509): GLib-GObject-WARNING **: invalid (NULL) pointer instance

** (process:15520): CRITICAL **: bluez.vala:104: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 2 matched rules; type="m$

(process:15580): Indicator-Power-WARNING **: Fail to query backlight devices.

(xfsettingsd:15585): xfsettingsd-CRITICAL **: Your XI is too old (1.3) version 1.4 is required.
system-config-printer-applet: failed to start NewPrinterNotification service
system-config-printer-applet: failed to start PrinterDriversInstaller service: org.freedesktop.DBus.Error.AccessDenied: Connection ":1.114" is not al$

(xfsettingsd:15585): GLib-CRITICAL **: g_str_has_prefix: assertion 'prefix != NULL' failed

** (nm-applet:15538): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Rejected send message, 3 matched rules; type="method$

(xfwm4:15482): xfwm4-WARNING **: The property '/general/double_click_distance' of type int is not supported

** (process:15555): CRITICAL **: volume_control_set_volume_internal: assertion '_tmp1_ == PA_CONTEXT_READY' failed

(xfsettingsd:15585): xfsettingsd-WARNING **: Failed to get the _NET_NUMBER_OF_DESKTOPS property.

** (nm-applet:15538): CRITICAL **: nm_secret_agent_register: assertion 'priv->registered == FALSE' failed

(xfdesktop:15491): thunar-uca-WARNING **: Failed to load `/etc/xdg/Thunar/uca.xml': &#1054;&#1090;&#1082;&#1072;&#1079;&#1072;&#1085;&#1086; &#1074; &#1076;&#1086;&#1089;&#1090;&#1091;&#1087;&#1077;

** (process:15555): CRITICAL **: file /build/buildd/indicator-sound-12.10.2+14.04.20140401/obj-x86_64-linux-gnu/src/volume-control.c: line 1775: unca$

(xfdesktop:15491): libxfce4util-CRITICAL **: Unable to open file /home/antonio/.config/xfce4/desktop/icons.screen0-784x584.rc.new.15491.tmp for writi$

(xfdesktop:15491): libxfce4util-CRITICAL **: Unable to open file /home/antonio/.config/xfce4/desktop/icons.screen0-784x584.rc.new.15491.tmp for writi$
xfce4-panel-migrate-Message: Requires the transfer of the panel settings...

(migrate:15591): GLib-CRITICAL **: g_hash_table_foreach: assertion 'hash_table != NULL' failed


(migrate:15591): GLib-CRITICAL **: g_hash_table_foreach: assertion 'hash_table != NULL' failed

(migrate:15591): GLib-CRITICAL **: g_hash_table_lookup: assertion 'hash_table != NULL' failed

(migrate:15591): GLib-CRITICAL **: g_hash_table_destroy: assertion 'hash_table != NULL' failed
xfce4-panel-migrate-Message: Configuration of panel updated.

(xfce4-panel:15486): libxfce4ui-WARNING **: ICE I/O Error

(xfce4-panel:15486): libxfce4ui-WARNING **: Disconnected from session manager.
```

~/.cache/lxsession/LXDE/run.log
```
** (process:20876): WARNING **: killswitch.vala:103: Can't open /dev/rfkill for use as a killswitch backend: Access denied

** (process:20876): CRITICAL **: bluez.vala:104: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 2 matched rules; type="m$

(process:20869): Indicator-Power-WARNING **: Fail to query backlight devices.

(polkit-gnome-authentication-agent-1:20857): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(polkit-gnome-authentication-agent-1:20857): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnkn$
Openbox-Message: Requested key "XF86Terminal" on the screen does not exist

(process:20869): Indicator-Power-WARNING **: Fail to query backlight devices.

(polkit-gnome-authentication-agent-1:20857): GLib-CRITICAL **: g_variant_new_string: assertion 'string != NULL' failed

(polkit-gnome-authentication-agent-1:20857): polkit-gnome-1-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnkn$
Openbox-Message: Requested key "XF86Terminal" on the screen does not exist

(zeitgeist-datahub:20867): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(zeitgeist-datahub:20867): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

** (nm-applet:20862): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Rejected send message, 3 matched rules; type="method$
** Message: x-terminal-emulator has very limited support, consider choose another terminal
** Message: x-terminal-emulator has very limited support, consider choose another terminal
nm-applet-Message: using fallback from indicator to GtkStatusIcon
** Message: settings.vala:482: Desktop file change, reloading XSettings daemon
** Message: options.vala:186: Reload xsettings_manager build-in
** Message: utils.vala:68: User config used : /home/antonio/.config/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /home/antonio/.config/lxsession/LXDE/desktop.conf
** Message: settings.vala:476: Reload the xsettings option
** Message: settings.vala:482: Desktop file change, reloading XSettings daemon
** Message: options.vala:186: Reload xsettings_manager build-in
** Message: utils.vala:68: User config used : /home/antonio/.config/lxsession/LXDE/desktop.conf
** Message: utils.vala:89: Final file used : /home/antonio/.config/lxsession/LXDE/desktop.conf
** Message: settings.vala:476: Reload the xsettings option
```

Today I was lucky 1 time when I saw fully loaded lxde. Then I tried to log-out and make a new session - again without panel.

---

### Post by Bear_Ukraine on 2014-09-25
The problem is fixed. 
Short summarise: Or add a new user or if there is no need to add new users, then just ->
1. Remove everything from ~/ directory (I didnt have anything I need to save, so I cleaned up my folder fully).
2. Via x2go client reconnect to the server.

Ubuntu simply creates new file\folders for the logged-in user (in our case default one). 

No errors, everything is ok.
It seems to be, that during initial installation when I plugged monitor, something was written to config files that interferes to work via terminal session as it should work.
Thats all.
Thanks a lot)

---

