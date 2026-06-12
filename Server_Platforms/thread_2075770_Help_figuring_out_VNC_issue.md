---
title: "Help figuring out VNC issue"
date: 2012-10-24
forum: Server Platforms
---

### Post by jnichols51 on 2012-10-24
I have setup two servers both running 12.04. The first one I believe I started at 12.04 and the second was an upgrade. The first one runs vnc4server just fine. (Sort of. Still trying to figure out how to run apps from desktop as root. But that's another story...) However when I run it on the second box I get a blank desktop with 3 checkboxs in the upper left. I know it is running something because I can right click and create folders and the like. But I don't get any menu system and when I try to change the desktop wallpaper it just stays the default.

I have been running SSH on this server for awhile. I just would like to be able to use GUI apps on my iPad. I am accessing the SSH from inside of a VPN. Everytime I have tried to run a GUI app from SSH it has been painfully slow at updating any part of the GUI. I am hoping VNC will fix that.

I have scoured the net and have run all of the tutorials I can find. They only point to making sure that "gnome-session --session=gnome-classic &" is added. I have done that as well as making it gnome-fallback but nothing seems to help. See my xstartup log:


Xvnc Free Edition 4.1.1 - built Feb  5 2012 20:06:55
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Wed Oct 24 11:25:11 2012
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
gnome-session[3746]: WARNING: GSIdleMonitor: IDLETIME counter not found
gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256
gnome-session[3746]: WARNING: Session 'gnome-classic' runnable check failed: Exited with code 1
gnome-session[3746]: WARNING: GsmSessionSave: Failed to create directory /home/jnichols/.config/gnome-session/saved-session: Permission denied
gnome-session[3746]: WARNING: GsmSessionSave: could not create directory for saved session: /home/jnichols/.config/gnome-session/saved-session
gnome-session[3746]: WARNING: Unable to find required component 'gnome-panel'
gnome-session[3746]: WARNING: GsmSessionSave: Failed to create directory /home/jnichols/.config/gnome-session/saved-session: Permission denied
gnome-session[3746]: WARNING: Unable to find required component 'gnome-settings-daemon'
gnome-session[3746]: WARNING: GsmSessionSave: Failed to create directory /home/jnichols/.config/gnome-session/saved-session: Permission denied
gnome-session[3746]: WARNING: Unable to find default provider 'metacity' of required provider 'windowmanager'
GNOME_KEYRING_CONTROL=/tmp/keyring-vrsMNh
SSH_AUTH_SOCK=/tmp/keyring-vrsMNh/ssh
GNOME_KEYRING_PID=3764
GNOME_KEYRING_CONTROL=/tmp/keyring-vrsMNh
SSH_AUTH_SOCK=/tmp/keyring-vrsMNh/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-vrsMNh
SSH_AUTH_SOCK=/tmp/keyring-vrsMNh/ssh
GPG_AGENT_INFO=/tmp/keyring-vrsMNh/gpg:0:1
GNOME_KEYRING_CONTROL=/tmp/keyring-vrsMNh
SSH_AUTH_SOCK=/tmp/keyring-vrsMNh/ssh
GPG_AGENT_INFO=/tmp/keyring-vrsMNh/gpg:0:1

(gnome-settings-daemon:3768: power-plugin-WARNING **: Unable to start power manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:3768: color-plugin-WARNING **: Unable to start color manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:3768: xrandr-plugin-WARNING **: Unable to start xrandr manager: RANDR extension is too old (must be at least 1.2)

(gnome-settings-daemon:3768: keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

(gnome-settings-daemon:3768: keyboard-plugin-WARNING **: XKB extension not available

(gnome-settings-daemon:3768: keyboard-plugin-WARNING **: Neither XKeyboard not Xfree86's keyboard extensions are available,
no way to support keyboard autorepeat rate settings

(gnome-settings-daemon:3768: keyboard-plugin-WARNING **: Failed to set the keyboard layouts: GDBus.Error:org.freedesktop.Accounts.Error.PermissionDenied: Not authorized

(bluetooth-applet:3788: Bluetooth-WARNING **: Could not open RFKILL control device, please verify your installation
Initializing nautilus-gdu extension

** (nm-applet:3787): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: applet now removed from the notification area

** (nm-applet:3787): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
** Message: using fallback from indicator to GtkStatusIcon

** (nautilus:3786): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:3786): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:3786): WARNING **: Can not get _NET_WORKAREA

** (nautilus:3786): WARNING **: Can not determine workarea, guessing at layout
** Message: Starting applet secret agent because GNOME Shell disappeared

** (nm-applet:3787): WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
Failure: Module initalization failed

(gdu-notification-daemon:3838: GduNotification-WARNING **: Error creating directory `/home/jnichols/.config/gnome-disk-utility/ata-smart-ignore': Permission denied
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1" 
      after 175 requests (175 known processed) with 0 events remaining. 
gnome-session[3746]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(gnome-settings-daemon:3768: Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(gnome-fallback-mount-helper:3784): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(polkit-gnome-authentication-agent-1:3785): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(notification-daemon:3790): Gdk-WARNING **: notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(nm-applet:3787): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(bluetooth-applet:3788: Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


(nautilus:3786): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.

g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.

(gdu-notification-daemon:3838: Gdk-WARNING **: gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.


To keep the log small I just started the server and killed it right away.

---

