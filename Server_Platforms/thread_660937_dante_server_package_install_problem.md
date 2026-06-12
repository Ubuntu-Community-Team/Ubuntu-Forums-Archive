---
title: "dante server package install problem"
date: 2008-01-07
forum: Server Platforms
---

### Post by alina.bolero on 2008-01-07
I have a fully updated Gutsy install, and it doesn't seem to want to install the Dante proxy server package.  Any idea why that might be?

Thanks,
Alina

```

~# apt-get install dante-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dante-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/124kB of archives.
After unpacking 344kB of additional disk space will be used.
Selecting previously deselected package dante-server.
(Reading database ... 93726 files and directories currently installed.)
Unpacking dante-server (from .../dante-server_1.1.18-2.1_i386.deb) ...
Setting up dante-server (1.1.18-2.1) ...
Starting Dante SOCKS daemon: Jan  7 11:42:07 (1199724127) danted[0]: socks_seteuid(): old: 0, new: 13
Jan  7 11:42:07 (1199724127) danted[0]: socks_reseteuid(): current: 13, new: 0
Jan  7 11:42:07 (1199724127) danted[0]: socks_seteuid(): old: 0, new: 65534
Jan  7 11:42:07 (1199724127) danted[0]: socks_reseteuid(): current: 65534, new: 0
Jan  7 11:42:07 (1199724127) danted[0]: socks_seteuid(): old: 0, new: 65534
Jan  7 11:42:07 (1199724127) danted[0]: socks_reseteuid(): current: 65534, new: 0
Jan  7 11:42:07 (1199724127) danted[0]: fixsettings(): no internal address given
Jan  7 11:42:07 (1199724127) danted[0]: sockdexit(): terminating
invoke-rc.d: initscript danted, action "start" failed.
dpkg: error processing dante-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dante-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by anthro398 on 2008-02-07
I'm really tired of this bug.  Well, I think it's a bug.  For several versions there has been a package error with danted.  You'll probably notice that danted is installed fine on you system.  The problem, for reasons I don't understand, seems to be the /etc/init.d/danted script.  So, although you can start it manually by ```
sudo /etc/init.d/danted start
``` it won't start automatically as part of the boot process.

I saw your post here just as I finally started searching for a solution.  Will post back if I find something.

---

