---
title: "need help on fixing system service error"
date: 2019-06-27
forum: Ubuntu/Debian BASED
---

### Post by rm32 on 2019-06-27
I'm currently working on my first Ubuntu server getting a Minecraft server set up.  I'm setting up the system service for starting the Minecraft server on boot but I keep running in to an error.





(*path)
/opt/minecraft/survival


banned-ips.json      eula.txt  mkdir     server.properties  whitelist.json
banned-players.json  logs      ops.json  Server.jar  usercache.json     world




(*Path)
/etc/systemd/system/minecraft@.service


cloud-final.service.wants              dbus-org.freedesktop.thermald.service  getty.target.wants      minecraft@.service           open-vm-tools.service.requires     snap-core-7169.mount       sshd.service         
timers.target.wants                    cloud-init.target.wants                          default.target.wants                                          graphical.target.wants                  multi-user.target.wants       paths.target.wants              
snap-core-7270.mount                   sysinit.target.wants                          dbus-org.freedesktop.resolve1.service                 final.target.wants                        iscsi.service           
network-online.target.wants            samba-ad-dc.service                        sockets.target.wants      syslog.service




(*Code in Minecraft@.service)
[Unit]
Description=Minecraft Server: %i
After=network.target




[Service]
WorkingDirectory=/opt/minecraft/%i


User=minecraft
Group=minecraft


Restart=always


ExecStart=/usr/bin/screen -DmS mc-%i /usr/bin/java -Xmx6G -jar server.jar nogui


ExecStop=/usr/bin/screen -p 0 -S mc-%i -X eval 'stuff "say SERVER SHUTTING DOWN IN 5 SECONDS. SAVING ALL MAPS..."\015'
ExecStop=/bin/sleep 5
ExecStop=/usr/bin/screen -p 0 -S mc-%i -X eval 'stuff "save-all"\015'
ExecStop=/usr/bin/screen -p 0 -S mc-%i -X eval 'stuff "stop"\015'




[Install]
WantedBy=multi-user.target


(*end of code)


(*error log)
&#9679; [email]minecraft@survival.servic[/email]e - Minecraft Server: survival
   Loaded: loaded (/etc/systemd/system/minecraft@.service; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2019-06-28 03:01:36 UTC; 48s ago
  Process: 2953 ExecStop=/usr/bin/screen -p 0 -S mc-survival -X eval stuff "say SERVER SHUTTING DOWN IN 5 SECONDS. SAVING ALL MAPS..."^M (code=exited, status=1/FAILURE)
  Process: 2951 ExecStart=/usr/bin/screen -DmS mc-survival /usr/bin/java -Xmx6G -jar server.jar nogui (code=exited, status=0/SUCCESS)
 Main PID: 2951 (code=exited, status=0/SUCCESS)


Jun 28 03:01:36 minecraft-server systemd[1]: [email]minecraft@survival.servic[/email]e: Service hold-off time over, scheduling restart.
Jun 28 03:01:36 minecraft-server systemd[1]: [email]minecraft@survival.servic[/email]e: Scheduled restart job, restart counter is at 5.
Jun 28 03:01:36 minecraft-server systemd[1]: Stopped Minecraft Server: survival.
Jun 28 03:01:36 minecraft-server systemd[1]: [email]minecraft@survival.servic[/email]e: Start request repeated too quickly.
Jun 28 03:01:36 minecraft-server systemd[1]: [email]minecraft@survival.servic[/email]e: Failed with result 'exit-code'.
Jun 28 03:01:36 minecraft-server systemd[1]: Failed to start Minecraft Server: survival.

---

