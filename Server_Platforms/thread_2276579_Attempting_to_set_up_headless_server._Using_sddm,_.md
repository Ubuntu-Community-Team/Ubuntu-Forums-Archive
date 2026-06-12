---
title: "Attempting to set up headless server. Using sddm, x11vnc, and plasma on 15.04"
date: 2015-05-03
forum: Server Platforms
---

### Post by huhlig on 2015-05-03
So I just installed a copy of ubuntu server on 15.04 and I am attempting to setup x11vnc with login support. I currently have sddm setup, x11vnc setup and x11vnc running as a service. I can connect successfully right now but all I get is a black screen with an X shaped cursor. I was assuming I would see the sddm login prompt. Is there something I didn't setup properly?

/lib/systemd/system/x11vnc.service:
[Unit]
Description=Start x11vnc at startup.
After=multi-user.target


[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth /var/run/sddm/:0 -forever -loop -noxdamage -noxrecord -noxfixes -repeat -rfbport 5900 -shared -o /var/log/x11vnc.log


[Install]
WantedBy=multi-user.target

---

### Post by wildmanne39 on 2015-05-04
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2015-05-05
You have an X/Windows connection. Right click and look for a menu. Might need to hold it down for some period of time.
Did you load any X/Windows desktop or WM? Without that, there really isn't much to do.

OTOH, I stopped using vnc years ago - prefer NX solutions like x2go. Better security AND better performance.

---

