---
title: "Deamon starts as Active (exited)"
date: 2016-03-24
forum: Server Platforms
---

### Post by izznogooood on 2016-03-24
I have installed a python script called "plexconnect" which is basicly a script to trick my apple tv3 in to looking elsewhere for its trailers.
More information here: [https://github.com/iBaa/PlexConnect](https://github.com/iBaa/PlexConnect)

Then i made an init script.
Source: [https://forums.plex.tv/discussion/156534/install-on-ubuntu-server](https://forums.plex.tv/discussion/156534/install-on-ubuntu-server)

The (minor) problem i have with this init script is after a reboot the service allways start as active (exited):

```
&#9679; plexconnect.service - LSB: This is the Plex Connect daemon
   Loaded: loaded (/etc/init.d/plexconnect; bad; vendor preset: enabled)
   Active: active (exited) since sø. 2016-03-27 14:29:27 CEST; 1min 14s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1043 ExecStart=/etc/init.d/plexconnect start (code=exited, status=0/SUCCESS)
    Tasks: 0 (limit: 512)


mars 27 14:29:26 lenox2 systemd[1]: Starting LSB: This is the Plex Connect daemon...
mars 27 14:29:27 lenox2 plexconnect[1043]:  * Starting the process PlexConnect
mars 27 14:29:27 lenox2 systemd[1]: Started LSB: This is the Plex Connect daemon.
[COLOR=#C7254E][FONT=Menlo]
[/FONT][/COLOR]
```

After i restart the service it works fine active (running):

```
&#9679; plexconnect.service - LSB: This is the Plex Connect daemon
   Loaded: loaded (/etc/init.d/plexconnect; bad; vendor preset: enabled)
   Active: active (running) since sø. 2016-03-27 14:31:09 CEST; 1s ago
     Docs: man:systemd-sysv-generator(8)
  Process: 1911 ExecStop=/etc/init.d/plexconnect stop (code=exited, status=0/SUCCESS)
  Process: 1921 ExecStart=/etc/init.d/plexconnect start (code=exited, status=0/SUCCESS)
    Tasks: 6 (limit: 512)
   CGroup: /system.slice/plexconnect.service
           &#9500;&#9472;1930 /usr/bin/SCREEN -S PlexConnect -d -m /usr/local/lib/PlexConnect/PlexConnect.py
           &#9500;&#9472;1933 python /usr/local/lib/PlexConnect/PlexConnect.py
           &#9500;&#9472;1936 python /usr/local/lib/PlexConnect/PlexConnect.py
           &#9500;&#9472;1940 python /usr/local/lib/PlexConnect/PlexConnect.py
           &#9500;&#9472;1942 python /usr/local/lib/PlexConnect/PlexConnect.py
           &#9492;&#9472;1944 python /usr/local/lib/PlexConnect/PlexConnect.py


mars 27 14:31:09 lenox2 systemd[1]: Starting LSB: This is the Plex Connect daemon...
mars 27 14:31:09 lenox2 plexconnect[1921]:  * Starting the process PlexConnect
mars 27 14:31:09 lenox2 systemd[1]: Started LSB: This is the Plex Connect daemon.

```

This was part of the original script:

```
#Required-Start:  networking plexmediaserver
```

Now the Plexmediaserver ubuntu package uses Upstart so this will not work.


I´ve been looking at converting the sysvinit (plexconnect) to an Upstart.conf since Plexmediaserver is an Upstart.conf but i ran in to another issue when trying to add it:

```
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
```

So now i´m even more confused... How could plexmediaplayer get to be an Upstart service if 16.04 does not allow me to update Upstart?

Complete init script:

```
[COLOR=#880000]#!/bin/bash[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]### BEGIN INIT INFO[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Provides:          plexconnect[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Required-Start:    networking[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Required-Stop:     networking[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Default-Start:     3 4 5[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Default-Stop:      0 1 6[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Short-Description: This is the Plex Connect daemon[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]# Description:       This script starts the Plex Connect[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]#                    Python scripts in a detached screen.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#880000]### END INIT INFO[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#880000]# Using the lsb functions to perform the operations.[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#666600].[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]lib[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]lsb[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]init[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]functions

[/COLOR][COLOR=#880000]# Process name ( For display )[/COLOR][COLOR=#000000]
NAME[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#660066]PlexConnect[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#880000]# Daemon name, where is the actual executable[/COLOR][COLOR=#000000]
DAEMON[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"/usr/bin/screen"[/COLOR][COLOR=#000000]
DAEMON_OPTS[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"-S PlexConnect -d -m /usr/local/lib/PlexConnect/PlexConnect.py"[/COLOR][COLOR=#000000]
DAEMON_USER[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"root"[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#880000]# pid file for the daemon[/COLOR][COLOR=#000000]
PIDFILE[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]/var/[/COLOR][COLOR=#000000]run[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#660066]PlexConnect[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]pid

[/COLOR][COLOR=#880000]# If the daemon is not there, then exit.[/COLOR][COLOR=#000000]
test [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]x [/COLOR][COLOR=#008800]"$DAEMON"[/COLOR][COLOR=#666600]||[/COLOR][COLOR=#0000DD]exit[/COLOR][COLOR=#006666]5[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#0000DD]case[/COLOR][COLOR=#000000] $1 [/COLOR][COLOR=#0000DD]in[/COLOR][COLOR=#000000]
 start[/COLOR][COLOR=#666600])[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#880000]# Checked the PID file exists and check the actual status of process[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]if[/COLOR][COLOR=#666600][[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]e $PIDFILE [/COLOR][COLOR=#666600]];[/COLOR][COLOR=#0000DD]then[/COLOR][COLOR=#000000]
   status_of_proc [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]p $PIDFILE [/COLOR][COLOR=#008800]"$DAEMON $DAEMON_OPTS"[/COLOR][COLOR=#008800]"$NAME process"[/COLOR][COLOR=#666600]&&[/COLOR][COLOR=#000000] status[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"0"[/COLOR][COLOR=#666600]||[/COLOR][COLOR=#000000] status[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"$?"[/COLOR][COLOR=#000000]
   [/COLOR][COLOR=#880000]# If the status is SUCCESS then don't need to start again.[/COLOR][COLOR=#000000]
   [/COLOR][COLOR=#0000DD]if[/COLOR][COLOR=#666600][[/COLOR][COLOR=#000000] $[/COLOR][COLOR=#666600]?[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"0"[/COLOR][COLOR=#666600]];[/COLOR][COLOR=#0000DD]then[/COLOR][COLOR=#000000]
    log_success_msg [/COLOR][COLOR=#008800]"Starting the process $NAME"[/COLOR][COLOR=#000000]
    [/COLOR][COLOR=#0000DD]exit[/COLOR][COLOR=#880000]# Exit[/COLOR][COLOR=#000000]
   [/COLOR][COLOR=#0000DD]fi[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]fi[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#880000]# Start the daemon.[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#880000]# Start the daemon with the help of start-stop-daemon[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#880000]# Log the message appropriately[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]if[/COLOR][COLOR=#000000] start[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]stop[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]daemon [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]start [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]quiet [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]oknodo [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]pidfile $PIDFILE [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]startas $DAEMON [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]p $PIDFILE [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000] $[/COLOR][COLOR=#666600]{[/COLOR][COLOR=#000000]DAEMON_OPTS[/COLOR][COLOR=#666600]};[/COLOR][COLOR=#0000DD]then[/COLOR][COLOR=#000000]
   [/COLOR][COLOR=#0000DD]while[/COLOR][COLOR=#000000] read line [/COLOR][COLOR=#666600];[/COLOR][COLOR=#0000DD]do[/COLOR][COLOR=#666600][[[/COLOR][COLOR=#000000] $line [/COLOR][COLOR=#666600]=~[/COLOR][COLOR=#666600]([[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#006666]9[/COLOR][COLOR=#666600]]*).[/COLOR][COLOR=#660066]PlexConnect[/COLOR][COLOR=#666600]]][/COLOR][COLOR=#666600]&&[/COLOR][COLOR=#000000] echo $[/COLOR][COLOR=#666600]{[/COLOR][COLOR=#000000]BASH_REMATCH[/COLOR][COLOR=#666600][[/COLOR][COLOR=#006666]1[/COLOR][COLOR=#666600]]}[/COLOR][COLOR=#666600];[/COLOR][COLOR=#0000DD]done[/COLOR][COLOR=#666600]<[/COLOR][COLOR=#666600]<([/COLOR][COLOR=#000000]screen [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]ls[/COLOR][COLOR=#666600])[/COLOR][COLOR=#666600]>[/COLOR][COLOR=#000000] $PIDFILE
   log_success_msg [/COLOR][COLOR=#008800]"Starting the process $NAME"[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]else[/COLOR][COLOR=#000000]
   log_failure_msg [/COLOR][COLOR=#008800]"Starting the process $NAME"[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]fi[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#666600];;[/COLOR][COLOR=#000000]
 stop[/COLOR][COLOR=#666600])[/COLOR][COLOR=#000000]

  [/COLOR][COLOR=#880000]# Stop the daemon.[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]if[/COLOR][COLOR=#666600][[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]e $PIDFILE [/COLOR][COLOR=#666600]];[/COLOR][COLOR=#0000DD]then[/COLOR][COLOR=#000000]
   status_of_proc [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]p $PIDFILE [/COLOR][COLOR=#008800]"$DAEMON DAEMON_OPTS"[/COLOR][COLOR=#008800]"Stoppping the $NAME process"[/COLOR][COLOR=#666600]&&[/COLOR][COLOR=#000000] status[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"0"[/COLOR][COLOR=#666600]||[/COLOR][COLOR=#000000] status[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]"$?"[/COLOR][COLOR=#000000]
   [/COLOR][COLOR=#0000DD]if[/COLOR][COLOR=#666600][[/COLOR][COLOR=#008800]"$?"[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]];[/COLOR][COLOR=#0000DD]then[/COLOR][COLOR=#000000]
    start[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]stop[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]daemon [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]stop [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]quiet [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]oknodo [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]pidfile $PIDFILE
    [/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]bin[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]rm [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]rf $PIDFILE
    log_success_msg [/COLOR][COLOR=#008800]""[/COLOR][COLOR=#660066]Stopping[/COLOR][COLOR=#000000] the $NAME process[/COLOR][COLOR=#008800]""[/COLOR][COLOR=#000000]
   [/COLOR][COLOR=#0000DD]fi[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]else[/COLOR][COLOR=#000000]
   log_failure_msg [/COLOR][COLOR=#008800]"$NAME process is not running"[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]fi[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#666600];;[/COLOR][COLOR=#000000]
 restart[/COLOR][COLOR=#666600])[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#880000]# Restart the daemon.[/COLOR][COLOR=#000000]
  $0 stop [/COLOR][COLOR=#666600]&&[/COLOR][COLOR=#000000] sleep [/COLOR][COLOR=#006666]2[/COLOR][COLOR=#666600]&&[/COLOR][COLOR=#000000] $0 start
  [/COLOR][COLOR=#666600];;[/COLOR][COLOR=#000000]
 status[/COLOR][COLOR=#666600])[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#880000]# Check the status of the process.[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]if[/COLOR][COLOR=#666600][[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]e $PIDFILE [/COLOR][COLOR=#666600]];[/COLOR][COLOR=#0000DD]then[/COLOR][COLOR=#000000]
   status_of_proc [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]p $PIDFILE [/COLOR][COLOR=#008800]"$DAEMON $DAEMON_OPTS"[/COLOR][COLOR=#008800]"$NAME process"[/COLOR][COLOR=#666600]&&[/COLOR][COLOR=#0000DD]exit[/COLOR][COLOR=#006666]0[/COLOR][COLOR=#666600]||[/COLOR][COLOR=#0000DD]exit[/COLOR][COLOR=#000000] $[/COLOR][COLOR=#666600]?[/COLOR][COLOR=#000000]
   log_success_msg [/COLOR][COLOR=#008800]"$NAME process is running"[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]else[/COLOR][COLOR=#000000]
   log_failure_msg [/COLOR][COLOR=#008800]"$NAME process is not running"[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]fi[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#666600];;[/COLOR][COLOR=#000000]
 reload[/COLOR][COLOR=#666600])[/COLOR][COLOR=#000000]
  $0 restart
  [/COLOR][COLOR=#666600];;[/COLOR][COLOR=#000000]
 [/COLOR][COLOR=#666600]*)[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#880000]# For invalid arguments, print the usage message.[/COLOR][COLOR=#000000]
  echo [/COLOR][COLOR=#008800]"Usage: $0 {start|stop|restart|reload|status}"[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#0000DD]exit[/COLOR][COLOR=#006666]2[/COLOR][COLOR=#000000]
  [/COLOR][COLOR=#666600];;[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#0000DD]esac[/COLOR]
```

---

### Post by izznogooood on 2016-03-29
I'm giving this a bump as I have added lots of information the past days and still have noe answers. Any points in ANY direction would be fine at this moment :)

---

### Post by Bashing-om on 2016-03-29
izznogooood; Hey ...

My experience with systemd is very limited, however, I am aware that upstart and systemd speak different languages.
As well, my bash scripting skills leave a lot to be desired.
See:
[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)
[http://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/](http://www.freedesktop.org/wiki/Software/systemd/NetworkTarget/) <- Running Services After the Network is up
[https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units)

maybe these will point you to a resolution .

[INDENT][INDENT]just a bit of help
[/INDENT][/INDENT]

---

### Post by izznogooood on 2016-03-29
Thank you, I´ll have a look at these links as soon as i have time. I think Im realizing there is no magical solution for this.

---

### Post by izznogooood on 2016-03-30
Turns out you cant run Upstart and Systemd at the same time but both are backwards compatible with sysvinit (/etc/init.d).
The confusing part was Plexmediaserver had both a Upstart file and a Systemd file, but was using systemd as all ubuntu does after 15.

The solution was to make a new Unit file (systemd) for plexconnect and skip sysvinit all together...

New Unit file code:

```
[COLOR=#666600][[/COLOR][COLOR=#660066]Unit[/COLOR][COLOR=#666600]][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]Description[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#660066]Plexconnect[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]After[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]plexmediaserver[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]service

[/COLOR][COLOR=#666600][[/COLOR][COLOR=#660066]Service[/COLOR][COLOR=#666600]][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]Type[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]simple
[/COLOR][COLOR=#660066]ExecStart[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#008800]/usr/[/COLOR][COLOR=#000000]bin[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]python [/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]usr[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#0000DD]local[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#000000]lib[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#660066]PlexConnect[/COLOR][COLOR=#666600]/[/COLOR][COLOR=#660066]PlexConnect[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]py
[/COLOR][COLOR=#660066]User[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]root
[/COLOR][COLOR=#660066]Group[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]root
[/COLOR][COLOR=#660066]Restart[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]on[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]failure
[/COLOR][COLOR=#660066]RestartSec[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]5[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]StartLimitInterval[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]60s[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]StartLimitBurst[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#006666]3[/COLOR][COLOR=#000000]


[/COLOR][COLOR=#666600][[/COLOR][COLOR=#660066]Install[/COLOR][COLOR=#666600]][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#660066]WantedBy[/COLOR][COLOR=#666600]=[/COLOR][COLOR=#000000]multi[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]user[/COLOR][COLOR=#666600].[/COLOR][COLOR=#000000]target[/COLOR]
```

I made a guide here: [http://forums.plex.tv/discussion/213637/howto-install-plexconnect-as-a-service-in-ubuntu-15-or-others-with-systemd#latest](http://forums.plex.tv/discussion/213637/howto-install-plexconnect-as-a-service-in-ubuntu-15-or-others-with-systemd#latest)

---

### Post by Bashing-om on 2016-03-30
izznogooood; Outstanding !

You do good work, appreciate you did provide the proper solution.

open source:
[INDENT][INDENT]help each other along the way
[/INDENT][/INDENT]

---

