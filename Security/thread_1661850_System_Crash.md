---
title: "System Crash"
date: 2011-01-07
forum: Security
---

### Post by johnmay on 2011-01-07
My 10.04 system just crashed for 'no reason' . 

Looking through the system logs the rtkit daemon was started up a bout a minute before the crash. Is there a better place to see if my system has been compromised?  What should I look for? Any suggestions are helpful!

Thanks

---

### Post by cmoraes on 2011-01-07
It would help if you could describe what exactly happened when your system crashed, for e.g. did the UI become unresponsive, or did the system throw up some error screen, etc.

There is an .xsession-errors file in your home directory that may provide some indication.

---

### Post by bodhi.zazen on 2011-01-07
> **johnmay said:**
> My 10.04 system just crashed for 'no reason' . 

Looking through the system logs the rtkit daemon was started up a bout a minute before the crash. Is there a better place to see if my system has been compromised?  What should I look for? Any suggestions are helpful!

Thanks

Could be almost anything, this is not windows and I would not assume the cause is security related.

---

### Post by Rubi1200 on 2011-01-07
The name is perhaps a bit misleading, but nothing to be concerned about:
[rtkit]("http://manpages.ubuntu.com/manpages/lucid/man8/rtkitctl.8.html")

As cmoraes asked already, try and describe the events in more detail.

Posting the full specifications for the computer would also be helpful.

---

### Post by johnmay on 2011-01-07
System Specs: 

10.04 Lucid 
Kernel Linux 2.6.32-27-generic
GNOME 2.30.2 

#.8GB Memory Core i7 @2.93

Avail Disk Space 96.7 GB

Video lspci -v -s 02:00.0
02:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a1)
    Subsystem: eVga.com. Corp. Device c549
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at b1000000 (32-bit, non-prefetchable) [size=16M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at b0000000 (64-bit, non-prefetchable) [size=16M]
    I/O ports at 1000 [size=128]
    Expansion ROM at <ignored> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau  


.xsession-errors


```

Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/etc/X11/Xsession.d/98vboxadd-xclient: 29: /usr/bin/VBoxClient: not found
/etc/X11/Xsession.d/98vboxadd-xclient: 30: /usr/bin/VBoxClient: not found
/etc/X11/Xsession.d/98vboxadd-xclient: 31: /usr/bin/VBoxClient: not found
/etc/X11/Xsession.d/98vboxadd-xclient: 32: /usr/bin/VBoxClient: not found
GNOME_KEYRING_CONTROL=/tmp/keyring-xJMjKd
GNOME_KEYRING_CONTROL=/tmp/keyring-xJMjKd
GNOME_KEYRING_CONTROL=/tmp/keyring-xJMjKd
SSH_AUTH_SOCK=/tmp/keyring-xJMjKd/ssh

(polkit-gnome-authentication-agent-1:1829): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1829): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
07/01/2011 06:02:51 AM Autoprobing TCP port in (all) network interface
07/01/2011 06:02:51 AM Listening IPv{4,6}://*:5900
07/01/2011 06:02:51 AM Autoprobing selected port 5900
07/01/2011 06:02:51 AM Advertising security type: 'TLS' (18)
07/01/2011 06:02:51 AM Advertising authentication type: 'VNC Authentication' (2)
07/01/2011 06:02:51 AM Advertising security type: 'VNC Authentication' (2)
** (nm-applet:1845): DEBUG: old state indicates that this was not a disconnect 0
/usr/bin/compiz (core) - Fatal: Software rendering detected.
/usr/bin/compiz (core) - Error: Failed to manage screen: 0
/usr/bin/compiz (core) - Fatal: No manageable screens found on display :0.0

(gnome-power-manager:1822): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x23d85c0'
Unable to find a synaptics device.
** (nm-applet:1845): DEBUG: foo_client_state_changed_cb

(gnome-panel:1838): GConf-WARNING **: Directory `/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x229a300

(gnome-panel:1838): GConf-WARNING **: Directory `/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x229a300
Initializing nautilus-gdu extension

** (gnome-screensaver:1935): WARNING **: screensaver already running in this session
** (nm-applet:1845): DEBUG: foo_client_state_changed_cb
evolution-alarm-notify-Message: Setting timeout for 64598 1294473600 1294409002
evolution-alarm-notify-Message:  Sat Jan  8 00:00:00 2011

evolution-alarm-notify-Message:  Fri Jan  7 06:03:22 2011

** (update-notifier:2102): DEBUG: Skipping reboot required
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x1800003 (syslog - S); these messages lack timestamps and therefore suck.
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x1800003 (syslog - S); these messages lack timestamps and therefore suck.

(gnome-display-properties:2199): Gtk-WARNING **: Ignoring the separator setting

(gnome-display-properties:2199): Gtk-WARNING **: No object called: 
Window manager warning: Received a _NET_WM_MOVERESIZE message for 0x1800003 (syslog - S); these messages lack timestamps and therefore suck.
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead

(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Interrupted system call
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2163):invoke_NPP_NewStream: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1923):invoke_NPP_SetWindow: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))
*** NSPlugin Wrapper *** ERROR: NPObject 0x7f7d2a60d350 is no longer valid!
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()


```

---

### Post by bodhi.zazen on 2011-01-07
I am closing this thread as it is not security related.

Please start a new thread with a more appropriate title in general help.

When posting logs, either shorten them to the relevant line or lines [we do not need to see '(npviewer.bin:2679): Gdk-WARNING **: XID collision, trouble ahead' listed over and over ] or attach the log as a text file.

Thank you.

My guess is this is either a VNC problem or a problem with compiz, I can not tell. Try deactivating compiz.

Also you seem to be running in virtualbox ? If so, the guest does not use your hardware directly.

---

