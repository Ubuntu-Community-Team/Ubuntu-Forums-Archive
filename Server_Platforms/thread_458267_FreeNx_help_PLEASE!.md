---
title: "FreeNx help PLEASE!"
date: 2007-05-29
forum: Server Platforms
---

### Post by kevdog on 2007-05-29
Currently trying to install freenx server on Ubuntu Feisty. I ran into a lot of problems.

All packages where download and installed from seaveas repository:
freenx
nxclient
nxlibs
nxagent

Ive suspended all firewalls on the machine

With the server I have added myself as a user and given a password
With the no machine nx client I can connect and authenticate.

The problems begins when trying to start the X session. I suddenly receive and error.
Here is a copy of the log:

NXPROXY - Version 2.1.0

Copyright (C) 2001, 2006 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '23593'.
Session: Starting session at 'Tue May 29 12:25:10 2007'.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Info: Using lan link parameters 1536/24/1/0.
Info: Using image streaming parameters 50/128/1024KB/6144/768.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-rle-9' with session 'unix-gnome'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using persistent cache.
Info: Listening for font server connections on port '11000'.
Session: Session started at 'Tue May 29 12:25:10 2007'.
Info: Established X server connection.
Info: Using shared memory parameters 1/2048K.
Error: Connection with remote peer broken.
Error: Please check the state of your network and retry.
Session: Session terminated at 'Tue May 29 12:25:13 2007'.

It seems I always get connection with remote peer is broken (no matter if I try unix-gnome or unix-kde) Both kde and gnome are installed on the server

Here are the versions of the client and server I am using:
NXCLIENT - Version 2.1.0-17
NXSERVER - Version 1.5.0-60 OS (GPL)

Any help would be greatly appreciated. I did spend hours looking at other posts, however couldn't find a solution.

---

