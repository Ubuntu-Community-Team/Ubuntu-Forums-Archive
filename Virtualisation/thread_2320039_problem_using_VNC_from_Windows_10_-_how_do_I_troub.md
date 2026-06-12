---
title: "problem using VNC from Windows 10 - how do I troubleshoot and address please?"
date: 2016-04-09
forum: Virtualisation
---

### Post by Shahin_Ansari on 2016-04-09
I have a remote Ubuntu machine, which I decided to use VNC to connect to. I followed the  [http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html](http://www.havetheknowhow.com/Configure-the-server/Install-VNC.html) instructions. The Ubuntu machine is a VM with just a root account at the moment, and I *think* my problem is that I need to create a user account. Here is what I have:
- When I started the VNC server for the first time I got the error:
```
xauth:  file /root/.Xauthority does not exist

```
- VNC log file has the following messages:

```
Sat Apr  9 22:01:03 2016
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
Window manager warning: Log level 32: could not find XKB extension.
    
(gnome-settings-daemon:20161): power-plugin-WARNING **: Unable to start gsd_power manager:RANDR extension is too old (must be at least 1.2)
    
 (gnome-settings-daemon:20161): xrandr-plugin-WARNING **: Unable to start gsd_xrandr manager: RANDR extension is too old (must be at least 1.2)
    
(gnome-settings-daemon:20161): color-plugin-WARNING **: Unable to start gsd_color manager:RANDR extension is too old (must be at least 1.2)
    
(gnome-settings-daemon:20161): cursor-plugin-WARNING **: Unable to start gsd_cursor manager: XFixes cursor extension not available
    
** (gnome-settings-daemon:20161): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
    
** (process:20211): WARNING **: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```

I did check my Windows 10 firewalls settings, and the IP address of the VM is not being blocked. I am not sure what else to look into.

---

### Post by MAFoElffen on 2016-04-10
root account has no user directory in /home, so cannot have an .Xauthority file... so cannot start an X session with root. You need an user account for an X session.

---

