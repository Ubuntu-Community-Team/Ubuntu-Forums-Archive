---
title: "Hosting a CSGO server"
date: 2020-10-23
forum: Server Platforms
---

### Post by curckish on 2020-10-23
Hello,

I'm new to ubuntu and i'm trying to get a small csgo server running on my old machine but when i start the server i can't connect to it neither my friends(Connection failed after 30 .....)

```
Distro Details
=================================
Distro:    Ubuntu 20.04.1 LTS
Arch:      x86_64
Kernel:    5.4.0-51-generic
Hostname:  Curckish
Uptime:    0d, 2h, 54m
tmux:      tmux 3.0a
glibc:     2.31

Server Resource
=================================
CPU         
Model:      Intel(R) Core(TM) i3-3225 CPU @ 3.30GHz
Cores:      4
Frequency:  1874.584MHz
Avg Load:   0,08, 0,24, 0,18

Memory     
Mem:       total  used   free   cached  available
Physical:  7,8GB  1,3GB  6,2GB  2,2GB   6,2GB
Swap:      2,0GB  0B     2,0GB

Storage
Filesystem:  /dev/sda5
Total:       457G
Used:        33G
Available:   401G


Game Server Resource Usage
=================================
CPU Used:  20%
Mem Used:  2%   224MB

Storage
Total:        24G
Serverfiles:  24G

Counter-Strike: Global Offensive Server Details
=================================
Server name:      LinuxGSM
App ID:           740
Server IP:        0.0.0.0:27015
Internet IP:      -
Server password:  NOT SET
RCON password:    adminmrDWPa43
Maxplayers:       13
Default map:      de_mirage
Game type:        0
Game mode:        0
Tick rate:        128
Master server:    listed
Status:           ONLINE

csgoserver Script Details
=================================
Script name:            csgoserver
LinuxGSM version:       v20.5.1
glibc required:         2.15
Discord alert:          off
Email alert:            off
IFTTT alert:            off
Mailgun (email) alert:  off
Pushbullet alert:       off
Pushover alert:         off
Rocketchat alert:       off
Slack alert:            off
Telegram alert:         off
Update on start:        off
User:                   csgoserver
Location:               /home/csgoserver
Config file:            /home/csgoserver/serverfiles/csgo/cfg/csgoserver.cfg

Backups
=================================
No Backups created

Command-line Parameters
=================================
./srcds_run -game csgo -usercon -strictportbind -ip 0.0.0.0 -port 27015 +clientport 27005 +tv_port 27020 +sv_setsteamaccount 3F7F7791B13290C9A105CC5EC2CE5F79 -tickrate 128 +map de_mirage +servercfgfile csgoserver.cfg -maxplayers_override 13 +mapgroup mg_active +game_type 0 +game_mode 0 +host_workshop_collection  +workshop_start_map  -authkey  -nobreakpad

Ports
=================================
Change ports by editing the parameters in:
/home/csgoserver/lgsm/config-lgsm/csgoserver

Useful port diagnostic command:
netstat -atunp | grep srcds_linux

DESCRIPTION  DIRECTION  PORT   PROTOCOL
> Game/RCON  INBOUND    27015  tcp/udp
> SourceTV   INBOUND    27020  udp
< Client     OUTBOUND   27005  udp

Status:    ONLINE
```

And i run also ```
netstat -atunp | grep srcds_linux:

(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
tcp        0      0 0.0.0.0:27015           0.0.0.0:*               LISTEN      25369/./srcds_linux 
tcp        0      0 192.168.100.17:36679    146.66.155.38:27030     ESTABLISHED 25369/./srcds_linux 
udp        0      0 0.0.0.0:27005           0.0.0.0:*                           25369/./srcds_linux 
udp        0      0 0.0.0.0:27015           0.0.0.0:*                           25369/./srcds_linux 
udp        0      0 0.0.0.0:27020           0.0.0.0:*                           25369/./srcds_linux 
```

The ports are forwarded on my router and ufw.

---

### Post by slickymaster on 2020-10-23
*Thread moved to **Server Platforms**.*

---

### Post by LHammonds on 2020-10-24
```
ufw status
```

---

