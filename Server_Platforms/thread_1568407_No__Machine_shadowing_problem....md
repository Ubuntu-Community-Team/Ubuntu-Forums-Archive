---
title: "No  Machine shadowing problem..."
date: 2010-09-05
forum: Server Platforms
---

### Post by shaft on 2010-09-05
Hello,

I am using debian testing on my office pc, but i need to access it's desktop from time to time. So i need No machine/teamviewer software that can provide me with possibility to interact my desktop.

The problem is, that i want to run shadowed session type, because teamviewer is not good for me. So, when i run no machine in shadowed mode, it crashes with message 
"The connection with remote server was shut down, please check your network settings and try again."

The log is here:


> NXAGENT - Version 3.4.0

Copyright (C) 2001, 2010 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Agent running with pid '5235'.
Session: Starting session at 'Sun Sep  5 14:12:56 2010'.
Info: Proxy running in server mode with pid '5235'.
Info: Waiting for connection from '127.0.0.1' on port '5026'.
Info: Accepted connection from '127.0.0.1'.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using agent parameters 5000/0/50/0/0.
Info: Using pack method 'adaptive-9' with session 'shadow'.
Info: Using product 'LFE/None/LFEN/None'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Listening to X11 connections on display ':1026'.
Info: Established X client connection.
Info: Using shared memory parameters 1/1/0/0K.
Info: Using alpha channel in render extension.
Info: Using local device configuration changes.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

NXCreatePoller: WARNING! Failed to initialize poller.
NXShadowCreate: WARNING! NXCreatePoller failed.
Error: Aborting session with 'Failed to connect to display ':0''.
Session: Aborting session at 'Sun Sep  5 14:12:59 2010'.
Session: Session aborted at 'Sun Sep  5 14:12:59 2010'.
Warning: Signals were not blocked in process with pid '5235'.
Info: Watchdog running with pid '5244'.
Info: Waiting the watchdog process to complete.
Warning: Parent process appears to be dead. Exiting watchdog.

I have only one X server running and only one X session working on the pc.

So, what is the problem? Probably i miss something in the config?

If there is somebody who can help me, please do!

Thanks in advance!

Kindly regards,
Ventsislav Chochev

---

### Post by shaft on 2010-09-07
Nobody can help me?

---

