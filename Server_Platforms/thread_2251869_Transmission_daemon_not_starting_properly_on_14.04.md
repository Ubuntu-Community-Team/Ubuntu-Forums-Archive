---
title: "Transmission daemon not starting properly on 14.04"
date: 2014-11-07
forum: Server Platforms
---

### Post by zeroburn on 2014-11-07
Hello all, 

ever since I upgraded my server install from 12.04 to 14.04 I had this problem with transmission-daemon reporting a successful start on boot:

Transmission 2.84 (14307)

From PPA:

deb [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) trusty main
deb-src [http://ppa.launchpad.net/transmissionbt/ppa/ubuntu](http://ppa.launchpad.net/transmissionbt/ppa/ubuntu) trusty main

 /var/log/upstart/transmission-daemon.log: 
```

[2014-11-07 13:02:58.300 CET] RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1033)
[2014-11-07 13:02:58.300 CET] Using settings from "/var/lib/transmission-daemon/info" (daemon.c:557)
[2014-11-07 13:02:58.300 CET] Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
[2014-11-07 13:02:58.300 CET] transmission-daemon requiring authentication (daemon.c:577)
[2014-11-07 14:31:10.392 CET] Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
Closing transmission session... done.
[2014-11-07 14:31:11.705 CET] RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1033)
[2014-11-07 14:31:11.705 CET] Using settings from "/var/lib/transmission-daemon/info" (daemon.c:557)
[2014-11-07 14:31:11.705 CET] Saved "/etc/transmission-daemon/settings.json" (variant.c:1214)
[2014-11-07 14:31:11.705 CET] transmission-daemon requiring authentication (daemon.c:577)
[2014-11-07 14:31:30.704 CET] Searching for web interface file "/home/debian-transmission/.local/share/transmission/web/index.html" (platform.c:405)
[2014-11-07 14:31:30.705 CET] Searching for web interface file "/usr/share/transmission/web/index.html" (platform.c:405)

```

but it's not responding to any requests from either the web-ui nor the transmission-gui on my clients. If I manually restart the service after boot (service transmission-daemon restart) all is fine. The first part of the log before the session closing is what started at boot, the second part is after a manual service restart + attempt to enter the web gui. 

This is my settings.json file:

```

{
    "alt-speed-down": 20,
    "alt-speed-enabled": false,
    "alt-speed-time-begin": 540,
    "alt-speed-time-day": 127,
    "alt-speed-time-enabled": false,
    "alt-speed-time-end": 1020,
    "alt-speed-up": 5,
    "bind-address-ipv4": "192.168.69.3",
    "bind-address-ipv6": "::",
    "blocklist-enabled": true,
    "blocklist-url": "http://list.iblocklist.com/?list=bt_level1&fileformat=p2p&archiveformat=",
    "cache-size-mb": 4,
    "dht-enabled": true,
    "download-dir": "/var/lib/transmission-daemon/downloads",
    "download-limit": 100,
    "download-limit-enabled": 0,
    "download-queue-enabled": true,
    "download-queue-size": 1,
    "encryption": 2,
    "idle-seeding-limit": 30,
    "idle-seeding-limit-enabled": false,
    "incomplete-dir": "/root/Downloads",
    "incomplete-dir-enabled": false,
    "lpd-enabled": false,
    "max-peers-global": 400,
    "message-level": 2,
    "peer-congestion-algorithm": "",
    "peer-id-ttl-hours": 6,
    "peer-limit-global": 400,
    "peer-limit-per-torrent": 400,
    "peer-port": 51413,
    "peer-port-random-high": 65535,
    "peer-port-random-low": 49152,
    "peer-port-random-on-start": false,
    "peer-socket-tos": "default",
    "pex-enabled": true,
    "port-forwarding-enabled": false,
    "preallocation": 1,
    "prefetch-enabled": 1,
    "queue-stalled-enabled": true,
    "queue-stalled-minutes": 30,
    "ratio-limit": 2.5,
    "ratio-limit-enabled": true,
    "rename-partial-files": true,
    "rpc-authentication-required": true,
    "rpc-bind-address": "192.168.69.3",
    "rpc-enabled": true,
    "rpc-password": "*********************************************",
    "rpc-port": 9091,
    "rpc-url": "/transmission/",
    "rpc-username": "transmission",
    "rpc-whitelist": "192.168.69.*,192.168.70.*",
    "rpc-whitelist-enabled": true,
    "scrape-paused-torrents-enabled": true,
    "script-torrent-done-enabled": false,
    "script-torrent-done-filename": "",
    "seed-queue-enabled": false,
    "seed-queue-size": 10,
    "speed-limit-down": 100,
    "speed-limit-down-enabled": false,
    "speed-limit-up": 20,
    "speed-limit-up-enabled": true,
    "start-added-torrents": true,
    "trash-original-torrent-files": false,
    "umask": 18,
    "upload-limit": 100,
    "upload-limit-enabled": 0,
    "upload-slots-per-torrent": 14,
    "utp-enabled": false
}

```

This is mildly annoying. Has anyone had this issue and found a solution?

Thanks.

---

### Post by ian-weisser on 2014-11-07
My version of Transmission from the 14.10 Ubuntu repositories starts properly.

What method are you using to automatically start your PPA version of Transmission at boot?
An Upstart job? An init script? Something you wrote yourself?
Have you contacted the PPA maintainers to see if anyone else using their version has a similar issue?

---

### Post by zeroburn on 2014-11-10
Using the default UPSTART script that comes with the packages. I even tried to purge and go for the 2.82 version in the ubuntu repo, but it shows identical issues.

---

### Post by ian-weisser on 2014-11-10
Reporting aside, *is* transmission-demon actually running at boot? Is torrent activity going on before you restart the apparently unresponsive service?

If not, then you might have a problem with the daemon itself. Though, honestly, that seems unlikely or it would affect _everyone_.
If so, then you may just have a problem with the rpc server.

Other thoughts, admittedly grasping at straws:

- Check netstat to see if the rpc server has bound to a port.

- Try disabling rpc authentication and see if that makes a difference.

---

### Post by zeroburn on 2014-11-11
Those are very good ideas that I didn't think of (checking netstat to see if it binds the port AND to check if torrents actually start on boot). The only thing I am sure of is that the process is up after boot, just the RPC doesn't connect.

Will post back after some testing!

---

### Post by zeroburn on 2014-11-11
Nothing's moving at boot until I restart the service, even if there are torrents in the queue, the only thing listed is:

```

udp        0      0 0.0.0.0:56247           0.0.0.0:*                           576/transmission-da

```

compared to the situation after a manual service restart:

```

tcp        0      0 server.name.home:51413  *:*                     LISTEN      1845/transmission-d
tcp        0      0 server.name.home:9091    *:*                     LISTEN      1845/transmission-d
several other connections to peers/seeds

```

---

### Post by roald2 on 2015-01-01
> **zeroburn said:**
> Nothing's moving at boot until I restart the service, even if there are torrents in the queue, the only thing listed is:

```

udp        0      0 0.0.0.0:56247           0.0.0.0:*                           576/transmission-da

```

compared to the situation after a manual service restart:

```

tcp        0      0 server.name.home:51413  *:*                     LISTEN      1845/transmission-d
tcp        0      0 server.name.home:9091    *:*                     LISTEN      1845/transmission-d
several other connections to peers/seeds

```
Hello zeroburn,

I wonder, have you managed to get this working? I'm setting up a new installation of Transmission Daemon and I too have this behaviour of Transmission not starting properly after a reboot of Ubuntu 14.04.1 LTS. Although a simple restart of the service solves this problem, I'm not quite happy with it.

If you have any solutions, please let me know.!

Regards,
Roald

---

### Post by iagathodaemon on 2015-05-01
I solved this problem. 
Open /etc/init/transmissiom-daemon.conf and replace
```
start on (filesystem and net-device-up IFACE**=**lo)
```
to
```
start on (filesystem and net-device-up IFACE**!=**lo)
```

---

