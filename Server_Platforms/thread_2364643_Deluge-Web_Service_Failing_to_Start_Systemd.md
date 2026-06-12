---
title: "Deluge-Web Service Failing to Start: Systemd"
date: 2017-06-26
forum: Server Platforms
---

### Post by linderrex on 2017-06-26
I am trying to install Deluge on my Ubuntu 17.04 server and run the web service daemon using [this guide.]("http://dev.deluge-torrent.org/wiki/UserGuide/Service/systemd") I have no problems with the deluged section. But when I try to set up deluge-web I cannot get the service to start.


Here is my deluge-web.service file. It is located in the /etc/systemd/system/deluge-web.service directory:
```
[Unit]
Description=Deluge Bittorrent Client Web Interface
Documentation=man:deluge-web
After=network-online.target deluged.service
Wants=deluged.service
[Service]
Type=simple
User=deluge
Group=deluge
UMask=027
ExecStart=/usr/bin/deluge-web -d
Restart=on-failure
[Install]
WantedBy=multi-user.target

```

I can run *sudo systemctl enable /etc/systemd/system/deluge-web.service* and *sudo systemctl start deluge-web* but when I run *sudo systemctl status deluge-web* I get the following message:


```
******@********:/etc/systemd/system$ sudo systemctl status deluge-web
&#9679; deluge-web.service - Deluge Bittorrent Client Web Interface
   Loaded: loaded (/etc/systemd/system/deluge-web.service; enabled; vendor 
preset: enabled)
   Active: failed (Result: exit-code) since Sun 2017-06-25 22:32:17 MDT; 3s 
ago
     Docs: man:deluge-web
  Process: 6520 ExecStart=/usr/bin/deluge-web -d (code=exited, status=2)
 Main PID: 6520 (code=exited, status=2)


Hun 25 22:32:17 ******** systemd[1]: deluge-web.service: Failed with result 
'exit-code'.
Hun 25 22:32:17 ******** systemd[1]: deluge-web.service: Service hold-off 
time over, scheduling restart.
Hun 25 22:32:17 ******** systemd[1]: Stopped Deluge Bittorrent Client Web 
Interface.
Hun 25 22:32:17 ******** systemd[1]: deluge-web.service: Start request 
repeated too quickly.
Hun 25 22:32:17 ******** systemd[1]: Failed to start Deluge Bittorrent 
Client Web Interface.
Hun 25 22:32:17 ******** systemd[1]: deluge-web.service: Unit entered failed 
state.
Hun 25 22:32:17 ******** systemd[1]: deluge-web.service: Failed with result 
'exit-code'.



```How can I get the deluge-web daemon to start without failing?

---

### Post by wildmanne39 on 2017-06-26
*Thread moved to **Server Platforms**.*

---

