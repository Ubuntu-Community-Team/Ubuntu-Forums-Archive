---
title: "No desktop environment can be loaded with my onboard Intel  865G."
date: 2012-09-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ymcatar on 2012-09-10
I was trying to update my 12.04.1 to 12.10 and find out that no desktop environment can be loaded at all, as only unity 3d is included in 12.10.  I was only able to use the gnome-fallback session (not even gnome3 works) then, selecting other desktop environment will only get me to a blank screen with only the wallpaper and the cursor. After that I was back to 12.04.1 in which I can at least use the unity 2d session.

My Graphic Configuration:  Intel® 865G x86/MMX/SSE2 (I know it does not have the ability to run unity 3d but I know that llvmpipe can render it with software rendering instead, so at least I will be able to use either gnome 3 or unity 3d interface). I have taste the power of llvmpipe with fedora 17 and gnome 3 can be run on my rather old computer without any problem.

So, may I ask if there is something I'm missing, or Ubuntu 12.10 has poor support with 865G?
It will be quite a problem because when I use a liveUSB, I can never start getting unity 3d as I am stuck in a blank screen, and cannot fallback to unity 2d ... :(

Thanks! :D

---

### Post by dino99 on 2012-09-10
you can watch the logs to know about possible usefull warnings/errors logged (.xsession-errors & /var/log/)

if you have an xorg.conf you should remove it as the actual kernel directly deal with X.

---

### Post by steeldriver on 2012-09-10
You could maybe try booting the liveCD with ' i915.modeset=0' which should force it to fall back to the VESA driver - at least until you can get llvmpipe installed

---

### Post by ymcatar on 2012-09-10
Thanks for the quick responses!
I will now boot into the liveUSB and extract the log out.

---

### Post by ymcatar on 2012-09-11
Well, I found out that gnome3 has blacklisted my 865G in their default setting,and it apperars to me that it might relate to this problem.

I try commenting a line in Fedora 17 (/usr/share/gnome-session/hardware-requirement) and gnome 3 session works like a charm! As Fedora and Ubuntu are both now using llvmpipe to render their desktop on older hardware, I will install 12.10 again on my machine and report if this workground is working for me.

---

### Post by dino99 on 2012-09-11
> **ymcatar said:**
> Well, I found out that gnome3 has blacklisted my 865G in their default setting,and it apperars to me that it might relate to this problem.

I try commenting a line in Fedora 17 (/usr/share/gnome-session/hardware-requirement) and gnome 3 session works like a charm! As Fedora and Ubuntu are both now using llvmpipe to render their desktop on older hardware, I will install 12.10 again on my machine and report if this workground is working for me.

Good catch, maybe you could report that issue :

 ubuntu-bug xserver-xorg-video-intel

---

### Post by ymcatar on 2012-09-11
> **dino99 said:**
> Good catch, maybe you could report that issue :

 ubuntu-bug xserver-xorg-video-intel
After doing so, at least gnome-shell is working, therefore I can attrach my log recording the unity failure:

```
org.gtk.vfs.MountTracker.listMountableInfo call failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gtk.vfs.MountTracker' on object at path /org/gtk/vfs/mounttracker (g-dbus-error-quark, 19)
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/ymcatar/.compiz/session/10adc696ee574db612134736362087841700000026110032"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
** Message: applet now removed from the notification area
compiz (core) - Info: Starting plugin: unityshell
** Message: using fallback from indicator to GtkStatusIcon
compiz (unityshell) - Error: OpenGL 1.4+ not supported

compiz (unityshell) - Error: GL_ARB_fragment_program not supported

compiz (core) - Error: Plugin initScreen failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x1200003
  Serial number of failed request:  7716
  Current serial number in output stream:  7717
gnome-session[2611]: WARNING: App 'compiz.desktop' respawning too quickly
gnome-session[2611]: CRITICAL: We failed, but the fail whale is dead. Sorry....
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/ymcatar/.compiz/session/10adc696ee574db612134736362087841700000026110032"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

[COLOR="Red"]compiz (unityshell) - Error: OpenGL 1.4+ not supported

compiz (unityshell) - Error: GL_ARB_fragment_program not supported[/COLOR]

compiz (core) - Error: Plugin initScreen failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Value in failed request:  0x1ffffff
  Serial number of failed request:  7811
  Current serial number in output stream:  7817
gnome-session[2611]: WARNING: App 'compiz.desktop' respawning too quickly
gnome-session[2611]: WARNING: App 'compiz.desktop' respawning too quickly

** (nautilus:2703): WARNING **: Error calling current_status: Method "current_status" with signature "" on interface "com.ubuntuone.SyncDaemon.Status" doesn't exist


** (nautilus:2703): CRITICAL **: syncdaemon_status_info_get_online: assertion `SYNCDAEMON_IS_STATUS_INFO (sinfo)' failed

(gnome-settings-daemon:2668): Gdk-WARNING **: gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(polkit-gnome-authentication-agent-1:2709): Gdk-WARNING **: polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(bluetooth-applet:2701): Gdk-WARNING **: bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(gnome-fallback-mount-helper:2706): Gdk-WARNING **: gnome-fallback-mount-helper: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(telepathy-indicator:2782): Gdk-WARNING **: telepathy-indicator: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nm-applet:2707): Gdk-WARNING **: nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(update-notifier:2886): Gdk-WARNING **: update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


(nautilus:2703): Gdk-WARNING **: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.


** (zeitgeist-datahub:2799): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Xsession: X session started for root at Tue Sep 11 19:41:32 HKT 2012
localuser:root being added to access control list
Setting IM through im-switch for locale=en_HK.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/root/.cache/keyring-hKBGW8
GNOME_KEYRING_PID=3019
GNOME_KEYRING_CONTROL=/root/.cache/keyring-hKBGW8
GNOME_KEYRING_CONTROL=/root/.cache/keyring-hKBGW8
SSH_AUTH_SOCK=/root/.cache/keyring-hKBGW8/ssh
GNOME_KEYRING_CONTROL=/root/.cache/keyring-hKBGW8
SSH_AUTH_SOCK=/root/.cache/keyring-hKBGW8/ssh
GPG_AGENT_INFO=/root/.cache/keyring-hKBGW8/gpg:0:1
org.gtk.vfs.MountTracker.listMountableInfo call failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gtk.vfs.MountTracker' on object at path /org/gtk/vfs/mounttracker (g-dbus-error-quark, 19)
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
Home directory /home/ymcatar not ours.

** (gnome-settings-daemon:3016): WARNING **: Failed to connect context: OK
Home directory /home/ymcatar not ours.
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
Home directory /home/ymcatar not ours.
Connection failure: Connection refused
pa_context_connect() failed: Connection refused

** (gnome-user-share:3102): WARNING **: gnome-user-share cannot be started as root for security reasons.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1327 requests (1327 known processed) with 0 events remaining.
compizconfig - Info: Backend     : ini
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
Xsession: X session started for root at Tue Sep 11 19:43:02 HKT 2012
localuser:root being added to access control list
Setting IM through im-switch for locale=en_HK.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/root/.cache/keyring-Z1jBO8
GNOME_KEYRING_PID=3224
GNOME_KEYRING_CONTROL=/root/.cache/keyring-Z1jBO8
GNOME_KEYRING_CONTROL=/root/.cache/keyring-Z1jBO8
SSH_AUTH_SOCK=/root/.cache/keyring-Z1jBO8/ssh
GNOME_KEYRING_CONTROL=/root/.cache/keyring-Z1jBO8
SSH_AUTH_SOCK=/root/.cache/keyring-Z1jBO8/ssh
GPG_AGENT_INFO=/root/.cache/keyring-Z1jBO8/gpg:0:1
org.gtk.vfs.MountTracker.listMountableInfo call failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `org.gtk.vfs.MountTracker' on object at path /org/gtk/vfs/mounttracker (g-dbus-error-quark, 19)
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
Home directory /home/ymcatar not ours.

** (gnome-settings-daemon:3221): WARNING **: Failed to connect context: OK
Home directory /home/ymcatar not ours.
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
compiz (core) - Info: Stopping plugin: ccp
compiz (core) - Info: Unloading plugin: ccp
compiz (core) - Info: Stopping plugin: core
compiz (core) - Info: Unloading plugin: core
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 1403 requests (1403 known processed) with 6 events remaining.
compizconfig - Info: Backend     : ini
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : default
```

It seems like that I am rejected by Unity 3D because my onboard Intel  865G does not meet some of the requirement. But shouldn't this be ignored because we are supposed to cope with this old hardware problems with llvmpipe? If it is not working on older devices, why do they delete Unity 2D? ;)

---

