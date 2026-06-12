---
title: "neatx server parent process appears to be dead"
date: 2010-08-10
forum: Server Platforms
---

### Post by map7 on 2010-08-10
I'm trying to setup neatx (or some free nx server) under Ubuntu 10.04 32bit and I'm getting issues.

I have this working on another server and I'm just following what I've done on that server.

Here is the client error I get (using NoMachines GPL nxclient which works with one server but not the other):
```
NXPROXY - Version 3.4.0

Copyright (C) 2001, 2010 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Proxy running in client mode with pid '12276'.
Session: Starting session at 'Wed Aug 11 13:29:20 2010'.
Info: Connection with remote proxy completed.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'gnome'.
Info: Using product 'GPL'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0.0'.
Info: Listening to font server connections on port '10033'.
Session: Session started at 'Wed Aug 11 13:29:20 2010'.
Session: Terminating session at 'Wed Aug 11 13:29:21 2010'.
Info: Waiting the cleanup timeout to complete.
Warning: Parent process appears to be dead. Exiting watchdog.
Warning: Parent process appears to be dead. Exiting keeper.
```


Here is the syslog on my server when I try and connect:
```

Aug 11 13:14:54 tony-desktop nxserver[23983]: INFO nxserver:689 Starting nxserver for user map7
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 103 Welcome to: tony-desktop user: map7\n'
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 105 '
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:227 <<< ' listsession --user="map7" --status="suspended,running" --geometry="1920x1080x24+render" --type="unix-gnome"\n'
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'Listsession --user="map7" --status="suspended,running" --geometry="1920x1080x24+render" --type="unix-gnome"\n'
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG nxserver:315 Looking for sessions with types=['unix-gnome'], state=['suspended', 'running']
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session 1734482C78FA47AF92669F9399C2CF11 from /var/lib/neatx/sessions/1734482C78FA47AF92669F9399C2CF11/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session 2A5281274432FF8B94007A35F799EF8A from /var/lib/neatx/sessions/2A5281274432FF8B94007A35F799EF8A/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session 899DB6565703612DD5BB885A3A371756 from /var/lib/neatx/sessions/899DB6565703612DD5BB885A3A371756/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session 931353BCE98488AA4C23B7A3D030BD26 from /var/lib/neatx/sessions/931353BCE98488AA4C23B7A3D030BD26/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session D690B1E4DF0F8AAB4348937AD73FE95D from /var/lib/neatx/sessions/D690B1E4DF0F8AAB4348937AD73FE95D/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session E31E026CD213185A4AF643588D0CBE80 from /var/lib/neatx/sessions/E31E026CD213185A4AF643588D0CBE80/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session F4248854370816F400ED850FDB907F81 from /var/lib/neatx/sessions/F4248854370816F400ED850FDB907F81/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session F62F1B0C6402E85A23B7044204C7FAFB from /var/lib/neatx/sessions/F62F1B0C6402E85A23B7044204C7FAFB/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG session:248 Loading session F9C8F0B217E903AD59A106B6B0D9360A from /var/lib/neatx/sessions/F9C8F0B217E903AD59A106B6B0D9360A/neatx.data
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> "NX> 127 Session list of user 'map7':\n"
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'Display Type             Session ID                       Options  Depth Screen         Status      Session Name\n'
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> '------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------\n'
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> '\n'
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 148 Server capacity: not reached for user: map7\n'
Aug 11 13:14:54 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 105 '
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:227 <<< 'startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="tony" --type="unix-gnome" --geometry="1920x1056" --client="linux" --keyboard="pc105/us" --screeninfo="1920x1056x24+render"\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'Start session with: --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="tony" --type="unix-gnome" --geometry="1920x1056" --client="linux" --keyboard="pc105/us" --screeninfo="1920x1056x24+render"\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: INFO nxserver:377 Starting new session '939533D250697E7BF16B94E73AC4EF38'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG nxserver:645 Connecting to nxnode
Aug 11 13:14:55 tony-desktop nxserver[23983]: INFO node:514 Connecting to '/var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/nxnode.sock'
Aug 11 13:14:55 tony-desktop nxnode-wrapper[23990]: Called with args: map7 939533D250697E7BF16B94E73AC4EF38
Aug 11 13:14:55 tony-desktop nxnode-wrapper[23990]: Started /usr/lib/neatx/nxnode map7 939533D250697E7BF16B94E73AC4EF38
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG nxnode:301 Starting mainloop
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG nxserver:385 Sending startsession command
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG node:551 Sending request: {'cmd': 'start', 'args': {'composite': '1', 'encryption': '1', 'cache': '16M', 'geometry': '1920x1056', 'client': 'linux', 'strict': '0', 'screeninfo': '1920x1056x24+render', 'session': 'tony', 'link': 'adsl', 'shmem': '1', 'media': '0', 'images': '64M', 'keyboard': 'pc105/us', 'type': 'unix-gnome', 'shpix': '1', 'backingstore': '1'}}
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO nxnode:266 Connection established
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO nxnode:81 Received request: 'start', {'session': 'tony', 'strict': '0', 'composite': '1', 'encryption': '1', 'cache': '16M', 'geometry': '1920x1056', 'screeninfo': '1920x1056x24+render', 'client': 'linux', 'link': 'adsl', 'shmem': '1', 'media': '0', 'images': '64M', 'keyboard': 'pc105/us', 'type': 'unix-gnome', 'shpix': '1', 'backingstore': '1'}
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG node:97 Trying display number 268
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG node:106 Display number 268 appears to be unused
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO node:290 Starting xauth for [(':268', 'DDB7C25B01839E81A420F06B7D5F206E'), ('localhost:268', 'DDB7C25B01839E81A420F06B7D5F206E')]
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO daemon:491 Starting program, executable=None, args=['/usr/bin/xauth', '-f', '/var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/authority']
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO daemon:519 Child /usr/bin/xauth[23996] started
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG node:558 Received response: {'result': True, 'success': True}
Aug 11 13:14:55 tony-desktop nxserver[23983]: INFO nxserver:594 Waiting for session '939533D250697E7BF16B94E73AC4EF38' to achieve waiting status
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG session:248 Loading session 939533D250697E7BF16B94E73AC4EF38 from /var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/neatx.data
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/xauth[23996] stderr: /usr/bin/xauth:  creating new authority file /var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/authority
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:560 __CheckExit /usr/bin/xauth[23996] stdin:True stdout:True stderr:True exit:0
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:580 /usr/bin/xauth[23996] exited cleanly
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO node:325 Starting nxagent
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG agent:233 Display for nxagent: 'nx/nx,options=/var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/options:268'
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG agent:627 Writing session options 'nx/nx,fullscreen=0,product=Neatx-GPL,shpix=1,clipboard=both,render=1,composite=1,cache=16M,geometry=1920x1056,accept=127.0.0.1,client=linux,strict=0,cleanup=0,cookie=DDB7C25B01839E81A420F06B7D5F206E,resize=0,keyboard=pc105/us,images=64M,link=adsl,type=gnome,id=tony-desktop-268-939533D250697E7BF16B94E73AC4EF38,backingstore=1,shmem=1:268\n' to /var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/options
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO daemon:491 Starting program, executable=None, args=['/usr/bin/nxagent', '-D', '-name', 'Neatx - map7@tony-desktop:268 - tony', '-options', '/var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/options', '-nolisten', 'tcp', ':268']
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO daemon:519 Child /usr/bin/nxagent[23998] started
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: 
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: NXAGENT - Version 3.4.0
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: 
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Copyright (C) 2001, 2010 NoMachine.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: See http://www.nomachine.com/ for more information.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: 
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Agent running with pid '23998'.
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO agent:346 Matched info agent_pid, PID 23998
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Session: Starting session at 'Wed Aug 11 13:14:55 2010'.
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO agent:409 Nxagent changed status from 'created' to 'starting'
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG session:288 Writing session '939533D250697E7BF16B94E73AC4EF38' to '/var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/neatx.data'
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Proxy running in server mode with pid '23998'.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Waiting for connection from '127.0.0.1' on port '4268'.
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO agent:409 Nxagent changed status from 'starting' to 'waiting'
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO node:366 Starting xrdb
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG session:248 Loading session 939533D250697E7BF16B94E73AC4EF38 from /var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/neatx.data
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO daemon:491 Starting program, executable=None, args=['/usr/bin/xrdb', '-merge']
Aug 11 13:14:55 tony-desktop nxnode[23993]: INFO daemon:519 Child /usr/bin/xrdb[24000] started
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG agent:444 Setting session port to 4268
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG session:288 Writing session '939533D250697E7BF16B94E73AC4EF38' to '/var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/neatx.data'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG session:248 Loading session 939533D250697E7BF16B94E73AC4EF38 from /var/lib/neatx/sessions/939533D250697E7BF16B94E73AC4EF38/neatx.data
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 700 Session id: tony-desktop-268-939533D250697E7BF16B94E73AC4EF38\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 705 Session display: 268\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 703 Session type: unix-gnome\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 701 Proxy cookie: DDB7C25B01839E81A420F06B7D5F206E\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 706 Agent cookie: DDB7C25B01839E81A420F06B7D5F206E\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 704 Session cache: unix-gnome\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 728 Session caption: Neatx - map7@tony-desktop:268 - tony\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 707 SSL tunneling: 1\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 708 Subscription: GPL\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 710 Session status: running\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 105 '
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:227 <<< 'bye\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'Bye\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: DEBUG protocol:172 >>> 'NX> 999 Bye.\n'
Aug 11 13:14:55 tony-desktop nxserver[23983]: INFO nxserver:714 Starting netcat (localhost:4268)
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Accepted connection from '127.0.0.1'.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Connection with remote proxy completed.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Using ADSL link parameters 512/24/1/0.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Using agent parameters 5000/10/50/0/0.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Using pack method 'adaptive-7' with session 'gnome'.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Using product 'Neatx-GPL'.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Using ZLIB data compression 1/1/32.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Using ZLIB stream compression 4/4.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: No suitable cache file found.
Aug 11 13:14:55 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Listening to X11 connections on display ':268'.
Aug 11 13:14:56 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Info: Established X client connection.
Aug 11 13:14:56 tony-desktop nxnode[23993]: DEBUG daemon:461 /usr/bin/nxagent[23998] stderr: Xlib: sequence lost (0x10000 > 0x4) in reply type 0x1!

```

I've tried freenx, but as I have neatx working on the other Ubuntu machine (in another location) I thought I would stick with that.

---

