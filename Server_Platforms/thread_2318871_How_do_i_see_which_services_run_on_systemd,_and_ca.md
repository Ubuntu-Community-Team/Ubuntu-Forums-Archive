---
title: "How do i see which services run on systemd, and can i create a new update.conf"
date: 2016-03-30
forum: Server Platforms
---

### Post by izznogooood on 2016-03-30
My basic problem is this:

I have an sysvinit script thats dependent on an Upstart script. As sysvinit and Upstart does not communicate so the sysvinit service needs a restart after boot.

My plan was to convert the sysvinit script into an Update.conf but since 15.04 Ubuntu now uses systemd and wont allow me to update upstarts. How could the .deb package make a new upstart when i cant? Am i missing something?.

I also want to know how to see all systemd services (To make sure there's not a duplicate service).

If i try to update upstart:

```
initctl: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
```

---

### Post by izznogooood on 2016-03-30
When doing a service status you can see the Loaded: part points to the location of the service and thus see which handler:


```
anders@lenox2:~$ systemctl status plexconnect.service 
&#9679; plexconnect.service - LSB: This is the Plex Connect daemon
   [COLOR=#ff0000]Loaded: loaded (/etc/init.d/plexconnect[/COLOR]; bad; vendor preset: enabled)
   Active: active (running) since on. 2016-03-30 02:33:45 CEST; 13h ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2609 ExecStop=/etc/init.d/plexconnect stop (code=exited, status=0/SUCCESS)
  Process: 2619 ExecStart=/etc/init.d/plexconnect start (code=exited, status=0/SUCCESS)
    Tasks: 6 (limit: 512)
   CGroup: /system.slice/plexconnect.service
           &#9500;&#9472;2628 /usr/bin/SCREEN -S PlexConnect -d -m /usr/local/lib/PlexConnect/PlexConnect.py
           &#9500;&#9472;2631 python /usr/local/lib/PlexConnect/PlexConnect.py
           &#9500;&#9472;2634 python /usr/local/lib/PlexConnect/PlexConnect.py
           &#9500;&#9472;2638 python /usr/local/lib/PlexConnect/PlexConnect.py
           &#9500;&#9472;2640 python /usr/local/lib/PlexConnect/PlexConnect.py
           &#9492;&#9472;2642 python /usr/local/lib/PlexConnect/PlexConnect.py


mars 30 02:33:45 lenox2 systemd[1]: Starting LSB: This is the Plex Connect daemon...
mars 30 02:33:45 lenox2 plexconnect[2619]:  * Starting the process PlexConnect
mars 30 02:33:45 lenox2 systemd[1]: Started LSB: This is the Plex Connect daemon.
anders@lenox2:~$ systemctl status plexmediaserver.service 
&#9679; plexmediaserver.service - Plex Media Server for Linux
   [COLOR=#ff0000]Loaded: loaded (/etc/systemd/system/plexmediaserver.service[/COLOR]; enabled; vendor preset: enabled)
   Active: active (running) since on. 2016-03-30 02:32:43 CEST; 13h ago
  Process: 1107 ExecStartPre=/bin/sh -c /usr/bin/test -d "${PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR}" || /bin/mkdir -p "${PLEX_MEDIA_SERVER_APPLICATION_SUPPORT_DIR}" (code=exited, status=0/SUCCESS)
 Main PID: 1122 (sh)
    Tasks: 43 (limit: 512)
   CGroup: /system.slice/plexmediaserver.service
           &#9500;&#9472;1122 /bin/sh -c /usr/lib/plexmediaserver/Plex\ Media\ Server
           &#9500;&#9472;1127 /usr/lib/plexmediaserver/Plex Media Server
           &#9500;&#9472;1214 Plex Plug-in [com.plexapp.system] /usr/lib/plexmediaserver/Resources/Plug-ins-7be11e1/Framework.bundle/Contents/Resources/Versions/2/Python/bootstrap.py --server-version 0.9.15.6.1714-7be11
           &#9492;&#9472;1413 /usr/lib/plexmediaserver/Plex DLNA Server
```

If your system is running on systemd you cannot add Upstart's or vice versa. But both systemd and upstart are both backward compatible with sysvinit (/etc/init.d)

---

