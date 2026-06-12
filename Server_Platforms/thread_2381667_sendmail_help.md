---
title: "sendmail help"
date: 2018-01-03
forum: Server Platforms
---

### Post by Gareth_2007 on 2018-01-03
Hi all,

I've got sendmail to send me a e-mail from a script using :

```
echo "Starting Ark Server..." | mail -s Ark Server myemail@pomail.net
```

would it be possible to get it to e-mail me the status of a program so i know it has loaded?

for example i need to login to view atm:

```
root@VPS:/home/boris# service  ark status
&#9679; ark.service - ARK: Survival Evolved dedicated server
   Loaded: loaded (/etc/systemd/system/ark.service; enabled)
   Active: active (running) since Wed 2018-01-03 22:04:31 GMT; 6min ago
  Process: 352 ExecStartPre=/home/steam/Steam/steamcmd.sh +login anonymous +force_install_dir /home/steam/Steam/servers/ark +app_update 376030 +quit (code=exited, status=0/SUCCESS)
 Main PID: 473 (ShooterGameServ)
   CGroup: /system.slice/ark.service
           &#9492;&#9472;473 /home/steam/Steam/servers/ark/ShooterGame/Binaries/Linux/ShooterGameServer TheIsland?listen?SessionName=Gaming?ServerPassword=PASSWORD?ServerAdminPassword=PASSWORD ...

Jan 03 22:04:27 VPS steamcmd.sh[352]: Steam Console Client (c) Valve Corporation
Jan 03 22:04:27 VPS steamcmd.sh[352]: -- type 'quit' to exit --
Jan 03 22:04:27 VPS steamcmd.sh[352]: Loading Steam API...OK.
Jan 03 22:04:29 VPS steamcmd.sh[352]: Connecting anonymously to Steam Public...Logged in OK
Jan 03 22:04:31 VPS steamcmd.sh[352]: Waiting for user info...OK
Jan 03 22:04:31 VPS steamcmd.sh[352]: Success! App '376030' already up to date.
Jan 03 22:04:31 VPS steamcmd.sh[352]: CWorkThreadPool::~CWorkThreadPool: work processing queue not empty: 2 items discarded.
Jan 03 22:04:31 VPS systemd[1]: Started ARK: Survival Evolved dedicated server.
Jan 03 22:04:35 VPS ShooterGameServer[473]: [S_API FAIL] SteamAPI_Init() failed; SteamAPI_IsSteamRunning() failed.
Jan 03 22:04:35 VPS ShooterGameServer[473]: Setting breakpad minidump AppID = 346110
```

this is the only important line really - 

```
Active: active (running) since Wed 2018-01-03 22:04:31 GMT; 6min ago
```

any help would be great

:)

---

### Post by howefield on 2018-01-03
Thread moved to the "*Server Platforms*" forum.

---

### Post by spjackson on 2018-01-04
How about...
```

service ark status | fgrep Active | mail -s "Ark Server" myemail@pomail.net

```

---

