---
title: "Smokeping totally broken after 12.x upgrade."
date: 2012-07-28
forum: Server Platforms
---

### Post by pot_roast on 2012-07-28
When I try to install (or reinstall) smokeping, I have the following:

The following packages will be REINSTALLED:
  smokeping 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up smokeping (2.6.7-1) ...       
 * Starting latency logger daemon smokeping
   ...fail!
invoke-rc.d: initscript smokeping, action "start" failed.
dpkg: error processing smokeping (--configure):
 subprocess installed post-installation script returned error exit status 6
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 smokeping
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up smokeping (2.6.7-1) ...
 * Starting latency logger daemon smokeping
   ...fail!
invoke-rc.d: initscript smokeping, action "start" failed.
dpkg: error processing smokeping (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 smokeping


--
Can't start it manually.
ERROR: /etc/smokeping/config, line 16: File '/etc/smokeping/smokemail' does not exist

A bug has already been filed on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/smokeping/+bug/993129](https://bugs.launchpad.net/ubuntu/+source/smokeping/+bug/993129)

Has anyone else run into this or found a workaround yet?
--

edit: yes, I have Googled extensively for this. I also tried downloading the source package, and there is no smokemail binary in it. So I have no idea where this is even coming from.

Also I am using 12.04, not 6.06.. I don't have enough posts (50!!!) to edit my own details.

---

