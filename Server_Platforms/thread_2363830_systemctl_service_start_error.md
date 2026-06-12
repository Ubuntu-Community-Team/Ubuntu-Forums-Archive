---
title: "systemctl service start error"
date: 2017-06-14
forum: Server Platforms
---

### Post by rgraze on 2017-06-14
Been at this for many hours but can not figure out why this wont run. I created a minecraft-server.service

```
[Unit]
Description=start and stop the minecraft-server
[Service]
WorkingDirectory=/home/minecraft
User=minecraft
Group=minecraft
Restart=on-failure
RestartSec=20 5
ExecStart=/usr/bin/java -Xms1536M -Xmx1536M -jar minecraft_server.jar nogui
[Install]
WantedBy=multi-user.target
Alias=minecraft.service
```

I can see it listed in services actively restarting and exiting but when I try to start then check status I get exited code (behind process)  i get a code exited status 1 failure

Any ideas?

---

