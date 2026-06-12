---
title: "Lightdm &amp; Desktop"
date: 2013-10-23
forum: Ubuntu Development Version
---

### Post by tad1073 on 2013-10-23
Lightdm takes a long time to load to be able to login and the Desktop also takes a long time to load, anyone else experiencing this? See sig. for specs.

---

### Post by deadflowr on 2013-10-23
Please define "Long Time".
10 seconds?
2 minutes?
2 hours?
A week?

It helps to know the ballpark area of what you consider long time.

---

### Post by tad1073 on 2013-10-23
> **deadflowr said:**
> Please define "Long Time".
10 seconds?
2 minutes?
2 hours?
A week?

It helps to know the ballpark area of what you consider long time.

idk...probably 30 to 45 seconds for each

---

### Post by deadflowr on 2013-10-24
You might try looking at the applications being launched during startup
Looky here how to easily display them in the startup applications

[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

---

### Post by tad1073 on 2013-10-24
> **deadflowr said:**
> You might try looking at the applications being launched during startup
Looky here how to easily display them in the startup applications

[https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications)

I don't think the startup applications have anything to do with my problem.

---

### Post by tad1073 on 2013-10-25
Bump

---

### Post by Toz on 2013-10-25
What do the log files **/var/log/lightdm/lightdm.log** and **/var/log/lightdm/x-0-greeter.log** say? 

Note: You'll need root privileges to access those files. You can use, from a terminal:
```
sudo -i gedit /var/log/lightdm/lightdm.log
```
...and:
```
sudo -i gedit /var/log/lightdm/x-0-greeter.log
```

---

### Post by tad1073 on 2013-10-25
> **Toz said:**
> What do the log files **/var/log/lightdm/lightdm.log** and **/var/log/lightdm/x-0-greeter.log** say? 

Note: You'll need root privileges to access those files. You can use, from a terminal:
```
sudo -i gedit /var/log/lightdm/lightdm.log
```

```

[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.9.0, UID=0 PID=1549
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-ubuntu.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Registered seat module unity
[+0.00s] DEBUG: Registered seat module surfaceflinger
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Seat: Starting
[+0.00s] DEBUG: Seat: Creating greeter session
[+0.00s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+0.00s] DEBUG: Seat: Creating display server of type x
[+0.00s] DEBUG: Seat: Starting local X display
[+0.00s] DEBUG: Using VT 7
[+0.00s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+0.00s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+0.01s] DEBUG: DisplayServer x-0: Launching X Server
[+0.01s] DEBUG: Launching process 1558: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+0.01s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+1.00s] DEBUG: Got signal 10 from process 1558
[+1.00s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+1.00s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+1.00s] DEBUG: Seat: Display server ready, starting session authentication
[+1.00s] DEBUG: Session: Setting XDG_VTNR=7
[+1.00s] DEBUG: Session pid=1566: Started with service 'lightdm-greeter', username 'lightdm'
[+1.05s] DEBUG: Session pid=1566: Authentication complete with return value 0: Success
[+1.05s] DEBUG: Seat: Session authenticated, running command
[+1.05s] DEBUG: Session pid=1566: Setting XDG_VTNR=7
[+1.05s] DEBUG: Session pid=1566: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+1.06s] DEBUG: Session pid=1566: Logging to /var/log/lightdm/x-0-greeter.log
[+1.08s] DEBUG: Activating VT 7
[+1.26s] DEBUG: Session pid=1566: Greeter connected version=1.9.0
[+1.42s] DEBUG: Session pid=1566: Greeter start authentication for thomas
[+1.42s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+1.42s] DEBUG: Session: Setting XDG_VTNR=7
[+1.42s] DEBUG: Session pid=1643: Started with service 'lightdm', username 'thomas'
[+1.42s] DEBUG: Session pid=1566: Greeter start authentication for thomas
[+1.42s] DEBUG: Session pid=1643: Sending SIGTERM
[+1.42s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+1.42s] DEBUG: Session: Setting XDG_VTNR=7
[+1.42s] DEBUG: Session pid=1646: Started with service 'lightdm', username 'thomas'
[+1.42s] DEBUG: Session pid=1643: Terminated with signal 15
[+1.42s] DEBUG: Session: Failed during authentication
[+1.42s] DEBUG: Seat: Session stopped
[+1.43s] DEBUG: Session pid=1646: Got 1 message(s) from PAM
[+1.43s] DEBUG: Session pid=1566: Prompt greeter with 1 message(s)
[+35.08s] DEBUG: Session pid=1566: Continue authentication
[+35.11s] DEBUG: Session pid=1646: Authentication complete with return value 0: Success
[+35.11s] DEBUG: Session pid=1566: Authenticate result for user thomas: Success
[+35.12s] DEBUG: Session pid=1566: User thomas authorized
[+35.23s] DEBUG: Session pid=1566: Greeter requests session ubuntu
[+35.26s] DEBUG: Writing /home/thomas/.dmrc
[+35.27s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+35.27s] DEBUG: Session pid=1566: Sending SIGTERM
[+35.27s] DEBUG: Session pid=1566: Exited with return value 0
[+35.27s] DEBUG: Seat: Session stopped
[+35.27s] DEBUG: Seat: Greeter stopped, running session
[+35.27s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+35.28s] DEBUG: Session pid=1646: Setting XDG_VTNR=7
[+35.28s] DEBUG: Session pid=1646: Running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+35.28s] DEBUG: Session pid=1646: Logging to .xsession-errors
[+35.30s] DEBUG: Activating VT 7

```
...and:
```
sudo -i gedit /var/log/lightdm/x-0-greeter.log
```

```

Activating service name='org.a11y.atspi.Registry'
Successfully activated service 'org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:435: Starting unity-greeter 13.10.3 UID=111 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:438: Setting cursor

** (at-spi2-registryd:1602): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (at-spi2-registryd:1602): WARNING **: Unable to register client with session manager
[+0.01s] DEBUG: unity-greeter.vala:452: Loading command line options
[+0.01s] DEBUG: unity-greeter.vala:480: Setting GTK+ settings
[+0.07s] DEBUG: unity-greeter.vala:503: Creating Unity Greeter
[+0.07s] DEBUG: unity-greeter.vala:55: Creating background surface
[+0.07s] DEBUG: Connecting to display manager...
[+0.07s] DEBUG: Wrote 17 bytes to daemon
[+0.07s] DEBUG: Read 8 bytes from daemon
[+0.07s] DEBUG: Read 149 bytes from daemon
[+0.07s] DEBUG: Connected version=1.9.0 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true show-remote-login=true
[+0.11s] DEBUG: menubar.vala:332: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.13s] WARNING: File '/usr/lib/indicators3/7/libcom.canonical.indicator.keyboard.so' does not exist.
[+0.13s] WARNING: File '/usr/lib/indicators3/7/com.canonical.indicator.keyboard.so' does not exist.
[+0.13s] WARNING: File '/usr/lib/indicators3/7/com.canonical.indicator.keyboard' does not exist.
[+0.13s] DEBUG: menubar.vala:364: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.14s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.14s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.16s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.16s] DEBUG: user-list.vala:988: Adding/updating user thomas (Thomas)
[+0.16s] DEBUG: user-list.vala:970: Adding guest account entry
[+0.23s] WARNING: Failed to open configuration file: No such file or directory
[+0.23s] WARNING: Failed to open sessions directory: Error opening directory '/usr/share/lightdm/sessions': No such file or directory
[+0.23s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.23s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.23s] DEBUG: Loaded session /usr/share/lightdm/remote-sessions/freerdp.desktop (FreeRDP, Full Screen RDP session)
[+0.23s] DEBUG: Loaded session /usr/share/lightdm/remote-sessions/uccsconfigure.desktop (UCCS Configure, Setup a UCCS Account)
[+0.23s] DEBUG: Starting authentication for user thomas...
[+0.23s] DEBUG: Wrote 22 bytes to daemon
[+0.23s] DEBUG: Starting authentication for user thomas...
[+0.23s] DEBUG: Wrote 22 bytes to daemon
[+0.24s] DEBUG: main-window.vala:181: Screen is 3840x1080 pixels
[+0.24s] DEBUG: main-window.vala:187: Monitor 0 is 1920x1080 pixels at 0,0
[+0.24s] DEBUG: main-window.vala:187: Monitor 1 is 1920x1080 pixels at 1920,0
[+0.24s] DEBUG: unity-greeter.vala:506: Showing greeter
[+0.24s] DEBUG: unity-greeter.vala:194: Showing main window
[+0.24s] DEBUG: background.vala:470: Regenerating backgrounds
[+0.24s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1920x1080
[+0.25s] DEBUG: unity-greeter.vala:524: Starting main loop
[+0.25s] DEBUG: Read 8 bytes from daemon
[+0.25s] DEBUG: Read 36 bytes from daemon
[+0.25s] DEBUG: Prompt user with 1 message(s)
[+0.29s] DEBUG: background.vala:68: Making background /home/thomas/Pictures/Wallpapers/Dock-Street-Market_www.FullHDWpp.com_ (another copy).jpg at 1920x1080
[+0.30s] DEBUG: background.vala:155: Error loading background: Failed to open file '/home/thomas/Pictures/Wallpapers/Dock-Street-Market_www.FullHDWpp.com_ (another copy).jpg': Permission denied
[+0.37s] DEBUG: menubar.vala:534: Adding indicator object 0xaa4558 at position 0
[+0.37s] DEBUG: unity-greeter.vala:177: starting system-ready sound
** Message: applet now removed from the notification area

** (gnome-settings-daemon:1622): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gnome-settings-daemon:1622): power-plugin-WARNING **: Failed to run GetActive() function on screensaver: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface 'org.gnome.ScreenSaver' on object at path /org/gnome/ScreenSaver
** Message: using fallback from indicator to GtkStatusIcon
[+21.71s] DEBUG: background.vala:117: Render of background /home/thomas/Pictures/Wallpapers/Dock-Street-Market_www.FullHDWpp.com_ (another copy).jpg complete
[+21.71s] DEBUG: background.vala:134: images[0] was null for /home/thomas/Pictures/Wallpapers/Dock-Street-Market_www.FullHDWpp.com_ (another copy).jpg
[+21.71s] DEBUG: menubar.vala:534: Adding indicator object 0xaa46b8 at position 1
[+21.72s] DEBUG: user-list.vala:254: removing manual login since we have a remote login entry
[+21.83s] DEBUG: menubar.vala:534: Adding indicator object 0xaa4978 at position 2
[+21.83s] DEBUG: background.vala:117: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+21.84s] DEBUG: Restarting service 'com.canonical.indicator.application' count 1
** Message: moving back from GtkStatusIcon to indicator
[+21.97s] DEBUG: Connected to Application Indicator Service.
[+21.97s] DEBUG: Request current apps
[+21.97s] DEBUG: Building new application entry: :1.14  with icon: nm-device-wired at position 0
[+21.97s] DEBUG: menubar.vala:534: Adding indicator object 0xb2c4b0 at position 3
[+33.89s] DEBUG: Providing response to display manager
[+33.89s] DEBUG: Wrote 31 bytes to daemon
[+33.94s] DEBUG: Read 8 bytes from daemon
[+33.94s] DEBUG: Read 18 bytes from daemon
[+33.94s] DEBUG: Authentication complete for user thomas with return code 0
[+34.05s] DEBUG: Starting session ubuntu
[+34.05s] DEBUG: Wrote 18 bytes to daemon

** (gnome-settings-daemon:1622): WARNING **: Name taken or bus went away - shutting down

(gnome-settings-daemon:1622): dconf-WARNING **: failed to commit changes to dconf: The connection is closed

```

---

### Post by Toz on 2013-10-25
I see you're running Ubuntu 14.04. Moving to the **Ubuntu+1** forum.

Since this is a very early version of 14.04, I think you should expect these sorts of issues. From looking at the x-0-greeter.log, the delays seem to be related to the indicators.

Perhaps someone who is testing 14.04 can confirm these delays and create the necessary bug reports.

---

### Post by ventrical on 2013-10-25
I am not getting a delay but I am getting a lightdm double take. That means that the login session with background will come on , fade out and then reassert itself (like a mini-boot within a boot).

---

### Post by Cavsfan on 2013-10-25
I think I am getting about the same. It takes maybe 20-30 seconds haven't counted but, the CLI login pops up for a few then it goes to GUI. 
As was mentioned this is really early in the cycle and it's looking pretty sweet from where I am.

My 12.04 Presice LTS install takes a lot longer to startup but, I don't mind.

---

### Post by xc3RnbFO8P on 2013-10-25
Mine is a mess:
```
[+0.01s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.01s] DEBUG: Starting Light Display Manager 1.9.0, UID=0 PID=1277
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-ubuntu.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/20-gnome.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.01s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registered seat module xlocal
[+0.01s] DEBUG: Registered seat module xremote
[+0.01s] DEBUG: Registered seat module unity
[+0.01s] DEBUG: Registered seat module surfaceflinger
[+0.01s] DEBUG: Adding default seat
[+0.04s] DEBUG: Quitting Plymouth; retaining splash
[+0.07s] DEBUG: Using VT 7
[+0.07s] DEBUG: Seat: Logging to /var/log/lightdm/unity-system-compositor.log
[+0.08s] DEBUG: Launching process 1292: /usr/sbin/unity-system-compositor.sleep --file '/tmp/mir_socket' --from-dm-fd 10 --to-dm-fd 13 --vt 7
[+0.08s] DEBUG: Seat: Waiting for system compositor for 60s
[+0.08s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.08s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.44s] DEBUG: Seat: Compositor closed communication channel
[+2.45s] DEBUG: Process 1292 exited with return value 1
[+2.45s] DEBUG: Releasing VT 7
[+2.45s] DEBUG: Seat: Compositor failed to start, switching to VT mode
[+2.45s] DEBUG: Seat: Starting
[+2.45s] DEBUG: Seat: Creating greeter session
[+2.45s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+2.45s] DEBUG: Seat: Not setting XDG_VTNR
[+2.45s] DEBUG: Seat: Creating display server of type x
[+2.45s] DEBUG: Seat: Starting X server on Unity compositor
[+2.45s] DEBUG: Using VT 7
[+2.45s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+2.45s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+2.45s] DEBUG: DisplayServer x-0: Launching X Server
[+2.45s] DEBUG: Launching process 1556: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+2.45s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+4.59s] DEBUG: Got signal 10 from process 1556
[+4.60s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+4.60s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+4.60s] DEBUG: Seat: Display server ready, starting session authentication
[+4.60s] DEBUG: Session: Setting XDG_VTNR=7
[+4.60s] DEBUG: Session pid=1660: Started with service 'lightdm-greeter', username 'lightdm'
[+5.91s] DEBUG: Session pid=1660: Authentication complete with return value 0: Success
[+5.91s] DEBUG: Seat: Session authenticated, running command
[+5.91s] DEBUG: Session pid=1660: Setting XDG_VTNR=7
[+5.91s] DEBUG: Session pid=1660: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+5.99s] DEBUG: Session pid=1660: Logging to /var/log/lightdm/x-0-greeter.log
[+6.03s] DEBUG: Activating VT 7
[+7.19s] DEBUG: Session pid=1660: Greeter connected version=1.9.0
[+9.43s] DEBUG: Session pid=1660: Greeter start authentication for rig
[+9.43s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+9.43s] DEBUG: Seat: Not setting XDG_VTNR
[+9.43s] DEBUG: Session: Setting XDG_VTNR=7
[+9.43s] DEBUG: Session pid=1985: Started with service 'lightdm', username 'rig'
[+9.45s] DEBUG: Session pid=1985: Got 1 message(s) from PAM
[+9.45s] DEBUG: Session pid=1660: Prompt greeter with 1 message(s)
[+9.52s] DEBUG: Session pid=1660: Greeter start authentication for rig
[+9.52s] DEBUG: Session pid=1985: Sending SIGTERM
[+9.52s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+9.52s] DEBUG: Seat: Not setting XDG_VTNR
[+9.52s] DEBUG: Session: Setting XDG_VTNR=7
[+9.52s] DEBUG: Session pid=1986: Started with service 'lightdm', username 'rig'
[+9.52s] DEBUG: Session pid=1985: Terminated with signal 15
[+9.52s] DEBUG: Session: Failed during authentication
[+9.52s] DEBUG: Seat: Session stopped
[+9.54s] DEBUG: Session pid=1986: Got 1 message(s) from PAM
[+9.54s] DEBUG: Session pid=1660: Prompt greeter with 1 message(s)
[+20.65s] DEBUG: Session pid=1660: Greeter start authentication for guest account
[+20.65s] DEBUG: Session pid=1986: Sending SIGTERM
[+20.65s] DEBUG: Session pid=1986: Terminated with signal 15
[+20.65s] DEBUG: Session: Failed during authentication
[+20.65s] DEBUG: Seat: Session stopped
[+26.85s] DEBUG: Session pid=1660: Greeter start authentication for lightdm
[+26.85s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+26.85s] DEBUG: Seat: Not setting XDG_VTNR
[+26.85s] DEBUG: Session: Setting XDG_VTNR=7
[+26.85s] DEBUG: Session pid=2407: Started with service 'lightdm', username 'lightdm'
[+26.89s] DEBUG: Session pid=2407: Got 1 message(s) from PAM
[+26.89s] DEBUG: Session pid=1660: Prompt greeter with 1 message(s)
[+29.40s] DEBUG: Session pid=1660: Greeter start authentication for rig
[+29.40s] DEBUG: Session pid=2407: Sending SIGTERM
[+29.40s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+29.41s] DEBUG: Seat: Not setting XDG_VTNR
[+29.41s] DEBUG: Session: Setting XDG_VTNR=7
[+29.41s] DEBUG: Session pid=2656: Started with service 'lightdm', username 'rig'
[+29.41s] DEBUG: Session pid=2407: Terminated with signal 15
[+29.41s] DEBUG: Session: Failed during authentication
[+29.41s] DEBUG: Seat: Session stopped
[+29.44s] DEBUG: Session pid=2656: Got 1 message(s) from PAM
[+29.44s] DEBUG: Session pid=1660: Prompt greeter with 1 message(s)
[+56.66s] DEBUG: Session pid=1660: Continue authentication
[+56.83s] DEBUG: Session pid=2656: Authentication complete with return value 0: Success
[+56.83s] DEBUG: Session pid=1660: Authenticate result for user rig: Success
[+56.91s] DEBUG: Session pid=1660: User rig authorized
[+56.94s] DEBUG: Session pid=1660: Greeter requests session cairo-dock
[+57.35s] DEBUG: Writing /home/rig/.dmrc
[+57.59s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+57.59s] DEBUG: Session pid=1660: Sending SIGTERM
[+57.62s] DEBUG: Session pid=1660: Exited with return value 0
[+57.62s] DEBUG: Seat: Session stopped
[+57.62s] DEBUG: Seat: Greeter stopped, running session
[+57.62s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+57.63s] DEBUG: Session pid=2656: Setting XDG_VTNR=7
[+57.63s] DEBUG: Session pid=2656: Running command /usr/sbin/lightdm-session gnome-session --session=cairo-dock
[+57.63s] DEBUG: Session pid=2656: Logging to .xsession-errors
[+57.81s] DEBUG: Activating VT 7
```

I got this Light Display Manager when I added Cinnamon session, and it doesn't work.
I'm using rig.

[[img]http://farm8.staticflickr.com/7381/10122169005_020587dc04_c.jpg[/img]](http://www.flickr.com/photos/96052779@N07/10122169005/)
[lightdm cinnamon](http://www.flickr.com/photos/96052779@N07/10122169005/) by [ringi_is](http://www.flickr.com/people/96052779@N07/), on Flickr

---

### Post by Cavsfan on 2013-10-25
> **Ringi said:**
> Mine is a mess:
```
[+0.01s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.01s] DEBUG: Starting Light Display Manager 1.9.0, UID=0 PID=1277
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-ubuntu.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/20-gnome.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-ubuntu.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf.d/50-xserver-command.conf
[+0.01s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
[+0.01s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.01s] DEBUG: Registered seat module xlocal
[+0.01s] DEBUG: Registered seat module xremote
[+0.01s] DEBUG: Registered seat module unity
[+0.01s] DEBUG: Registered seat module surfaceflinger
[+0.01s] DEBUG: Adding default seat
[+0.04s] DEBUG: Quitting Plymouth; retaining splash
[+0.07s] DEBUG: Using VT 7
[+0.07s] DEBUG: Seat: Logging to /var/log/lightdm/unity-system-compositor.log
[+0.08s] DEBUG: Launching process 1292: /usr/sbin/unity-system-compositor.sleep --file '/tmp/mir_socket' --from-dm-fd 10 --to-dm-fd 13 --vt 7
[+0.08s] DEBUG: Seat: Waiting for system compositor for 60s
[+0.08s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.08s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.44s] DEBUG: Seat: Compositor closed communication channel
[+2.45s] DEBUG: Process 1292 exited with return value 1
[+2.45s] DEBUG: Releasing VT 7
[+2.45s] DEBUG: Seat: Compositor failed to start, switching to VT mode
[+2.45s] DEBUG: Seat: Starting
[+2.45s] DEBUG: Seat: Creating greeter session
[+2.45s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+2.45s] DEBUG: Seat: Not setting XDG_VTNR
[+2.45s] DEBUG: Seat: Creating display server of type x
[+2.45s] DEBUG: Seat: Starting X server on Unity compositor
[+2.45s] DEBUG: Using VT 7
[+2.45s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
[+2.45s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
[+2.45s] DEBUG: DisplayServer x-0: Launching X Server
[+2.45s] DEBUG: Launching process 1556: /usr/bin/X -core :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
[+2.45s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
[+4.59s] DEBUG: Got signal 10 from process 1556
[+4.60s] DEBUG: DisplayServer x-0: Got signal from X server :0
[+4.60s] DEBUG: DisplayServer x-0: Connecting to XServer :0
[+4.60s] DEBUG: Seat: Display server ready, starting session authentication
[+4.60s] DEBUG: Session: Setting XDG_VTNR=7
[+4.60s] DEBUG: Session pid=1660: Started with service 'lightdm-greeter', username 'lightdm'
[+5.91s] DEBUG: Session pid=1660: Authentication complete with return value 0: Success
[+5.91s] DEBUG: Seat: Session authenticated, running command
[+5.91s] DEBUG: Session pid=1660: Setting XDG_VTNR=7
[+5.91s] DEBUG: Session pid=1660: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+5.99s] DEBUG: Session pid=1660: Logging to /var/log/lightdm/x-0-greeter.log
[+6.03s] DEBUG: Activating VT 7
[+7.19s] DEBUG: Session pid=1660: Greeter connected version=1.9.0
[+9.43s] DEBUG: Session pid=1660: Greeter start authentication for rig
[+9.43s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+9.43s] DEBUG: Seat: Not setting XDG_VTNR
[+9.43s] DEBUG: Session: Setting XDG_VTNR=7
[+9.43s] DEBUG: Session pid=1985: Started with service 'lightdm', username 'rig'
[+9.45s] DEBUG: Session pid=1985: Got 1 message(s) from PAM
[+9.45s] DEBUG: Session pid=1660: Prompt greeter with 1 message(s)
[+9.52s] DEBUG: Session pid=1660: Greeter start authentication for rig
[+9.52s] DEBUG: Session pid=1985: Sending SIGTERM
[+9.52s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+9.52s] DEBUG: Seat: Not setting XDG_VTNR
[+9.52s] DEBUG: Session: Setting XDG_VTNR=7
[+9.52s] DEBUG: Session pid=1986: Started with service 'lightdm', username 'rig'
[+9.52s] DEBUG: Session pid=1985: Terminated with signal 15
[+9.52s] DEBUG: Session: Failed during authentication
[+9.52s] DEBUG: Seat: Session stopped
[+9.54s] DEBUG: Session pid=1986: Got 1 message(s) from PAM
[+9.54s] DEBUG: Session pid=1660: Prompt greeter with 1 message(s)
[+20.65s] DEBUG: Session pid=1660: Greeter start authentication for guest account
[+20.65s] DEBUG: Session pid=1986: Sending SIGTERM
[+20.65s] DEBUG: Session pid=1986: Terminated with signal 15
[+20.65s] DEBUG: Session: Failed during authentication
[+20.65s] DEBUG: Seat: Session stopped
[+26.85s] DEBUG: Session pid=1660: Greeter start authentication for lightdm
[+26.85s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+26.85s] DEBUG: Seat: Not setting XDG_VTNR
[+26.85s] DEBUG: Session: Setting XDG_VTNR=7
[+26.85s] DEBUG: Session pid=2407: Started with service 'lightdm', username 'lightdm'
[+26.89s] DEBUG: Session pid=2407: Got 1 message(s) from PAM
[+26.89s] DEBUG: Session pid=1660: Prompt greeter with 1 message(s)
[+29.40s] DEBUG: Session pid=1660: Greeter start authentication for rig
[+29.40s] DEBUG: Session pid=2407: Sending SIGTERM
[+29.40s] DEBUG: Seat: Setting XDG_SEAT=seat0
[+29.41s] DEBUG: Seat: Not setting XDG_VTNR
[+29.41s] DEBUG: Session: Setting XDG_VTNR=7
[+29.41s] DEBUG: Session pid=2656: Started with service 'lightdm', username 'rig'
[+29.41s] DEBUG: Session pid=2407: Terminated with signal 15
[+29.41s] DEBUG: Session: Failed during authentication
[+29.41s] DEBUG: Seat: Session stopped
[+29.44s] DEBUG: Session pid=2656: Got 1 message(s) from PAM
[+29.44s] DEBUG: Session pid=1660: Prompt greeter with 1 message(s)
[+56.66s] DEBUG: Session pid=1660: Continue authentication
[+56.83s] DEBUG: Session pid=2656: Authentication complete with return value 0: Success
[+56.83s] DEBUG: Session pid=1660: Authenticate result for user rig: Success
[+56.91s] DEBUG: Session pid=1660: User rig authorized
[+56.94s] DEBUG: Session pid=1660: Greeter requests session cairo-dock
[+57.35s] DEBUG: Writing /home/rig/.dmrc
[+57.59s] DEBUG: Seat: Stopping greeter; display server will be re-used for user session
[+57.59s] DEBUG: Session pid=1660: Sending SIGTERM
[+57.62s] DEBUG: Session pid=1660: Exited with return value 0
[+57.62s] DEBUG: Seat: Session stopped
[+57.62s] DEBUG: Seat: Greeter stopped, running session
[+57.62s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+57.63s] DEBUG: Session pid=2656: Setting XDG_VTNR=7
[+57.63s] DEBUG: Session pid=2656: Running command /usr/sbin/lightdm-session gnome-session --session=cairo-dock
[+57.63s] DEBUG: Session pid=2656: Logging to .xsession-errors
[+57.81s] DEBUG: Activating VT 7
```

I got this Light Display Manager when I added Cinnamon session, and it doesn't work.
I'm using rig.

[[IMG]http://farm8.staticflickr.com/7381/10122169005_020587dc04_c.jpg[/IMG]]("http://www.flickr.com/photos/96052779@N07/10122169005/")
[lightdm cinnamon]("http://www.flickr.com/photos/96052779@N07/10122169005/") by [ringi_is]("http://www.flickr.com/people/96052779@N07/"), on Flickr

This thread is for Ubuntu+1 14.04. It looks like you have 13.10. You should post a thread in General Help.

---

### Post by xc3RnbFO8P on 2013-10-25
> **Cavsfan said:**
> This thread is for Ubuntu+1 14.04. It looks like you have 13.10. You should post a thread in General Help.

Lightdm will change later to 14.04, in 13.10 it change in alpha1

```
rig@rig-Aspire-R3600:~$ echo && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || echo && cat /proc/version  && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    LG Flatron W2452T " && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

Current Date/Time: fre okt 25 20:13:02 UTC 2013
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux version 3.11.0-13-generic (buildd@roseapple) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: ION/integrated/SSE2
OpenGL version string:  3.3.0 NVIDIA 331.13

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 130
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
  Version: 9.2.2-1ubuntu1

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  NVIDIA Corporation MCP79 Host Bridge
           +-00.1  NVIDIA Corporation MCP79 Memory Controller
           +-03.0  NVIDIA Corporation MCP79 LPC Bridge
           +-03.1  NVIDIA Corporation MCP79 Memory Controller
           +-03.2  NVIDIA Corporation MCP79 SMBus
           +-03.3  NVIDIA Corporation MCP79 Memory Controller
           +-03.5  NVIDIA Corporation MCP79 Co-processor
           +-04.0  NVIDIA Corporation MCP79 OHCI USB 1.1 Controller
           +-04.1  NVIDIA Corporation MCP79 EHCI USB 2.0 Controller
           +-08.0  NVIDIA Corporation MCP79 High Definition Audio
           +-09.0-[01]--
           +-0a.0  NVIDIA Corporation MCP79 Ethernet
           +-0b.0  NVIDIA Corporation MCP79 AHCI Controller
           +-0c.0-[02]--
           +-10.0-[03]----00.0  NVIDIA Corporation ION VGA
           +-15.0-[04]--
           +-16.0-[05]----00.0  Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express)
           +-17.0-[06]--
           \-18.0-[07]--

Display Properties:
 lcd monitor:    LG Flatron W2452T 
  dimensions:    1920x1200 pixels (508x318 millimeters)
  resolution:    96x96 dots per inch
```

---

### Post by tad1073 on 2013-10-25
> **Toz said:**
> I see you're running Ubuntu 14.04. Moving to the **Ubuntu+1** forum.

Since this is a very early version of 14.04, I think you should expect these sorts of issues. From looking at the x-0-greeter.log, the delays seem to be related to the indicators.

Perhaps someone who is testing 14.04 can confirm these delays and create the necessary bug reports.

I was on 13.10 and having the same issues.

---

### Post by cariboo on 2013-10-25
I'd suggest using bootchart to see where the problem is. Bootchart is in the repositories.

---

### Post by tad1073 on 2013-10-25
> **cariboo907 said:**
> I'd suggest using bootchart to see where the problem is. Bootchart is in the repositories.

I don't know how to read it but here it is.

[https://www.dropbox.com/s/7g55ig1847nzbze/thomthom-trusty-20131025-1.png](https://www.dropbox.com/s/7g55ig1847nzbze/thomthom-trusty-20131025-1.png)

---

### Post by mc4man on 2013-10-26
If you're booting/installed to a hdd then 52 sec probably is average, give or take 5-15 sec's

If you're using your ssd then it's awful, I'd expect 5-10 sec's.
(using an external ssd thru a less than fullrate usb3 port here & it's 15 sec in bootchart with No autologin

likely offtopic
(- Is there any good reason you use nomodeset

---

### Post by tad1073 on 2013-10-26
> **mc4man said:**
> If you're booting/installed to a hdd then 52 sec probably is average, give or take 5-15 sec's

If you're using your ssd then it's awful, I'd expect 5-10 sec's.
(using an external ssd thru a less than fullrate usb3 port here & it's 15 sec in bootchart with No autologin

likely offtopic
(- Is there any good reason you use nomodeset

Ubuntu is on my SSD.

[s]I use nomodeset because I am using nvidia drivers.[/s]

I turned off the nomodeset variable and it's working fine. Before without it nvidia drivers would break.

---

### Post by Cavsfan on 2013-10-26
@Ringi: I guess the 13.10 in the bottom of that picture is what made me think that but this is still early enough that things are probably labeled 13.10
I'm using the 319.60 Ubuntu Nvidia driver and everything is running smooth as silk even with Compiz, Cairo Dock, the Cube and the whole 9 yards.

```
cavsfan@cavsfan-MS-7529:~$ echo && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || echo && cat /proc/version  && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    LG Flatron W2452T " && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

Current Date/Time: Sat Oct 26 20:54:49 UTC 2013
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux version 3.11.0-12-generic (buildd@allspice) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu7) ) #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 319.60

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 130
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
dpkg-query: package 'mesa-common-dev' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
           +-01.0-[01]----00.0  NVIDIA Corporation G92 [GeForce 9800 GT]
           +-1b.0  Intel Corporation NM10/ICH7 Family High Definition Audio Controller
           +-1c.0-[02]--
           +-1c.1-[03]----00.0  Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           +-1d.0  Intel Corporation NM10/ICH7 Family USB UHCI Controller #1
           +-1d.1  Intel Corporation NM10/ICH7 Family USB UHCI Controller #2
           +-1d.2  Intel Corporation NM10/ICH7 Family USB UHCI Controller #3
           +-1d.3  Intel Corporation NM10/ICH7 Family USB UHCI Controller #4
           +-1d.7  Intel Corporation NM10/ICH7 Family USB2 EHCI Controller
           +-1e.0-[04]--
           +-1f.0  Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801G (ICH7 Family) IDE Controller
           +-1f.2  Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode]
           \-1f.3  Intel Corporation NM10/ICH7 Family SMBus Controller

Display Properties:
 lcd monitor:    HANNS-G HG281
  dimensions:    1920x1200 pixels (508x318 millimeters)
  resolution:    96x96 dots per inch
```
> **tad1073 said:**
> Ubuntu is on my SSD.

[s]I use nomodeset because I am using nvidia drivers.[/s]

I turned off the nomodeset variable and it's working fine. Before without it nvidia drivers would break.
Does that mean problem solved?

---

### Post by tad1073 on 2013-10-26
> **Cavsfan said:**
> @Ringi: I guess the 13.10 in the bottom of that picture is what made me think that but this is still early enough that things are probably labeled 13.10
I'm using the 319.60 Ubuntu Nvidia driver and everything is running smooth as silk even with Compiz, Cairo Dock, the Cube and the whole 9 yards.

```
cavsfan@cavsfan-MS-7529:~$ echo && echo -n "Current Date/Time: " && TZ='UTC' date && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || echo && cat /proc/version  && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo && dpkg -s mesa-utils && echo || echo && echo "Package: mesa-common-dev" && dpkg -s mesa-common-dev | sed 's/^/  /' | grep Version && echo || echo && echo "Package: xserver-xorg-core" && apt-cache policy xserver-xorg-core | grep Installed && echo || echo && echo "Package: xserver-common" && apt-cache policy xserver-common | grep Installed && echo || echo && echo "Package: xserver-xephyr" && apt-cache policy xserver-xephyr | grep Installed && echo || echo && echo "Tree Map of PCI Devices:" && lspci -tv && echo || echo && echo "Display Properties:" && echo -n " lcd monitor:    LG Flatron W2452T " && echo && xdpyinfo | grep -E '(resolution|dimensions)' && echo

Current Date/Time: Sat Oct 26 20:54:49 UTC 2013
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux version 3.11.0-12-generic (buildd@allspice) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu7) ) #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013
Gnome Release: GNOME Shell 3.8.4
Unity Release: unity 7.1.2

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9800 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 319.60

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 130
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
dpkg-query: package 'mesa-common-dev' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-xephyr
  Installed: 2:1.14.3-3ubuntu3

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
           +-01.0-[01]----00.0  NVIDIA Corporation G92 [GeForce 9800 GT]
           +-1b.0  Intel Corporation NM10/ICH7 Family High Definition Audio Controller
           +-1c.0-[02]--
           +-1c.1-[03]----00.0  Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller
           +-1d.0  Intel Corporation NM10/ICH7 Family USB UHCI Controller #1
           +-1d.1  Intel Corporation NM10/ICH7 Family USB UHCI Controller #2
           +-1d.2  Intel Corporation NM10/ICH7 Family USB UHCI Controller #3
           +-1d.3  Intel Corporation NM10/ICH7 Family USB UHCI Controller #4
           +-1d.7  Intel Corporation NM10/ICH7 Family USB2 EHCI Controller
           +-1e.0-[04]--
           +-1f.0  Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge
           +-1f.1  Intel Corporation 82801G (ICH7 Family) IDE Controller
           +-1f.2  Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode]
           \-1f.3  Intel Corporation NM10/ICH7 Family SMBus Controller

Display Properties:
 lcd monitor:    HANNS-G HG281
  dimensions:    1920x1200 pixels (508x318 millimeters)
  resolution:    96x96 dots per inch
```

Does that mean problem solved?

Not with boot time.

---

### Post by zika on 2013-10-26
What do You get with...
```
dmesg|grep soft
```?

---

### Post by tad1073 on 2013-10-26
> **zika said:**
> What do You get with...
```
dmesg|grep soft
```?


```
:~$ dmesg |grep soft
[    0.477137] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.477190] software IO TLB [mem 0xc3e90000-0xc7e90000] (64MB) mapped at [ffff8800c3e90000-ffff8800c7e8ffff]
[    1.052131] usb 1-4: Product: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam Cinema(TM)
[    1.052189] usb 1-4: Manufacturer: Microsoft
[    2.823119] uvcvideo: Found UVC 1.00 device Microsoft\xffffffc2\xffffffae\xffffffae LifeCam Cinema(TM) (045e:075d)
[    2.830297] input: Microsoft\xffffffc2\xffffffae\xffffffae LifeCam Cinema(TM) as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input10
[    4.081056] usb 4-1: Product: Microsoft Wireless Desktop Receiver 3.1
[    4.193834] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input15
[    4.196596] microsoft 0003:045E:00F9.0002: input,hidraw0: USB HID v1.11 Keyboard [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1a.1-1/input0
[    4.196614] microsoft 0003:045E:00F9.0003: fixing up Microsoft Wireless Receiver Model 1028 report descriptor
[    4.245238] input: Microsft Microsoft Wireless Desktop Receiver 3.1 as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input16
[    4.245416] microsoft 0003:045E:00F9.0003: input,hidraw1: USB HID v1.11 Mouse [Microsft Microsoft Wireless Desktop Receiver 3.1] on usb-0000:00:1a.1-1/input1
```

```
Current Date/Time: Sat Oct 26 21:51:22 UTC 2013
Distro Release: Ubuntu Trusty Tahr (development branch)
Kernel Release: Linux version 3.11.0-13-generic (buildd@roseapple) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013
Gnome Release: The program 'gnome-shell' is currently not installed. You can install it by typing:
sudo apt-get install gnome-shell

Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 130
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: mesa-demos
Version: 8.1.0-2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.14), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
Homepage: http://mesa3d.org/

Package: mesa-common-dev
dpkg-query: package 'mesa-common-dev' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Package: xserver-xorg-core
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-common
  Installed: 2:1.14.3-3ubuntu3

Package: xserver-xephyr
  Installed: (none)

Tree Map of PCI Devices:
-[0000:00]-+-00.0  Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller
           +-01.0-[01]--+-00.0  NVIDIA Corporation GF116 [GeForce GTX 550 Ti]
           |            \-00.1  NVIDIA Corporation GF116 High Definition Audio Controller
           +-19.0  Intel Corporation 82566DC-2 Gigabit Network Connection
           +-1a.0  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4
           +-1a.1  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5
           +-1a.2  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6
           +-1a.7  Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2
           +-1b.0  Intel Corporation 82801I (ICH9 Family) HD Audio Controller
           +-1d.0  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1
           +-1d.1  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2
           +-1d.2  Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3
           +-1d.7  Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1
           +-1e.0-[02]--+-00.0  Qualcomm Atheros AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn]
           |            \-06.0  VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
           +-1f.0  Intel Corporation 82801IH (ICH9DH) LPC Interface Controller
           +-1f.2  Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA Controller [IDE mode]
           +-1f.3  Intel Corporation 82801I (ICH9 Family) SMBus Controller
           \-1f.5  Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode]

Display Properties:
 lcd monitor:    LG Flatron W2452T 
  dimensions:    3840x1080 pixels (1016x286 millimeters)
  resolution:    96x96 dots per inch


```

---

### Post by mc4man on 2013-10-26
I put a new 14.04 install on same drive, very little changed from default & it's actually gotten faster than prev (which was really 13.10, set up & using)
So bootchart shows @ 9 sec's, the biggest gain would be systemd-udevd & wait for root, prev. about 8 sec, now down to 3. The rest is pretty much the same.

Pardon my ignorance but
is this a fresh 14.04 install
are you using this as a server (I see some things loading in your install that aren't here

---

### Post by cariboo on 2013-10-26
@tad1073 , I have to admit, I'm a bit confused too, are you running the server version or the desktop? I see you have:

[LIST]
[*]Apache2
[*]Mysql
[*]Samba
[/LIST]


Plus something called miniserver.pl.

That being said, the server components shouldn't take all that much extra time to load, but I know it does make a difference. I have two servers here, one running the full LAMP stack plus Samba and NFS, and the other is just a minidlna server. The minidlna server running on an Atom cpu with 1GiB of ram and 2 5400 RPM laptop drives using LVM boots in about 10 seconds, while my main server running on an Intel E5400 cpu with 4GiB ram and 6 various sized hard drives in a jbod array boots up in about 15 seconds.

Neither run a gui of any sort, so they boot faster than a comparable system running the desktop version.

---

### Post by tad1073 on 2013-10-27
> **cariboo907 said:**
> @tad1073 , I have to admit, I'm a bit confused too, are you running the server version or the desktop? I see you have:

[LIST]
[*]Apache2 
[*]Mysql 
[*]Samba 
[/LIST]


Plus something called miniserver.pl.

That being said, the server components shouldn't take all that much extra time to load, but I know it does make a difference. I have two servers here, one running the full LAMP stack plus Samba and NFS, and the other is just a minidlna server. The minidlna server running on an Atom cpu with 1GiB of ram and 2 5400 RPM laptop drives using LVM boots in about 10 seconds, while my main server running on an Intel E5400 cpu with 4GiB ram and 6 various sized hard drives in a jbod array boots up in about 15 seconds.

Neither run a gui of any sort, so they boot faster than a comparable system running the desktop version.

I am running the desktop version with the lamp stack. I am hosting my own website and have xbmc synced to the computer in the living room, as for the miniserver.pl, I have no clue what that is.

---

### Post by tad1073 on 2013-10-29
I have reverted back to 13.04 and my boot time has significantly decreased so that tells me that is something to do with 13.10 and 14.04.

---

### Post by tad1073 on 2013-10-30
I did a clean install of 13.10 for the second time and my boot time is what it should be now but Istill don't know what the problem was.

I went ahead and updated to 14.04 and no problems with boot time.

---

### Post by tad1073 on 2013-11-05
I switched back to 13.04 then installed the 3.12.0-031200 and concluded that it has something to do with the kernel because when I booted into 3.12 I had the same results as before, how to I go about notifying the kernel devs?

---

### Post by cariboo on 2013-11-05
You create a bug report against the kernel by using the following command:

```
apport linux
```

One of the Ubuntu kernel team will get back to you and have you run some tests to determine what the problem is. It may entail installing several different kernels, so you have to be willing to do the work to get the problem solved.

---

### Post by tad1073 on 2013-11-05
> **cariboo907 said:**
> You create a bug report against the kernel by using the following command:

```
apport linux
```

One of the Ubuntu kernel team will get back to you and have you run some tests to determine what the problem is. It may entail installing several different kernels, so you have to be willing to do the work to get the problem solved.


[s]No problem.[/s]

No command found for apport.

---

### Post by cariboo on 2013-11-06
I'm sorry, but I gave you the wrong command, it should be:

```
apport-bug linux
```

is the correct command. 

This is the only way to create a bug-report that will be looked at. For more information on bug reporting have a look at [this]("https://help.ubuntu.com/community/ReportingBugs") wiki page. Which is also linked to in my [sticky]("http://ubuntuforums.org/showthread.php?t=2181769") on the main page.

---

### Post by tad1073 on 2013-11-06
thanks, got it filed.

---

### Post by QDR06VV9 on 2013-11-06
> **Toz said:**
> I see you're running Ubuntu 14.04. Moving to the **Ubuntu+1** forum.

Since this is a very early version of 14.04, I think you should expect these sorts of issues. From looking at the x-0-greeter.log, the delays seem to be related to the indicators.

Perhaps someone who is testing 14.04 can [COLOR=#a52a2a]_confirm these delays _[/COLOR]and create the necessary bug reports.
This has been the norm at least for me since precise.(using pre-alphas, alphas, betas, and rc candidates)
But Also I run Multiple Desktops Gnome, KDE, Cinnamon, fallback or flashback.

---

### Post by tad1073 on 2013-11-07
Nvidia just released 331.20 driver and it fixed the slow boot time problem, reference this post here.
[http://ubuntuforums.org/showthread.php?t=2185004](http://ubuntuforums.org/showthread.php?t=2185004)

---

