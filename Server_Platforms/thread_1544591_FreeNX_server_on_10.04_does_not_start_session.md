---
title: "FreeNX server on 10.04 does not start session"
date: 2010-08-02
forum: Server Platforms
---

### Post by Fidelix on 2010-08-02
I tried using VNC with no success, so i came to try FreeNX.

I have set up the FreeNX server on Ubuntu 10.04 server, and i simply cant connect from my suse machine with NoMachine's FreeNX client.

QTnx does not work also.

I have xubuntu-desktop installed.

Here is the output of freenx-client:

```
NX> 203 NXSSH running with pid: 19863
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: XXXXXXX on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 105 hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 SET SHELL_MODE SHELL
NX> 105 SET AUTH_MODE PASSWORD
NX> 105 login
NX> 101 User: XXXXX
NX> 102 Password: 
NX> 103 Welcome to: XXXXX user: XXXXX
NX> 105 listsession --user="XXXXx" --status="suspended,running" --geometry="1680x1050x24+render" --type="unix-default"
NX> 127 Sessions list of user 'XXXXx' for reconnect:

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------


NX> 148 Server capacity: not reached for user: XXXXX
NX> 105 startsession  --rootless="1" --virtualdesktop="0" --link="adsl" --backingstore="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --imagecompressionmethod="3" --imagecompressionlevel="-1" --render="1" --session="BurstNET" --type="unix-default" --client="linux" --keyboard="pc102/br" --screeninfo="1680x1023x24+render" 

NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 700 Session id: XXXXXXX-2006-6362A672767DA872CE4B88CC4942A656
NX> 705 Session display: 2006
NX> 703 Session type: unix-default
NX> 701 Proxy cookie: eb595009e5d6be635c6e540ab10ec11c
NX> 702 Proxy IP: XXXXXXX
NX> 706 Agent cookie: eb595009e5d6be635c6e540ab10ec11c
NX> 704 Session cache: unix-default
NX> 707 SSL tunneling: 0
NX> 1009 Session status: starting
NX> 710 Session status: running
NX> 1002 Commit
NX> 105 /usr/bin/nxserver: line 1590:  1972 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 1006 Session status: running
bye
Bye
NX> 1001 Bye.
NX> 105 NX> 999 Bye
NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/XXXX/.nx/F-C-XXXXXXX-2006-6362A672767DA872CE4B88CC4942A656/session". You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality. Session log follows:
NX> 280 Exiting on signal: 15
```

Whats wrong?

---

### Post by ruffEdgz on 2010-08-02
I noticed at the bottom that is gave some ideas to why it might have failed. Did you try that yet?

---

### Post by arrrghhh on 2010-08-02
> **Fidelix said:**
> I have xubuntu-desktop installed.

Any reason you posted this in the server section then?

We can try and help, but for the most part people who run servers don't have GUI's... So FreeNX/VNC/etc would be relatively useless to us :p

I think ruffEdgz is already suggesting this as well, I'll just be more direct.  From your post: ```
You might also want to try: ssh -X myserver; /usr/lib/nx/nxnode --agent to test the basic functionality.
```

---

### Post by Fidelix on 2010-08-03
Here's what i get:

```
:~$ /usr/lib/nx/nxnode --agent
NX> 1000 NXNODE - Version 3.2.0-74-SVN OS (GPL, using backend: 3.4.0)
NX> 716 Starting NX Agent ...

NXAGENT - Version 3.4.0

Copyright (C) 2001, 2010 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '25XXX'.
Session: Starting session at 'Tue Aug  3 13:52:46 2010'.
Error: Aborting session with 'Unable to open display 'localhost:10.0''.
Session: Aborting session at 'Tue Aug  3 13:52:52 2010'.
Session: Session aborted at 'Tue Aug  3 13:52:52 2010'.
NX> 716 NX Agent exited with status: 1
NX> 1001 Bye.
```

**BTW, connecting from Windows FreeNX client works fine.**


I checked the file /home/xxxx/.nx/F-C-xxxxxx-2009-C73B30C3E546058549F44E0E7E434918/session and got this:

```
NXAGENT - Version 3.4.0

Copyright (C) 2001, 2010 NoMachine.
See http://www.nomachine.com/ for more information.

Info: Agent running with pid 'XXXXX'.
Session: Starting session at 'Mon Aug  2 20:33:46 2010'.
Info: Proxy running in server mode with pid '27658'.
Info: Waiting for connection from 'XXXXXXX' on port '6003'.
Info: Aborting the procedure due to signal '1'.
Error: Aborting session with 'Unable to open display 'nx/nx,options=/home/xxxxx/.nx/C-xxxxxxxx-2003-F1F0F41BB7C57AC83B5C95F39694CE0D/options:2003''.
Session: Aborting session at 'Mon Aug  2 20:34:46 2010'.
Session: Session aborted at 'Mon Aug  2 20:34:46 2010'.
```

---

### Post by arrrghhh on 2010-08-03
> **Fidelix said:**
> Here's what i get:

```
**Error: Aborting session with 'Unable to open display 'localhost:10.0''**
```

BTW, connecting from Windows FreeNX client works fine.

The errors said several times in several different ways that it couldn't open the display.  

Are you running X on the machine you're trying this on?  It doesn't look like you are, based on that error.  The -X piece in ssh should have forwarded the X session to the machine you are on.

---

### Post by Fidelix on 2010-08-03
I try to run X on SSH and i get:

```

Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)


Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```

I assumed freenx would open X.

I even tried to set "Run the default X client script on server" on FreeNXclient configurations dialog, but i get this:

```

Info: Connecting to remote host 'xxxx'.
Info: Connection to remote proxy 'xxxx' established.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-desktop'. Assuming agent session.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-7' with session 'unix-desktop'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '12017'.
Session: Session started at 'Tue Aug  3 17:54:39 2010'.
Info: Established X server connection.
Session: Terminating session at 'Tue Aug  3 17:54:39 2010'.
Warning: Parent process appears to be dead. Exiting keeper.

```

If u guys can recommend something more painless to setup than freenx, please do.

BTW, the machine i'm trying to connect from is running OpenSuse 11.3.
This is utterly strange. I'm connected right know from Windows, why doesnt it work on Suse?

---

### Post by arrrghhh on 2010-08-03
[quote=Fidelix]"Please also check the log file at "/var/log/Xorg.0.log" for additional information."[/quote]

Please do this.

---

