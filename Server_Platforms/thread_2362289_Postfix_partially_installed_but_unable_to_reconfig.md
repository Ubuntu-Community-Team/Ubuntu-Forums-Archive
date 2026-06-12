---
title: "Postfix partially installed but unable to reconfigure"
date: 2017-05-26
forum: Server Platforms
---

### Post by while.false on 2017-05-26
Hello guys,

I have a really annoying problem with Postfix. Not sure what I did but this is my current situation:

If I remove Postfix completly (apt-get purge postfix) and install it again the following error message is printed:

```
apt-get install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  postfix-cdb postfix-doc
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/1,346 kB of archives.
After this operation, 3,600 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package postfix.
(Reading database ... 201374 files and directories currently installed.)
Preparing to unpack .../postfix_2.11.7-0b~trusty0_amd64.deb ...
Unpacking postfix (2.11.7-0b~trusty0) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up postfix (2.11.7-0b~trusty0) ...
start: Job failed to start
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing package postfix (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for ufw (0.34~rc-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

While installing the installation dialog pops up but has already prefilled all information. 

So I'm assuming that apt-get purge postfix doesn't remove all config files.
After that Postfix doesn't start and /etc/postfix/main.cf and master.cf are missing (which is also the error message in /var/log/mail.err).

dpkg-reconfigure postfix returns:

```

/usr/sbin/dpkg-reconfigure: postfix is broken or not fully installed

```

Is it possible to completly remove postfix so I can perform a clean install? (I can't reinstall ubuntu)

---

