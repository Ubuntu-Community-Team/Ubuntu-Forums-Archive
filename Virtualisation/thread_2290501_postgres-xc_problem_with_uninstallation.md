---
title: "postgres-xc problem with uninstallation"
date: 2015-08-12
forum: Virtualisation
---

### Post by banjo900 on 2015-08-12
hi currently using a oracle VM virtualbox - with ubuntu 14.04 LTS

My problem is that i can't uninstall the postgres-xc

already tried this link ...   [http://ubuntuforums.org/showthread.php?t=2277582](http://ubuntuforums.org/showthread.php?t=2277582)

i used this command    ....

     [HTML]sudo apt-get purge postgr*[/HTML]

but got this instead 

The following packages will be REMOVED:
  postgres-xc*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 18.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 209130 files and directories currently installed.)
Removing postgres-xc (1.1-2ubuntu2) ...
 * Stopping Postgres-XC datanode                                                                                                                                                                      [ OK ] 
 * Stopping Postgres-XC coordinator                                                                                                                                                                          pg_ctl: server does not shut down
invoke-rc.d: initscript postgres-xc, action "stop" failed.
dpkg: error processing package postgres-xc (--purge):
 subprocess installed pre-removal script returned error exit status 1
 * Starting Postgres-XC datanode                                                                                                                                                                      [ OK ] 
 * Starting Postgres-XC coordinator                                                                                                                                                                          pg_ctl: another server might be running; trying to start server anyway
                                                                                                                                                                                                      [ OK ]
 * Starting Postgres-XC gtm                                                                                                                                                                                  gtm_ctl: invalid data in PID file "/var/lib/postgres-xc/GTM/gtm.pid"
invoke-rc.d: initscript postgres-xc, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgres-xc
E: Sub-process /usr/bin/dpkg returned an error code (1)




any help would really be appreciated here

---

