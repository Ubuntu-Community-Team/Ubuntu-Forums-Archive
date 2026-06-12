---
title: "Cannot connect to Xubuntu server with x2go anymore"
date: 2014-09-24
forum: Server Platforms
---

### Post by gorellana09 on 2014-09-24
Hello folks I am completely frustrated. I've tried everything I've found on google but I'm afraid I'm only making things worse. I need urgent help. 

I have a server which has Xubuntu Desktop 14.04 "Trusty Tahr" (XFCE + x2go) (BETA) (64bits) as the OS. I have been using x2go on windows to connect to this server. Everything had been going great. However I stupidly installed NoMachine on it because I wanted to try it. After I did this I had to reboot my server for some other reason and since then I simply cannot connect to the server with x2go, I've done all, I've reinstalled x2go on both the server and windows, I've uninstalled NoMachine on the server (through putty). I get all sorts of errors about authentication and my password is never accepted. I can connect via Putty ssh fine without a problem. Please what can I do? I don't want to reinstall the OS because I've already spent hours setting up Centova Cast on this server. Please some help?

this is the output on the x2go console
```


NXPROXY - Version 3.5.0


Copyright (C) 2001, 2010 NoMachine.
See http://www.nomachine.com/ for more information.


Info: Proxy running in client mode with pid '2052'.
Session: Starting session at 'Tue Sep 23 23:14:42 2014'.
Info: Connecting to remote host 'localhost:31008'.
Info: Connection to remote proxy 'localhost:31008' established.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
Warning: Failed to read data from the X auth command.
Warning: Generated a fake cookie for X authentication.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display 'localhost:1'.
Session: Session started at 'Tue Sep 23 23:14:44 2014'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Tue Sep 23 23:15:23 2014'.
Session: Session terminated at 'Tue Sep 23 23:15:23 2014'.


NXPROXY - Version 3.5.0


Copyright (C) 2001, 2010 NoMachine.
See http://www.nomachine.com/ for more information.


Info: Proxy running in client mode with pid '5620'.
Session: Starting session at 'Tue Sep 23 23:15:37 2014'.
Info: Connecting to remote host 'localhost:31008'.
Info: Connection to remote proxy 'localhost:31008' established.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
Warning: Failed to read data from the X auth command.
Warning: Generated a fake cookie for X authentication.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: Using cache file '/cygdrive/C/Users/GLO/X2GO~1/cache-unix-kde-depth_32/S-D564A6458B7DAB21195FA09137309A62'.
Info: Forwarding X11 connections to display 'localhost:1'.
Session: Session started at 'Tue Sep 23 23:15:40 2014'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.

```

In this instance it actually did finally connect but all I get is a blank screen and no Xubuntu desktop.

---

### Post by TheFu on 2014-09-24
Can you run an xterm?  This means using the custom config from the x2go client side.  Point it to the complete path to an xterm.  Then you can try to startup any desktop or window manager you like. This will make troubleshooting easier.

Might be worth re-installing xubuntu-desktop package. Perhaps that became corrupted?  Trying to run it from the xterm will let you see any errors.

---

### Post by gorellana09 on 2014-09-24
I had done that and it didn't work. Ended up just doing a whole OS reinstall. No solutions to this anywhere and all posts all over the net about this issue have gone unanswered.

---

### Post by TheFu on 2014-09-24
What did NoMachine support say?  Just curious, since that is why people use their code - support.

---

