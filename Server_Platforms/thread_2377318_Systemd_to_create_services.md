---
title: "Systemd to create services"
date: 2017-11-11
forum: Server Platforms
---

### Post by dam034 on 2017-11-11
Dear users,

I have a VPS with ubuntu server 16.04, I want to use systemd (as adviced in a previous topic) to run programs on my server.

I have many programs to run automatically at system startup, for example:
```
root@srvesp:~# mediatomb

MediaTomb UPnP Server version 0.12.2 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2010 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2017-11-11 22:56:16    INFO: Loading configuration from: /root/.mediatomb/config.xml
2017-11-11 22:56:16    INFO: Checking configuration...
2017-11-11 22:56:16    INFO: Setting filesystem import charset to UTF-8
2017-11-11 22:56:16    INFO: Setting metadata import charset to UTF-8
2017-11-11 22:56:16    INFO: Setting playlist charset to UTF-8
2017-11-11 22:56:16 WARNING: You enabled the YouTube feature, which allows you
                             to watch YouTube videos on your UPnP device!
                             Please check http://www.youtube.com/t/terms
                             By using this feature you may be violating YouTube
                             service terms and conditions!

2017-11-11 22:56:16    INFO: Configuration check succeeded.
2017-11-11 22:56:16    INFO: Initialized port: 49153
2017-11-11 22:56:16    INFO: Server bound to: 172.31.6.125
2017-11-11 22:56:17    INFO: MediaTomb Web UI can be reached by following this link:
2017-11-11 22:56:17    INFO: http://172.31.6.125:49153/
^C2017-11-11 22:57:38    INFO: MediaTomb shutting down. Please wait...
2017-11-11 22:57:38    INFO: Server terminating
root@srvesp:~#

```
This is mediatomb DLNA server, here you can see I ended the program by pressing CTRL-C.

Another example below:
```
root@srvesp:/srv/mtasa#./mta-server
MTA:BLUE Server for MTA:SA

Please wait...
==================================================================
= Multi Theft Auto: San Andreas v1.5.4
==================================================================
= Server name      : LAN MTA Test
= Server IP address: auto
= Server port      : 22003
=
= Log file         : /srv/mtasa/mods/deathmatch/logs/server.log
= Maximum players  : 20
= HTTP port        : 22005
= Voice Chat       : Disabled
= Bandwidth saving : None
==================================================================
[23:00:21] Compacting accounts database 'internal.db' ...
[23:00:29] Resources: 220 loaded, 0 failed
[23:00:29] Compacting database 'registry.db' ...
[23:00:29] Starting resources...
[23:00:30] Server minclientversion is now 1.3.0-9.04311
[23:00:30] Server minclientversion is now 1.3.3-9.04997
[23:00:30] Gamemode 'play' started.
[23:00:30] Authorized serial account protection is enabled for the ACL group(s):
 `Admin`  See http://mtasa.com/authserial
[23:00:30] Server started and is ready to accept connections!
[23:00:30] To stop the server, type 'shutdown' or press Ctrl-C
[23:00:30] Type 'help' for a list of commands.
start myres
[23:03:09] start: Requested by Console
[23:03:09] Starting myres
[23:03:10] Mysql connesso
[23:03:10] start: Resource 'myres' started
refreshall
```
This is Multi Theft Auto San Andreas server, and here you can see I have to leave the program *opened* because I executed two commands in the program ("start myres" and "refreshall"). But if I press CTRL-C the server will shut down, if I not press CTRL-C I can't use the console for other commands. Not to mention the connection, if I run the programs in the server directly is a thing, but if the server is remote, I need to leave open my console with PC and internet connection turned on.

Now, I know there is systemd which can fix my issues, and I found this [https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers) but I never used upstart, then I need to start from scratch.

What I need is:
[LIST]
[*]run those commands at system startup
[*]leave those commands opened
[*]execute some commands in the programs (like "start myres")
[*]close/restart the programs
[/LIST]

Someone can help me?

Thanks

---

### Post by TheFu on 2017-11-12
Why not just detach them from the console at start up?  This is very basic Unix knowledge. Job control is one of the first things I was taught in my "Learning Unix" class.  Any book on the subject will show you how.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is one. Free, no-hassle, download.  Ref Chpt 10.
```

$ /srv/mtasa/mta-server &
```

You might want to check out chpt 6 - about redirecting output from programs so your screen doesn't get interrupted.  Of course, you can open 10 terminals into the VPS over ssh. Each one would have the program output only for the programs running inside that connection, inside that window.

BTW, running services like these as root isn't usually safe.  Generally, it is considered a bad idea.  In fact, outside of a VPS, Ubuntu doesn't actually allow access to the root account, and certainly not from a remote connection.  Only sudo is allowed to run programs with temporarily elevated permissions.

Not sure how running a DLNA server on a VPS is useful.  DLNA is limited to LAN clients - doesn't work over the internet.  Sure, you CAN do it, but why? It isn't like you can access media from home on the VPS running DLNA clients.  You can use different protocols to access the media, just not DLNA.

There are help/guides for systemd config files. The one you found is the only one I know, but I've never looked. I would follow an example  already on the system and only if that failed, look for more info at the systemd support website.  On your system today, there are examples already.  These are in /etc/systemd/  6+ examples there from the base installation on my box. The files end in '.service', if that helps.

Or you can follow the old-school init script methods.  Those use normal bash scripts that have start/stop/restart/reload/status as options.  Init worked for 40+ yrs, to it isn't like everyone switched those scripts over the day systemd was released.  They will still work.  There are hundreds of thousands of examples of those.  The fast solution is sometimes the best solution, right?

---

### Post by LHammonds on 2017-11-12
> **TheFu said:**
> [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is one. Free, no-hassle, download.
Thanks for the link.

I wonder if there is an existing list of links to all the freely available ebooks about Linux/Ubuntu.

LHammonds

---

### Post by Tadaen_Sylvermane on 2017-11-12
I'm gonna give you the systemd service I use to autostart Kodi on my htpc. I don't have to do anything. It boots directly to Kodi on a bare Ubuntu Server installation. Should give you some ideas.

```
[Unit]
Description = Kodi Media Center
After = systemd-user-sessions.service network.target sound.target mysql.service
Wants = mysql.service

[Service]
User = kodimain
Group = kodimain
Type = simple
ExecStart = /usr/bin/xinit /usr/bin/dbus-launch --exit-with-session /usr/bin/kodi-standalone -- :0 -nolisten tcp vt7
Restart = always
RestartSec = 5

[Install]
WantedBy = multi-user.target
```

This autostarts Kodi on boot. You can adjust to launch anything you want really.

---

### Post by dam034 on 2017-11-12
So, if I understood good, it will be:
```
[Unit]
Description = Multi Theft Auto San Andreas
After = systemd-user-sessions.service network.target sound.target mysql.service
Wants = mysql.service

[Service]
User = mtasa
Group = myadmingroup
Type = simple
ExecStart = /srv/mtasa/mta-server
Restart = always
RestartSec = 5

[Install]
WantedBy = multi-user.target
```
I use mysql in MTA server to store some players' data.

So, I can't understand what "After" means in this code, and I want to know how can I operate in the server once I launched it.


Thanks

---

### Post by Tadaen_Sylvermane on 2017-11-13
If you will need to interact with it then another approach may be necessary. I use a script that uses screen for my minecraft servers. To launch them on boot they have an @reboot in the crontab of the appropriate user. I can do whatever through the created screen session.

---

### Post by dam034 on 2017-11-13
> **Tadaen_Sylvermane said:**
> If you will need to interact with it then another approach may be necessary. I use a script that uses screen for my minecraft servers. To launch them on boot they have an @reboot in the crontab of the appropriate user. I can do whatever through the created screen session.

Can you give me an example? Also what you do with your minecraft servers.


Thanks

---

### Post by Tadaen_Sylvermane on 2017-11-13
```
screen -dmS ${1} java -XX:ParallelGCThreads=2 -jar ${EXEDIRECTORY}/${CURRENTSERVERJAR} nogui
```

this starts the server for example. the script is alot more involved but this is the part you probably need. Throw this on an @reboot crontab on the proper user and you are set.

---

