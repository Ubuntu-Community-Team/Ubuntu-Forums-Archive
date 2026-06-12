---
title: "Problems setting Up The Plex Media Server On Linux"
date: 2016-04-30
forum: Server Platforms
---

### Post by arpit3 on 2016-04-30
Hello Guys, I'm running the latest version of Ubuntu OS i.e., Ubuntu 16.04 LTS and wanted to run the Plex Media Server so that I can manage all my media stuff with ease. Anyway, I searched for this and found this [guide]("https://techchomps.com/how-to-set-up-the-plex-media-server-on-linux/"). I've downloaded all the prerequisites such as the Plex media package and prepared for its install. But when I try to enable the package with this command: ```
sudo systemctl enable plexmediaserver.service
``` I recieve an error saying that the command is not recognized but when I again enter the same command, it works. Although, when I try to start the service using this command: ```
sudo systemctl4 start plexmediaserver.service
``` it doesn't starts. Can you tell me the possible reason for this? Any help is appreciated. Thanks.

---

### Post by nerdtron on 2016-04-30
Hello,

Did you installed the .deb successfully? did you not encountered an error?

And
Is that a typo on systemctl start?
To start the service:
```
 sudo systemctl start plexmediaserver.service 
```

Check the status if it's running or not:
```
sudo systemctl status plexmediaserver.service 
ps -ef | grep [plex]
```

Post the full output of your terminal here.

---

### Post by pjdw on 2017-02-12
```
 plexmediaserver.service - Plex Media Server for Linux
   Loaded: loaded (/etc/systemd/system/plexmediaserver.service; enabled; vendor preset: enabled)
   Active: inactive (dead) (Result: exit-code) since zo 2017-02-12 12:38:41 CET; 5min ago
  Process: 2844 ExecStart=/bin/sh -c /usr/lib/plexmediaserver/Plex\ Media\ Server (code=exited, status=134)
  Process: 2840 ExecStartPre=/bin/sh -c /usr/bin/test -d "${PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR}" || /bin/
 Main PID: 2844 (code=exited, status=134)


feb 12 12:38:36 UbM systemd[1]: plexmediaserver.service: Unit entered failed state.
feb 12 12:38:36 UbM systemd[1]: plexmediaserver.service: Failed with result 'exit-code'.
feb 12 12:38:41 UbM systemd[1]: plexmediaserver.service: Service hold-off time over, scheduling restart.
feb 12 12:38:41 UbM systemd[1]: Stopped Plex Media Server for Linux.
feb 12 12:38:41 UbM systemd[1]: plexmediaserver.service: Start request repeated too quickly.
feb 12 12:38:41 UbM systemd[1]: Failed to start Plex Media Server for Linux.
feb 12 12:39:02 UbM systemd[1]: Stopped Plex Media Server for Linux.
feb 12 12:39:02 UbM systemd[1]: plexmediaserver.service: Start request repeated too quickly.
feb 12 12:39:02 UbM systemd[1]: Failed to start Plex Media Server for Linux.
```

I did not saw a reply, so i pasted my failures ;)
Edit: it was a user issue. 

```
 plexmediaserver.service - Plex Media Server for Linux
   Loaded: loaded (/etc/systemd/system/plexmediaserver.service; enabled; vendor 
   Active: active (running) since zo 2017-02-12 12:54:45 CET; 2min 14s ago
  Process: 3026 ExecStartPre=/bin/sh -c /usr/bin/test -d "${PLEX_MEDIA_SERVER_AP
 Main PID: 3030 (sh)
   CGroup: /system.slice/plexmediaserver.service
           &#9500;&#9472;3030 /bin/sh -c /usr/lib/plexmediaserver/Plex\ Media\ Server
           &#9500;&#9472;3033 /usr/lib/plexmediaserver/Plex Media Server
           &#9500;&#9472;3043 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Res
           &#9500;&#9472;3094 Plex Plug-in [com.plexapp.agents.imdb] /usr/lib/plexmediaserve
           &#9492;&#9472;3097 /usr/lib/plexmediaserver/Plex DLNA Server


feb 12 12:54:45 UbM systemd[1]: Starting Plex Media Server for Linux...
feb 12 12:54:45 UbM systemd[1]: Started Plex Media Server for Linux.
lines 1-14/14 (END)
```

This looks better after

---

