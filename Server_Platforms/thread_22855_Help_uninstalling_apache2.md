---
title: "Help uninstalling apache2"
date: 2005-03-30
forum: Server Platforms
---

### Post by Stephen-I-M on 2005-03-30
I'm stuck. I'm trying to completely remove apache2 so that I can start with a clean slate, but one component won't uninstall. Any help MUCH appreciated:

stephen@mahler:/etc/apache2$ agr apache2-mpm-prefork
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  apache2-mpm-prefork
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 483kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 100172 files and directories currently installed.)
Removing apache2-mpm-prefork ...
 * Stopping web server (Apache2)...                                                                                                                 [fail]
invoke-rc.d: initscript apache2, action "stop" failed.
dpkg: error processing apache2-mpm-prefork (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 apache2-mpm-prefork
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Stephen-I-M on 2005-03-30
I got a tip to try adding "exit 0" to the top of "/etc/init.d/apache2", and this let me uninstall the package.

Stephen

---

### Post by antswartz on 2007-05-22
The easiest way I have found to completely remove Apache2 is to enter the Synaptic Package Manager and right click on the apache2 entry, after you searched for it and click on Mark for removal.  You will have to go down the line and remove whatever other extensions accompany apache2, but you will find you will no longer see the process running, telnet to the port, or see it listening in netstat.  Hope this helps.

---

