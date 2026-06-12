---
title: "Problem with installing apache module"
date: 2018-01-19
forum: Server Platforms
---

### Post by kurogane2 on 2018-01-19
Hi,

I've a problem to install [COLOR=#000000]libapache2-mod-fastcgi when try to install give me an errror.

[/COLOR]```
[COLOR=#000000]root@local:# apt-get install libapache2-mod-fastcgi[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  libapache2-mod-fastcgi
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/48.9 kB of archives.
After this operation, 209 kB of additional disk space will be used.
Selecting previously unselected package libapache2-mod-fastcgi.
(Reading database ... 94398 files and directories currently installed.)
Preparing to unpack .../libapache2-mod-fastcgi_2.4.7~0910052141-1.2_amd64.deb ...
Unpacking libapache2-mod-fastcgi (2.4.7~0910052141-1.2) ...
Setting up libapache2-mod-fastcgi (2.4.7~0910052141-1.2) ...
dpkg: error processing package libapache2-mod-fastcgi (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-mod-fastcgi [COLOR=#000000]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```[COLOR=#000000]

[/COLOR]```
[COLOR=#000000]root@local:# apt-get remove --auto-remove libapache2-mod-fastcgi[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libapache2-mod-fastcgi
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 209 kB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 94408 files and directories currently installed.)
Removing libapache2-mod-fastcgi (2.4.7~0910052141-1.2) ...
apache2_invoke fastcgi prerm: No action required
root@local:# apt-get purge --auto-remove libapache2-mod-fastcgi
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  libapache2-mod-fastcgi*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]
(Reading database ... 94400 files and directories currently installed.)
Removing libapache2-mod-fastcgi (2.4.7~0910052141-1.2) ...
Purging configuration files for libapache2-mod-fastcgi (2.4.7~0910052141-1.2) ... [COLOR=#000000]apache2_invoke fastcgi postrm: No action required[/COLOR]
```[COLOR=#000000]

[/COLOR]```
[COLOR=#000000]root@local:# apt-get install libapache2-mod-fastcgi[/COLOR]
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  libapache2-mod-fastcgi
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/48.9 kB of archives.
After this operation, 209 kB of additional disk space will be used.
Selecting previously unselected package libapache2-mod-fastcgi.
(Reading database ... 94398 files and directories currently installed.)
Preparing to unpack .../libapache2-mod-fastcgi_2.4.7~0910052141-1.2_amd64.deb ...
Unpacking libapache2-mod-fastcgi (2.4.7~0910052141-1.2) ...
Setting up libapache2-mod-fastcgi (2.4.7~0910052141-1.2) ...
dpkg: error processing package libapache2-mod-fastcgi (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-mod-fastcgi [COLOR=#000000]E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
```

```
# apachectl -vServer version: Apache/2.4.18 (Ubuntu)
Server built:   2017-09-18T15:09:02

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial
```

---

