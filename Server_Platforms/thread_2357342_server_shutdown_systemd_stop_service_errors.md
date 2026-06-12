---
title: "server shutdown: systemd stop service errors"
date: 2017-04-01
forum: Server Platforms
---

### Post by homeless.gamer on 2017-04-01
Hi, 
recently i reinstalled my ubuntu 16 LTS server. Now i have to use systemd, too, cause /etc/init.d's update-rc.d does not support ordered service starting anymore. back in the days without systemd, all my scripts just worked fine :(

My Problem:
i can start and stop all services manually using systemctl start/stop ttt.service. the ttt.service launcherscript terminates shortly after its launch was initialized, when stopping, it terminates after the ttt.service was fully stopped. by enabling ttt.service and myscreen.service everything starts just fine after a reboot, but the shutdown looks kinda ****ed up. **but why does it act diffrent on shutdown/manual stop? **and systemd doent seem to like people who care about their shutdown stuff. 

Here is a journalctl output of a manual & successful shutdown:
```
p@HP-2017:/etc/systemd/system$ journalctl -b -1 -e -u ttt.service

-- Logs begin at Fri 2017-03-31 10:29:17 CEST, end at Fri 2017-03-31 12:25:51 CEST. --
Mar 31 10:45:25 HP-2017 systemd[1]: Starting garrys mod in ttt mode...
Mar 31 10:45:25 HP-2017 sh[1480]: starting...
Mar 31 10:45:25 HP-2017 sh[1480]: spawn screen -x gaben/steam
Mar 31 10:45:29 HP-2017 sh[1480]: [492B blob data]
Mar 31 10:45:29 HP-2017 sh[1480]:  === starting server ===
Mar 31 10:45:29 HP-2017 sh[1480]: gaben@HP-2017:/$ echo ' ===> dont give keyboard input!'
Mar 31 10:45:29 HP-2017 sh[1480]:  ===> dont give keyboard input!
Mar 31 10:45:29 HP-2017 sh[1480]: gaben@HP-2017:/$
Mar 31 10:45:29 HP-2017 sh[1480]: gaben@HP-2017:/$ cd /home/gaben/garrysMod
Mar 31 10:45:29 HP-2017 sh[1480]: [233B blob data]
Mar 31 10:45:29 HP-2017 sh[1480]: Auto detecting CPU
Mar 31 10:45:29 HP-2017 sh[1480]: Using default binary: ./srcds_linux
Mar 31 10:45:29 HP-2017 sh[1480]: Server will auto-restart if there is a crash.
Mar 31 10:45:29 HP-2017 sh[1480]: WARNING: Failed to load 32-bit libtinfo.so.5 or libncurses.so.5.
Mar 31 10:45:29 HP-2017 sh[1480]:   Please install (lib32tinfo5 / ncurses-libs.i686 / equivalent) to enable readline.
Mar 31 10:45:29 HP-2017 systemd[1]: Started garrys mod in ttt mode.
Mar 31 10:45:29 HP-2017 sh[1480]: TERM environment variable not set.
Mar 31 10:45:29 HP-2017 sh[1480]: startup of gaben has been initialized.
Mar 31 11:06:58 HP-2017 systemd[1]: Stopping garrys mod in ttt mode...
Mar 31 11:06:58 HP-2017 sh[2755]: stopping...
Mar 31 11:06:58 HP-2017 sh[2755]: spawn screen -x gaben/steam
Mar 31 11:06:58 HP-2017 sh[2755]: There is no screen to be attached matching steam.
Mar 31 11:06:58 HP-2017 sh[2755]: send: spawn id exp3 not open
Mar 31 11:06:58 HP-2017 sh[2755]:     while executing
Mar 31 11:06:58 HP-2017 sh[2755]: "send "\x01\x32""
Mar 31 11:06:58 HP-2017 sh[2755]: TERM environment variable not set.
Mar 31 11:06:58 HP-2017 sh[2755]: server is now stopped
Mar 31 11:06:58 HP-2017 echo[2891]: tttStopped >> /root/tttlog
Mar 31 11:06:58 HP-2017 systemd[1]: Stopped garrys mod in ttt mode.
```

and here is what i get if the service gets stopped by a reboot:

```
p@HP-2017:/etc/systemd/system$ journalctl -b -1 -e -u ttt.service

-- Logs begin at Fri 2017-03-31 10:29:17 CEST, end at Fri 2017-03-31 12:25:51 CEST. --
Mar 31 10:45:25 HP-2017 systemd[1]: Starting garrys mod in ttt mode...
Mar 31 10:45:25 HP-2017 sh[1480]: starting...
Mar 31 10:45:25 HP-2017 sh[1480]: spawn screen -x gaben/steam
Mar 31 10:45:29 HP-2017 sh[1480]: [492B blob data]
Mar 31 10:45:29 HP-2017 sh[1480]:  === starting server ===
Mar 31 10:45:29 HP-2017 sh[1480]: gaben@HP-2017:/$ echo ' ===> dont give keyboard input!'
Mar 31 10:45:29 HP-2017 sh[1480]:  ===> dont give keyboard input!
Mar 31 10:45:29 HP-2017 sh[1480]: gaben@HP-2017:/$
Mar 31 10:45:29 HP-2017 sh[1480]: gaben@HP-2017:/$ cd /home/gaben/garrysMod
Mar 31 10:45:29 HP-2017 sh[1480]: [233B blob data]
Mar 31 10:45:29 HP-2017 sh[1480]: Auto detecting CPU
Mar 31 10:45:29 HP-2017 sh[1480]: Using default binary: ./srcds_linux
Mar 31 10:45:29 HP-2017 sh[1480]: Server will auto-restart if there is a crash.
Mar 31 10:45:29 HP-2017 sh[1480]: WARNING: Failed to load 32-bit libtinfo.so.5 or libncurses.so.5.
Mar 31 10:45:29 HP-2017 sh[1480]:   Please install (lib32tinfo5 / ncurses-libs.i686 / equivalent) to enable readline.
Mar 31 10:45:29 HP-2017 systemd[1]: Started garrys mod in ttt mode.
Mar 31 10:45:29 HP-2017 sh[1480]: TERM environment variable not set.
Mar 31 10:45:29 HP-2017 sh[1480]: startup of gaben has been initialized.
Mar 31 11:06:58 HP-2017 systemd[1]: Stopping garrys mod in ttt mode...
Mar 31 11:06:58 HP-2017 sh[2755]: stopping...
Mar 31 11:06:58 HP-2017 sh[2755]: spawn screen -x gaben/steam
Mar 31 11:06:58 HP-2017 sh[2755]: There is no screen to be attached matching steam.
Mar 31 11:06:58 HP-2017 sh[2755]: send: spawn id exp3 not open
Mar 31 11:06:58 HP-2017 sh[2755]:     while executing
Mar 31 11:06:58 HP-2017 sh[2755]: "send "\x01\x32""
Mar 31 11:06:58 HP-2017 sh[2755]: TERM environment variable not set.
Mar 31 11:06:58 HP-2017 sh[2755]: server is now stopped
Mar 31 11:06:58 HP-2017 echo[2891]: tttStopped >> /root/tttlog
Mar 31 11:06:58 HP-2017 systemd[1]: Stopped garrys mod in ttt mode.
```

What this all should do:

i'm booting:
[LIST=1]
[*]using 'su gaben -c "screen -dmS steam"' some screens are started for the user gaben 
[*]network connection gotta be up cause some gameservers need this to be able to start 
[*]using a expect script the launcher.sh connects to the screen and starts the gameserver which is represented by ttt.service 
[*]now i can log in using ssh and can do stuff in the gameserver console if i connect to the screen *thumbsup* 
[/LIST]
now i wanna reboot:
[LIST=1]
[*]the expect-script connects to the screen and sends the gameserver-console-cmd for shutting down the server. after the gameserver finished stopping, the expect script terminates 
[*]now screens may get cleaned up if they want to (/etc/init.d/screen-cleanup) 
[*]network connection may close now 
[*]i've done my stuff. server is allowed to reboot now. 
[/LIST]

to achieve this, i've done the following:

a service to start the screens:
```
p@HP-2017:/etc/systemd/system$ cat myscreens.service
[Unit]
Description=starts myscreens

[Service]
Type=oneshot
ExecStart=/bin/sh -c "/root/myscreens_start.sh"
RemainAfterExit=yes

[Install]
WantedBy=multi-user.target
p@HP-2017:/etc/systemd/system$ systemctl status myscreens.service
&#9679; myscreens.service - starts myscreens
   Loaded: loaded (/etc/systemd/system/myscreens.service; enabled; vendor preset: enabled)
   Active: active (exited) since Fri 2017-03-31 11:09:12 CEST; 1h 6min ago
  Process: 1072 ExecStart=/bin/sh -c /root/myscreens_start.sh (code=exited, status=0/SUCCESS)
 Main PID: 1072 (code=exited, status=0/SUCCESS)
    Tasks: 0
   Memory: 0B
      CPU: 0
   CGroup: /system.slice/myscreens.service

Mar 31 11:09:12 HP-2017 su[1424]: Successful su for minecraft by root
Mar 31 11:09:12 HP-2017 su[1424]: + ??? root:minecraft
Mar 31 11:09:12 HP-2017 su[1424]: pam_unix(su:session): session opened for user minecraft by (uid=0)
Mar 31 11:09:12 HP-2017 su[1435]: Successful su for gaben by root
Mar 31 11:09:12 HP-2017 su[1435]: + ??? root:gaben
Mar 31 11:09:12 HP-2017 su[1435]: pam_unix(su:session): session opened for user gaben by (uid=0)
Mar 31 11:09:12 HP-2017 su[1488]: Successful su for gaben by root
Mar 31 11:09:12 HP-2017 su[1488]: + ??? root:gaben
Mar 31 11:09:12 HP-2017 su[1488]: pam_unix(su:session): session opened for user gaben by (uid=0)
Mar 31 11:09:12 HP-2017 systemd[1]: Started starts myscreens.
p@HP-2017:/etc/systemd/system$
```

... and one to start the gameserver:
```
p@HP-2017:/etc/systemd/system$ cat ttt.service
[Unit]
Description=garrys mod in ttt mode
After=myscreens.service network.target screen-cleanup.service
Requires=myscreens.service network.target screen-cleanup.service
Conflicts=garrysModUpdater.service

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/bin/sh -c "/home/gaben/garrysMod/launcher.sh start_ttt"
ExecStop=-/bin/sh -c "/home/gaben/garrysMod/launcher.sh stop" ; /bin/echo tttStopped >> /root/tttlog

[Install]
WantedBy=multi-user.target
p@HP-2017:/etc/systemd/system$ systemctl status ttt.service
&#9679; ttt.service - garrys mod in ttt mode
   Loaded: loaded (/etc/systemd/system/ttt.service; enabled; vendor preset: enabled)
   Active: active (exited) since Fri 2017-03-31 11:09:16 CEST; 1h 9min ago
  Process: 1515 ExecStart=/bin/sh -c /home/gaben/garrysMod/launcher.sh start_ttt (code=exited, status=0/SUCCESS)
 Main PID: 1515 (code=exited, status=0/SUCCESS)
    Tasks: 0
   Memory: 0B
      CPU: 0
   CGroup: /system.slice/ttt.service

Mar 31 11:09:12 HP-2017 sh[1515]: spawn screen -x gaben/steam
Mar 31 11:09:14 HP-2017 sh[1515]: [440B blob data]
Mar 31 11:09:14 HP-2017 sh[1515]: echo ' ===> dont give keyboard input!'
Mar 31 11:09:14 HP-2017 sh[1515]: gaben@HP-2017:/$ echo ' === starting server === '
Mar 31 11:09:14 HP-2017 sh[1515]:  === starting server ===
Mar 31 11:09:14 HP-2017 sh[1515]: gaben@HP-2017:/$ echo ' ===> dont give keyboard input!'
Mar 31 11:09:14 HP-2017 sh[1515]:  ===> dont give keyboard input!
Mar 31 11:09:16 HP-2017 sh[1515]: gaben@HP-2017:/$ TERM environment variable not set.
Mar 31 11:09:16 HP-2017 sh[1515]: startup of gaben has been initialized.
Mar 31 11:09:16 HP-2017 systemd[1]: Started garrys mod in ttt mode.
```

---

