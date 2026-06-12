---
title: "Ubuntu Enterprise Server 16.04 lightdm not starting on boot up."
date: 2016-02-22
forum: Ubuntu Development Version
---

### Post by mikenash on 2016-02-22
I have a new install of ubuntu 16.04 where lightdm is failing to start.  I would link to know if there are an Administator's Guide available?
When looking at the log there are no /etc/xdg/lightdm configuration directories or files. 

```
 systemctl status lightdm
&#9679; lightdm.service - Light Display Manager
   Loaded: loaded (/lib/systemd/system/lightdm.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since Mon 2016-02-22 10:40:23 EST; 6h ago
     Docs: man:lightdm(1)
  Process: 841 ExecStart=/usr/sbin/lightdm (code=exited, status=1/FAILURE)
  Process: 836 ExecStartPre=/bin/sh -c [ "$(basename $(cat /etc/X11/default-display-manager 2>/dev/null))" = "lightdm" ] (code=exite
d, status=0/SUCCESS)
 Main PID: 841 (code=exited, status=1/FAILURE)

Feb 22 10:40:22 linux140 systemd[1]: lightdm.service: Main process exited, code=exited, status=1/FAILURE
Feb 22 10:40:22 linux140 systemd[1]: lightdm.service: Unit entered failed state.
Feb 22 10:40:22 linux140 systemd[1]: lightdm.service: Failed with result 'exit-code'.
Feb 22 10:40:23 linux140 systemd[1]: lightdm.service: Service hold-off time over, scheduling restart.
Feb 22 10:40:23 linux140 systemd[1]: Stopped Light Display Manager.
Feb 22 10:40:23 linux140 systemd[1]: lightdm.service: Start request repeated too quickly.
Feb 22 10:40:23 linux140 systemd[1]: Failed to start Light Display Manager.
```

```
 root@linux140:/var/log/lightdm# cat lightdm.log
 [+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
 [+0.00s] DEBUG: Starting Light Display Manager 1.17.5, UID=0 PID=703
 [+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
 [+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
 [+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
 [+0.00s] DEBUG: Registered seat module xlocal
 [+0.00s] DEBUG: Registered seat module xremote
 [+0.00s] DEBUG: Registered seat module unity
 [+0.02s] DEBUG: Monitoring logind for seats
 [+0.02s] DEBUG: New seat added from logind: seat0
 [+0.02s] DEBUG: Seat seat0: Loading properties from config section Seat:*
 [+0.02s] DEBUG: Seat seat0 has property CanMultiSession=no
 [+0.02s] DEBUG: Seat seat0: Starting
 [+0.02s] DEBUG: Seat seat0: Creating greeter session
 [+0.02s] DEBUG: Seat seat0: Creating display server of type x
 [+0.02s] DEBUG: Using VT 7
 [+0.02s] DEBUG: Seat seat0: Starting local X display on VT 7
 [+0.02s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
 [+0.02s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
 [+0.02s] DEBUG: DisplayServer x-0: Launching X Server
 [+0.02s] DEBUG: Launching process 759: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
 [+0.02s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
 [+0.02s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
 [+0.02s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
 [+0.07s] DEBUG: Loading users from org.freedesktop.Accounts
 [+0.07s] DEBUG: User /org/freedesktop/Accounts/User1000 added
 [+0.53s] DEBUG: Process 759 terminated with signal 6
 [+0.53s] DEBUG: DisplayServer x-0: X server stopped
 [+0.53s] DEBUG: Releasing VT 7
 [+0.53s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
 [+0.53s] DEBUG: Seat seat0: Display server stopped
 [+0.53s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
 [+0.53s] DEBUG: Seat seat0: Stopping
 [+0.53s] DEBUG: Seat seat0: Stopping session
 [+0.53s] DEBUG: Seat seat0: Session stopped
 [+0.53s] DEBUG: Seat seat0: Stopped
 [+0.53s] DEBUG: Required seat has stopped
 [+0.53s] DEBUG: Stopping display manager
 [+0.53s] DEBUG: Display manager stopped
 [+0.53s] DEBUG: Stopping daemon
 [+0.53s] DEBUG: Seat seat0: Stopping session
 [+0.53s] DEBUG: Exiting with return value 1
 [+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
 [+0.00s] DEBUG: Starting Light Display Manager 1.17.5, UID=0 PID=793
 [+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
 [+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
 [+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
 [+0.00s] DEBUG: Registered seat module xlocal
 [+0.00s] DEBUG: Registered seat module xremote
 [+0.00s] DEBUG: Registered seat module unity
 [+0.00s] DEBUG: Monitoring logind for seats
 [+0.00s] DEBUG: New seat added from logind: seat0
 [+0.00s] DEBUG: Seat seat0: Loading properties from config section Seat:*
 [+0.00s] DEBUG: Seat seat0 has property CanMultiSession=no
 [+0.00s] DEBUG: Seat seat0: Starting
 [+0.00s] DEBUG: Seat seat0: Creating greeter session
 [+0.00s] DEBUG: Seat seat0: Creating display server of type x
 [+0.01s] DEBUG: Using VT 7
 [+0.01s] DEBUG: Seat seat0: Starting local X display on VT 7
 [+0.01s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
 [+0.01s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
 [+0.01s] DEBUG: DisplayServer x-0: Launching X Server
 [+0.01s] DEBUG: Launching process 801: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
 [+0.01s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
 [+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
 [+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
 [+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
 [+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
 [+0.12s] DEBUG: Process 801 terminated with signal 6
 [+0.12s] DEBUG: DisplayServer x-0: X server stopped
 [+0.12s] DEBUG: Releasing VT 7
 [+0.12s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
 [+0.12s] DEBUG: Seat seat0: Display server stopped
 [+0.12s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
 [+0.12s] DEBUG: Seat seat0: Stopping
 [+0.12s] DEBUG: Seat seat0: Stopping session
 [+0.12s] DEBUG: Seat seat0: Session stopped
 [+0.12s] DEBUG: Seat seat0: Stopped
 [+0.12s] DEBUG: Required seat has stopped
 [+0.12s] DEBUG: Stopping display manager
 [+0.12s] DEBUG: Display manager stopped
 [+0.12s] DEBUG: Stopping daemon
 [+0.12s] DEBUG: Seat seat0: Stopping session
 [+0.12s] DEBUG: Exiting with return value 1
 [+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
 [+0.00s] DEBUG: Starting Light Display Manager 1.17.5, UID=0 PID=809
 [+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
 [+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
 [+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
 [+0.00s] DEBUG: Registered seat module xlocal
 [+0.00s] DEBUG: Registered seat module xremote
 [+0.00s] DEBUG: Registered seat module unity
 [+0.00s] DEBUG: Monitoring logind for seats
 [+0.00s] DEBUG: New seat added from logind: seat0
 [+0.00s] DEBUG: Seat seat0: Loading properties from config section Seat:*
 [+0.00s] DEBUG: Seat seat0 has property CanMultiSession=no
 [+0.00s] DEBUG: Seat seat0: Starting
 [+0.00s] DEBUG: Seat seat0: Creating greeter session
 [+0.00s] DEBUG: Seat seat0: Creating display server of type x
 [+0.01s] DEBUG: Using VT 7
 [+0.01s] DEBUG: Seat seat0: Starting local X display on VT 7
 [+0.01s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
 [+0.01s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
 [+0.01s] DEBUG: DisplayServer x-0: Launching X Server
 [+0.01s] DEBUG: Launching process 817: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
 [+0.01s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
 [+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
 [+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
 [+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
 [+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
 [+0.12s] DEBUG: Process 817 terminated with signal 6
 [+0.12s] DEBUG: DisplayServer x-0: X server stopped
 [+0.12s] DEBUG: Releasing VT 7
 [+0.12s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
 [+0.12s] DEBUG: Seat seat0: Display server stopped
 [+0.12s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
 [+0.12s] DEBUG: Seat seat0: Stopping
 [+0.12s] DEBUG: Seat seat0: Stopping session
 [+0.12s] DEBUG: Seat seat0: Session stopped
 [+0.12s] DEBUG: Seat seat0: Stopped
 [+0.12s] DEBUG: Required seat has stopped
 [+0.12s] DEBUG: Stopping display manager
 [+0.12s] DEBUG: Display manager stopped
 [+0.12s] DEBUG: Stopping daemon
 [+0.12s] DEBUG: Seat seat0: Stopping session
 [+0.12s] DEBUG: Exiting with return value 1
 [+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
 [+0.00s] DEBUG: Starting Light Display Manager 1.17.5, UID=0 PID=825
 [+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
 [+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
 [+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
 [+0.00s] DEBUG: Registered seat module xlocal
 [+0.00s] DEBUG: Registered seat module xremote
 [+0.00s] DEBUG: Registered seat module unity
 [+0.00s] DEBUG: Monitoring logind for seats
 [+0.00s] DEBUG: New seat added from logind: seat0
 [+0.00s] DEBUG: Seat seat0: Loading properties from config section Seat:*
 [+0.00s] DEBUG: Seat seat0 has property CanMultiSession=no
 [+0.00s] DEBUG: Seat seat0: Starting
 [+0.00s] DEBUG: Seat seat0: Creating greeter session
 [+0.00s] DEBUG: Seat seat0: Creating display server of type x
 [+0.01s] DEBUG: Using VT 7
 [+0.01s] DEBUG: Seat seat0: Starting local X display on VT 7
 [+0.01s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
 [+0.01s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
 [+0.01s] DEBUG: DisplayServer x-0: Launching X Server
 [+0.01s] DEBUG: Launching process 833: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
 [+0.01s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
 [+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
 [+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
 [+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
 [+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
 [+0.12s] DEBUG: Process 833 terminated with signal 6
 [+0.12s] DEBUG: DisplayServer x-0: X server stopped
 [+0.12s] DEBUG: Releasing VT 7
 [+0.12s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
 [+0.12s] DEBUG: Seat seat0: Display server stopped
 [+0.12s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
 [+0.12s] DEBUG: Seat seat0: Stopping
 [+0.12s] DEBUG: Seat seat0: Stopping session
 [+0.12s] DEBUG: Seat seat0: Session stopped
 [+0.12s] DEBUG: Seat seat0: Stopped
 [+0.12s] DEBUG: Required seat has stopped
 [+0.12s] DEBUG: Stopping display manager
 [+0.12s] DEBUG: Display manager stopped
 [+0.12s] DEBUG: Stopping daemon
 [+0.12s] DEBUG: Seat seat0: Stopping session
 [+0.12s] DEBUG: Exiting with return value 1
 [+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
 [+0.00s] DEBUG: Starting Light Display Manager 1.17.5, UID=0 PID=841
 [+0.00s] DEBUG: Loading configuration dirs from /usr/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-disable-log-backup.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-greeter-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-guest-wrapper.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/50-xserver-command.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-lightdm-gtk-greeter.conf
 [+0.00s] DEBUG: Loading configuration from /usr/share/lightdm/lightdm.conf.d/60-xubuntu.conf
 [+0.00s] DEBUG: Loading configuration dirs from /usr/local/share/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration dirs from /etc/xdg/lightdm/lightdm.conf.d
 [+0.00s] DEBUG: Loading configuration from /etc/lightdm/lightdm.conf
 [+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
 [+0.00s] DEBUG: Registered seat module xlocal
 [+0.00s] DEBUG: Registered seat module xremote
 [+0.00s] DEBUG: Registered seat module unity
 [+0.00s] DEBUG: Monitoring logind for seats
 [+0.00s] DEBUG: New seat added from logind: seat0
 [+0.00s] DEBUG: Seat seat0: Loading properties from config section Seat:*
 [+0.00s] DEBUG: Seat seat0 has property CanMultiSession=no
 [+0.00s] DEBUG: Seat seat0: Starting
 [+0.00s] DEBUG: Seat seat0: Creating greeter session
 [+0.00s] DEBUG: Seat seat0: Creating display server of type x
 [+0.01s] DEBUG: Using VT 7
 [+0.01s] DEBUG: Seat seat0: Starting local X display on VT 7
 [+0.01s] DEBUG: DisplayServer x-0: Logging to /var/log/lightdm/x-0.log
 [+0.01s] DEBUG: DisplayServer x-0: Writing X server authority to /var/run/lightdm/root/:0
 [+0.01s] DEBUG: DisplayServer x-0: Launching X Server
 [+0.01s] DEBUG: Launching process 849: /usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
 [+0.01s] DEBUG: DisplayServer x-0: Waiting for ready signal from X server :0
 [+0.01s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
 [+0.01s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
 [+0.01s] DEBUG: Loading users from org.freedesktop.Accounts
 [+0.01s] DEBUG: User /org/freedesktop/Accounts/User1000 added
 [+0.12s] DEBUG: Process 849 terminated with signal 6
 [+0.12s] DEBUG: DisplayServer x-0: X server stopped
 [+0.12s] DEBUG: Releasing VT 7
 [+0.12s] DEBUG: DisplayServer x-0: Removing X server authority /var/run/lightdm/root/:0
 [+0.12s] DEBUG: Seat seat0: Display server stopped
 [+0.12s] DEBUG: Seat seat0: Stopping; greeter display server failed to start
 [+0.12s] DEBUG: Seat seat0: Stopping
 [+0.12s] DEBUG: Seat seat0: Stopping session
 [+0.12s] DEBUG: Seat seat0: Session stopped
 [+0.12s] DEBUG: Seat seat0: Stopped
 [+0.12s] DEBUG: Required seat has stopped
 [+0.12s] DEBUG: Stopping display manager
 [+0.12s] DEBUG: Display manager stopped
 [+0.12s] DEBUG: Stopping daemon
 [+0.12s] DEBUG: Seat seat0: Stopping session
 [+0.12s] DEBUG: Exiting with return value 1
 
```

---

### Post by MAFoElffen on 2016-02-22
Just trying to decipher what you posted. I know a bit about the Linux Graphics Layer...
 - Ubuntu 16.04 is still in pre-release / alpha. Release is still out over a month from now. 
 - There is no Enterprise version of Desktop nor Server. (Is this your idea?)
 - There is no GUI with Server Edition.
 - Ligthdm is a graphical login manager. Which would be dependent on XServer and a Desktop Manager. 

So-- Did you install 16.04 Server Editon (alpha), XServer, a Desktop Manager and a Graphical logon Manager? If so- which pieces and in what order? 

Why? Because the order you install those pieces matters to get the wiring right.

Beyond that-- It went south, right after these lines:
```

 [+0.07s] DEBUG: Loading users from org.freedesktop.Accounts
 [+0.07s] DEBUG: User /org/freedesktop/Accounts/User1000 added

```
About that time, it's going to look for the user's .Xauthority file. And root does not have one, so he cant' do that without a workaround... Problem with that is most commonly a permissions/ownership problem.

Please tell s which user was tryign to log in and post the results for that userName (please subsittue the userName of the user):
```

ls -ls /home/userName/.Xauthority

```
Right after it succefully hits that file, then it should continue with the desktop manager... 

I install minimal X instances in this order
(1) XServer
(2) Desktop Manager
(3) Graphical Login Manager
If you do not install (on your own, with your won pieces) then the wiring is not wired right... It just seems to work or fail that way.

---

### Post by bab1 on 2016-02-22
> **mikenash said:**
> I have a new install of ubuntu 16.04 where lightdm is failing to start.  I would link to know if there are an Administator's Guide available?
When looking at the log there are no /etc/xdg/lightdm configuration directories or files. 

@ MAFoElffen's points are cogent, nevertheless this post belongs in the forum: [**Ubuntu Development Version**]("http://ubuntuforums.org/forumdisplay.php?f=427") at the present time.  It deals with a future release of Ubuntu.  Things can (and do) change.

---

### Post by QIII on 2016-02-22
*Moved to **Ubuntu Development Version***

---

### Post by mikenash on 2016-02-23
During the initial install a userid named michael was created.  No other configurations were asked to be made.  Some packages would fail during an install and some packages I did not select.  I noted the failures and performed a fresh install with the packages that I wanted and knew would install.  The installation order is controlled by the installlation process.  I am thinking that lightdm is a VNC server that is simular to the tiger-vnc used by Red Hat and Suse.  
This setup was a fresh install:
Installed selections:
 Manual Package Installer
 Standard system utilities
 Tomcat Java Server
 Open SSH server  
 Basic Ubuntu Server  
 Samba file server
 Ubuntu Mate desktop
 Xbantu minimal installation
 xbuntu desktop
 

 

 Not Selected:
 Ubuntu Cloud Image
 DNS server  
 LAMP server  
 Mail Server  
 Ubuntu Mate cloudtop
 
Note:  I did not select these packages during this install.

 Prior selections that failed: 

 Postgresql database                                      Process - FAILED
 Ubuntu Mate minimal installation               Process - FAILED
 Virtual machine host                                   Process - FAILED

---

