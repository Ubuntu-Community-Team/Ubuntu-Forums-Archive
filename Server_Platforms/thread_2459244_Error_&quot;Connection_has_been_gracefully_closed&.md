---
title: "Error &quot;Connection has been gracefully closed&quot; trying to vnc to Ubuntu v20.04"
date: 2021-03-14
forum: Server Platforms
---

### Post by wanman06212 on 2021-03-14
I am a Linux noobe who put up a Ubuntu Server v20.04 as a Plex Media Server.  

I want to be  able to TightVNC into my Ubuntu Server (from Windows 10) to perform  file management (via XCFE Desktop) and run process' from the console  that will continue to run even though I disconnect my putty connection.  I am in the process of moving 8TB of media files to specific locations on the Ubuntu server.  I feel this would be easier with the XCFE GUI rather than the commandline.  I have putty v.074 and xMing v6.9.0.31 Installed on my Windows  10 Desktop.  Whenever I attempt to connect from Windows 10 using Tightvnc, I get the error  "Connection has been gracefully closed".  I added some details below.  Any help is appreciated



I followed the process documented [here]("https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-20-04") to install VNCServer on the Ubuntu Server.

I installed VNCServer v1.3.10-0ubuntu5 using the process below.

```
sudo apt install xfce4 xfce4-goodies
sudo apt install tightvncserver
vncserver (to set the password)
vncserver -kill :1
mv ~/.vnc/xstartup ~/.vnc/xstartup.bak
cp ~/.vnc/xstartup.bak backups/xstartup.bak
nano ~/.vnc/xstartup (creates a new empty file)
****************I Pasted these lines into the xstartup file, saved and exited the nano editor
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
******************
chmod +x ~/.vnc/xstartup
vncserver -localhost
```

The problem I see is that I cant find the "$HOME/.Xresources" file anywhere in the /home folder.  I tried running "sudo vncserver -localhost" and "vncserver -localhost" but neither work.  What would I have to have in Xresources for this to work?  Also where does this file have to exist?  Under Root's home or my non-root user's home folder?

I opened a firewall port using UFW using this command (sudo ufw allow proto tcp to any port 5091 from 192.168.1.0/24).  The output to "sudo ufw status verbose" is shown below:

```
To                         Action      From
--                         ------      ----
137,138/udp (Samba)        ALLOW IN    192.168.1.0/24
139,445/tcp (Samba)        ALLOW IN    192.168.1.0/24
135/tcp                    ALLOW IN    192.168.1.0/24
5901/tcp                   ALLOW IN    192.168.1.0/24
```

/var/log/auth.log Errors when I run "vncserver -localhost"

```
Mar  7 18:12:00 servername polkitd(authority=local): Registered Authentication Agent for unix-session:12 (system bus name :1.185 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale C.UTF-8)
Mar  7 18:12:08 servername pkexec[11485]: username: Error executing command as another user: Not authorized [USER=root] [TTY=unknown] [CWD=/home/username/.vnc] [COMMAND=/usr/lib/update-notifier/package-system-locked]
Mar  7 18:12:22 servername sshd[5338]: error: connect_to 192.168.1.8 port 5901: failed.
Mar  7 18:12:26 servername dbus-daemon[1263]: [system] Failed to activate service 'org.bluez': timed out (service_start_timeout=25000ms)
```

~/.vnc/servername:1.log Errors when I run "vncserver -localhost"  - Appears to be permissions, but the permission are (-rwxrwxr-x 1 username groupname   46 Mar  7 17:53 xstartup)

```
username@servername:~/.vnc$ vncserver -localhost

New 'X' desktop is servername:1

Starting applications specified in /home/username/.vnc/xstartup
Log file is /home/username/.vnc/servername:1.log

username@servername:~/.vnc$ cat servername\:1.log
07/03/21 18:11:58 Xvnc version TightVNC-1.3.10
07/03/21 18:11:58 Copyright (C) 2000-2009 TightVNC Group
07/03/21 18:11:58 Copyright (C) 1999 AT&T Laboratories Cambridge
07/03/21 18:11:58 All Rights Reserved.
07/03/21 18:11:58 See http://www.tightvnc.com/ for information on TightVNC
07/03/21 18:11:58 Desktop name 'X' (servername:1)
07/03/21 18:11:58 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
07/03/21 18:11:58 Listening for VNC connections on TCP port 5901
Font directory '/usr/share/fonts/X11/75dpi/' not found - ignoring
Font directory '/usr/share/fonts/X11/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/username/.xstartup'
/usr/bin/startxfce4: X server already running on display :1
gpg-agent[11192]: WARNING: "--write-env-file" is an obsolete option - it has no effect
gpg-agent: a gpg-agent is already running - not starting a new one

(xfce4-session:11172): xfce4-session-WARNING **: 18:11:59.907: gpg-agent returned no PID in the variables

(xfce4-session:11172): xfce4-session-WARNING **: 18:11:59.912: xfsm_manager_load_session: Something wrong with /home/username/.cache/sessions/xfce4-session-servername:1, Does it exist? Permissions issue?

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.018: XSync extension too old (3.0).

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.018: The display does not support the XRender extension.

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.018: The display does not support the XRandr extension.

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.018: The display does not support the XComposite extension.

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.018: The display does not support the XDamage extension.

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.018: The display does not support the XFixes extension.

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.019: The display does not support the XPresent extension.

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.019: Compositing manager disabled.
xfwm4-Message: 18:12:00.066: Unsupported keyboard modifier '<Super>Tab'

(xfwm4:11194): xfwm4-WARNING **: 18:12:00.076: Cannot find visual format on screen 0

(xfsettingsd:11198): xfsettingsd-CRITICAL **: 18:12:00.128: No RANDR extension found in display :1. Display settings won't be applied.
Xlib:  extension "XInputExtension" missing on display ":1".

(xfsettingsd:11198): xfsettingsd-CRITICAL **: 18:12:00.128: XI is not present.

(xfsettingsd:11198): xfsettingsd-CRITICAL **: 18:12:00.128: Failed to initialize the Xkb extension.

(xfsettingsd:11198): xfsettingsd-CRITICAL **: 18:12:00.128: Failed to initialize the Accessibility extension.
xfwm4-Message: 18:12:00.224: Unsupported keyboard modifier '<Super>Tab'

** (xiccd:11232): CRITICAL **: 18:12:00.568: RandR extension is not working on display :1.0

(polkit-gnome-authentication-agent-1:11235): GLib-CRITICAL **: 18:12:00.662: g_variant_new_string: assertion 'string != NULL' failed

(polkit-gnome-authentication-agent-1:11235): polkit-gnome-1-WARNING **: 18:12:00.664: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (wrapper-2.0:11216): WARNING **: 18:12:00.681: No XRANDR extension found

** (wrapper-2.0:11215): WARNING **: 18:12:00.712: Binding 'XF86AudioLowerVolume' failed!

(wrapper-2.0:11215): pulseaudio-plugin-WARNING **: 18:12:00.712: Could not have grabbed volume control keys. Is another volume control application (xfce4-volumed) running?

** (wrapper-2.0:11215): WARNING **: 18:12:00.712: Binding 'XF86AudioPlay' failed!

(wrapper-2.0:11215): pulseaudio-plugin-WARNING **: 18:12:00.712: Could not have grabbed multimedia control keys.

(wrapper-2.0:11217): GLib-GIO-CRITICAL **: 18:12:00.758: g_file_new_for_path: assertion 'path != NULL' failed

(wrapper-2.0:11217): GLib-GIO-CRITICAL **: 18:12:00.758: g_file_monitor_file: assertion 'G_IS_FILE (file)' failed

(wrapper-2.0:11217): GLib-GObject-WARNING **: 18:12:00.758: invalid (NULL) pointer instance

(wrapper-2.0:11217): GLib-GObject-CRITICAL **: 18:12:00.758: g_signal_connect_data: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

(wrapper-2.0:11217): Gtk-WARNING **: 18:12:00.758: Attempting to add a widget with type GtkToggleButton to a container of type XfcePanelPlugin, but the widget is already inside a container of type XfcePanelPlugin, please remove the widget from its existing container first.
AUDIT: Sun Mar  7 18:12:00 2021: 11166 Xtightvnc: client 22 rejected from local host
Failure: Module initialization failed

** (light-locker:11271): ERROR **: 18:12:00.802: Environment variable XDG_SESSION_PATH not set. Is LightDM running?

(wrapper-2.0:11217): Gtk-WARNING **: 18:12:00.844: Negative content width -3 (allocation 1, extents 2x2) while allocating gadget (node button, owner GtkToggleButton)

(wrapper-2.0:11216): Gtk-WARNING **: 18:12:00.927: Negative content width -3 (allocation 1, extents 2x2) while allocating gadget (node button, owner PowerManagerButton)

(wrapper-2.0:11220): Gtk-WARNING **: 18:12:00.928: Negative content width -1 (allocation 1, extents 1x1) while allocating gadget (node button, owner XfceArrowButton)
blueman-applet 18.12.01 WARNING  PluginManager:147 __load_plugin: Not loading DhcpClient because its conflict has higher priority
blueman-tray version 2.1.2 starting
There is an instance already running
blueman-applet 18.12.01 WARNING  PluginManager:147 __load_plugin: Not loading PPPSupport because its conflict has higher priority
Error executing command as another user: Not authorized

This incident has been reported.
Xlib:  extension "DPMS" missing on display ":1.0".

(wrapper-2.0:11215): libnotify-WARNING **: 18:12:25.741: Failed to connect to proxy

(wrapper-2.0:11215): Gtk-WARNING **: 18:12:25.776: Negative content width -3 (allocation 1, extents 2x2) while allocating gadget (node button, owner PulseaudioButton)
blueman-applet 18.12.26 WARNING  DiscvManager:109 update_menuitems: warning: Adapter is None
```

---

### Post by QIII on 2021-03-14
If I might make a suggestion for re-thinking what you are trying to accomplish:

Linux servers are *very rarely* provisioned with a GUI interface like a DE.  When you log in to a server over SSH, you are already in the command line interface.  There is no need to add the potential security liability and extra CPU and memory sucking load of a DE.  It is a waste of your time to add a DE to use it only to open a terminal.

While Windows servers have graphical interfaces, Linux servers rarely do.

---

### Post by wanman06212 on 2021-03-14
QIII,

Thanks for your reply.

I understand and you are correct.  Let me explain further.

This is a Plex Media Server with 8TB of media located all over the  place.  I have two raid groups and 2 lvms setup with different mount  points for different types of media.  Moving data within a mount point  is quick, but from mount point to mount point or volume group to volume  group it takes much longer.  There are times where i have to transfer  400GB of  media files from one place on the drive to another.  And there  are times when I have to transfer 1 file totaling 2GB to another  location.  These files should've been placed properly to begin wit, but  its a mute point now.


This is a temporary solution to the problem of moving 8TB of data to my  server.  I understand that I can remove the firewall rule and disable  the VNCServer service when not in use and permanently when this process  is done.  

If there is a better solution than remoting  to the console and using the GUI, Im willing to hear it.  Or if you can  help me figure out the error that Im getting, that would be great.


Thanks

---

### Post by LHammonds on 2021-03-15
When it comes to moving large amounts of files, even on Windows, I resort to using the command line...mainly batch files so that I can log the results with verified reads/writes and have a handy-dandy report at the end of it all letting me know if everything was successfully copied or not.  Another point is that I "copy" files first, then verify, then delete from the source.

On Windows, I use robocopy.  On Linux, I use rsync.

Another benefit to using the command-line besides using scripts and logging results, you can start the script using "nohup" which means you run the script and it continues to process in the background even if you your session gets disconnected.  Having the results of the copy/sync being sent to a log means I can later reconnect and look at the end of the log to see if the process finished or if its still ongoing.

And once you have a script that can do all of this one time, you have this script for the next time and the time after that.

LHammonds

---

### Post by wanman06212 on 2021-03-15
LHammonds,

Thanks for your response.  I agree with everything you said.  I am a Windows guy who uses Robocopy and a Linux newbie who uses rsync.  However, for this specific file transfer that Im doing, I would like to use an XCFE file manager via VNC from my Windows 10 PC to my Ubuntu server.  Do you know how I can get the error I am getting ("Connection has been gracefully closed") resolved?  Does anything in the logs I posted jump out at you as a possible cause?

---

### Post by LHammonds on 2021-03-16
Sorry, I do not have experience with Linux desktop environments.  All my servers are managed via SSH only and none of them have a DE installed.

LHammonds

---

