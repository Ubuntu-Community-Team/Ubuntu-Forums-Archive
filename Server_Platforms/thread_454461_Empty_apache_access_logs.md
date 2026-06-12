---
title: "Empty apache access logs"
date: 2007-05-25
forum: Server Platforms
---

### Post by robk86 on 2007-05-25
Since May 16 there have been no entries going to the Apache access.log file.  I think it might be from me changing the Apache settings to remove the virtual host and only have the default host.  My website works fine, except shopping carts won't install, but that's probably a topic for another thread.   I tried restarting apache and then the computer.  Just now I used Webmin to change a few settings and force a logfile rotation, but that didn't work either.  Here is some of the Apache error.log.2 file minutes after the last access.log entry:
```

[Wed May 16 13:44:36 2007] [notice] SIGHUP received.  Attempting to restart
[Wed May 16 13:44:36 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
PHP Warning:  Module 'gd' already loaded in Unknown on line 0
[Wed May 16 13:44:36 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Wed May 16 13:44:47 2007] [error] [client 192.168.1.2] File does not exist: /htdocs, referer: http://192.168.1.5/
[Wed May 16 13:50:50 2007] [notice] SIGHUP received.  Attempting to restart
[Wed May 16 13:50:50 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
PHP Warning:  Module 'gd' already loaded in Unknown on line 0
[Wed May 16 13:50:50 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Wed May 16 13:54:13 2007] [notice] SIGHUP received.  Attempting to restart
PHP Warning:  Module 'gd' already loaded in Unknown on line 0
[Wed May 16 13:54:13 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations

```
The entries for error.log are still being updated continuously.
Anyone have any thoughts on how to fix this?

---

### Post by robk86 on 2007-05-27
I suppose now might be a good time to try out version 7.04.

---

