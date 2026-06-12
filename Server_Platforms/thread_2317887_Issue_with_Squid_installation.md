---
title: "Issue with Squid installation"
date: 2016-03-21
forum: Server Platforms
---

### Post by fareednn on 2016-03-21
Hi 
      I am trying to install squid I get  error like below I am a beginner please try to help me out.

 ```
sudo apt-get install squid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  squid
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
Need to get 5,962 B of archives.
After this operation, 142 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe squid amd64 3.3.8-1ubuntu6.6 [5,962 B]
Fetched 5,962 B in 1s (5,283 B/s)
Selecting previously unselected package squid.
(Reading database ... 275029 files and directories currently installed.)
Preparing to unpack .../squid_3.3.8-1ubuntu6.6_amd64.deb ...
Unpacking squid (3.3.8-1ubuntu6.6) ...
Setting up postfix (2.11.0-1ubuntu1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: invalid character 47(decimal): cstb.local/cstbdomain
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: cstb.local/cstbdomain
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.

dpkg: error processing package bsd-mailx (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of icinga-common:
 icinga-common depends on bsd-mailx | mailx; however:
  Package bsd-mailx is not configured yet.
  Package mailx is not installed.
  Package bsd-mailx which provides mailx is not configured yet.

dpkg: error processing package icinga-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of icinga-cgi:
 icinga-cgi depends on icinga-common (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-common is not configured yet.

dpkg: error processing package icinga-cgi (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of icinga-core:
 icinga-core depends on icinga-common (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-common is not configured yet.

dpkg: error processing package icinga-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of icinga:
 icinga depends on icinga-cgi (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-cgi is not configured yet.
 icinga depends on icinga-core (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-core is not configured yet.

dpkg: error processing package icinga (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of icinga-idoutils:
 icinga-idoutils depends on icinga-common (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-common is not configured yet.

dpkg: error processing package icinga-idoutils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up squid (3.3.8-1ubuntu6.6) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Errors were encountered while processing:
 postfix
 bsd-mailx
 icinga-common
 icinga-cgi
 icinga-core
 icinga
 icinga-idoutils
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@cstb:/home/cstbdomain# apt-get install postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postfix is already the newest version.
postfix set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up postfix (2.11.0-1ubuntu1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: invalid character 47(decimal): cstb.local/cstbdomain
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: cstb.local/cstbdomain
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              No apport report written because MaxReports is reached already
                                                            dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.

dpkg: error processing package bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icinga-common:
 icinga-common depends on bsd-mailx | mailx; however:
  Package bsd-mailx is not configured yet.
  Package mailx is not installed.
  Package bsd-mailx which provides mailx is not configured yet.

dpkg: error processing package icinga-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icinga-cgi:
 icinga-cgi depends on icinga-common (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-common is not configured yet.

dpkg: error processing package icinga-cgi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icinga-core:
 icinga-core depends on icinga-common (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-common is not configured yet.

dpkg: error processing package icinga-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icinga:
 icinga depends on icinga-cgi (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-cgi is not configured yet.
 icinga depends on icinga-core (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-core is not configured yet.

dpkg: error processing package icinga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of icinga-idoutils:
 icinga-idoutils depends on icinga-common (= 1.13.3-1~ppa1~trusty1); however:
  Package icinga-common is not configured yet.

dpkg: error processing package icinga-idoutils (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Errors were encountered while processing:
 postfix
 bsd-mailx
 icinga-common
 icinga-cgi
 icinga-core
 icinga
 icinga-idoutils
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@cstb:/home/cstbdomain# service postfix reload
 * Reloading Postfix configuration...                                           postfix: warning: valid_hostname: invalid character 47(decimal): cstb.local/cstbdomain
postfix: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: cstb.local/cstbdomain
                                                                         [fail]
root@cstb:/home/cstbdomain# vi /etc/postfix/main.cf
root@cstb:/home/cstbdomain# service postfix reload
 * Reloading Postfix configuration...                                           postfix/postfix-script: fatal: the Postfix mail system is not running
                                                                         [fail]
root@cstb:/home/cstbdomain# apt-get install postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
postfix is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up postfix (2.11.0-1ubuntu1) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 
Setting up bsd-mailx (8.1.2-0.20131005cvs-1ubuntu0.14.04.1) ...
update-alternatives: using /usr/bin/bsd-mailx to provide /usr/bin/mailx (mailx) in auto mode
Setting up icinga-common (1.13.3-1~ppa1~trusty1) ...
 * Starting icinga monitoring daemon icinga                              [ OK ] 
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up icinga-idoutils (1.13.3-1~ppa1~trusty1) ...
dbconfig-common: writing config to /etc/dbconfig-common/icinga-idoutils.conf

Creating config file /etc/dbconfig-common/icinga-idoutils.conf with new version

Creating config file /etc/icinga/ido2db.cfg with new version
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES).
unable to connect to mysql server.
error encountered creating user:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
dbconfig-common: icinga-idoutils configure: aborted.
dbconfig-common: flushing administrative password
dpkg: error processing package icinga-idoutils (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up icinga-cgi (1.13.3-1~ppa1~trusty1) ...

Creating config file /etc/icinga/apache2.conf with new version
apache2_invoke cgi: already enabled
 * Restarting web server apache2                                         [ OK ] 
apache2_invoke: Enable configuration icinga
 * Reloading web server apache2                                                  * 
Adding password for user icingaadmin
Setting up icinga-core (1.13.3-1~ppa1~trusty1) ...
Setting up icinga (1.13.3-1~ppa1~trusty1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 icinga-idoutils
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Regards
Fareed

---

### Post by deadflowr on 2016-03-21
Moved to ***Server Platforms***.

Though it is not clear if you are running a server.
Server platforms seems like the best place for this.

---

### Post by SeijiSensei on 2016-03-21
Nothing there has anything to do with Squid.  It looks like you previously tried to install a package called icinga, and it failed because you had not configured a password for the root user in MySQL.  Since you say you're a beginner, is there a reason you need a monitoring package like that?  If not, I'd start over, not install icinga for the time being, then install Squid and work with that first.

Otherwise you can configure MySQL to have a root password with mysqladmin: [https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords](https://www.howtoforge.com/setting-changing-resetting-mysql-root-passwords).  Then run "sudo dpkg --configure -a" and see how things sort out.

---

