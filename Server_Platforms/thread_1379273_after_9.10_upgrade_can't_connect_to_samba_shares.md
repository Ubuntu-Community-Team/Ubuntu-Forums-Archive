---
title: "after 9.10 upgrade can't connect to samba shares"
date: 2010-01-12
forum: Server Platforms
---

### Post by gobbledigook on 2010-01-12
Hi! 

Last night i updated to 9.10, all good except i can no longer access my samba shares!! 

here is the info from log.smbd after i stared it this afternoon

```
  smbd version 3.4.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/01/12 16:35:57,  1] param/loadparm.c:6355(map_parameter)
  Unknown parameter encountered: "executable"
[2010/01/12 16:35:57,  0] param/loadparm.c:7449(lp_do_parameter)
  Ignoring unknown parameter "executable"
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter smb ports found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter server string found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter dns proxy found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter log file found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter max log size found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter syslog found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter panic action found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter encrypt passwords found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter passdb backend found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter obey pam restrictions found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter unix password sync found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter passwd program found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter passwd chat found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter pam password change found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter map to guest found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter socket options found in service section!
[2010/01/12 16:35:57,  0] param/loadparm.c:7478(lp_do_parameter)
  Global parameter usershare allow guests found in service section!
[2010/01/12 16:36:07,  0] lib/util_sock.c:1468(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
[2010/01/12 16:36:07,  0] lib/util_sock.c:730(write_data)
[2010/01/12 16:36:07,  0] lib/util_sock.c:1468(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2010/01/12 16:36:07,  0] smbd/process.c:62(srv_send_smb)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)


```

i kept my original smb.conf file during the upgrade.

any ideaS?

plus attached is my .conf :)

---

### Post by gobbledigook on 2010-01-12
d'oh!

sorry i forgot some important info :)

When i try to log in from a windows machine i get the user/pass prompt... however if i try and log in using "user" with password blank i just get returned to the login screen? blank passwords is enabled in the .conf... the only thing that has changed is my updated to karmic?

---

### Post by gobbledigook on 2010-01-13
*bump*

---

### Post by gobbledigook on 2010-01-13
ok so i got bored waiting for you guys to reply ;)

so i purged samba after backing up the smb.conf on reinstallation i get:

```
server@server:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  smbldap-tools ldb-tools
The following NEW packages will be installed
  samba
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B/6,241kB of archives.
After this operation, 17.1MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 213506 files and directories currently installed.)
**[SIZE="2"][COLOR="Red"]Unpacking samba (from .../samba_2%3a3.4.0-3ubuntu5.3_i386.deb)[/COLOR][/SIZE]** ...
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Setting up samba (2:3.4.0-3ubuntu5.3) ...
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
 * Starting Samba daemons                                                                                                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and if i manually configure:

```
server@server:~$ sudo dpkg --configure samba
Setting up samba (2:3.4.0-3ubuntu5.3) ...
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
Suggested entry (automatically converted using itox):

-----------------------------------------------------------

 * Starting Samba daemons                                                                                                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
server@server:~$

```

the only thing that means anything to me is this line in the first section which is highlighted in red :)

i have an amd64 processor?

---

### Post by gobbledigook on 2010-01-14
*bump*

---

### Post by neoanderthal on 2010-01-14
what does 'testparm' tell you? any errors with your configuration?

---

### Post by gobbledigook on 2010-01-14
hi! thanx for your suggestion :)

```
server@server:~$ testparm
Load smb config files from /etc/samba/smb.conf
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf                                                                             ":
        No such file or directory
Error loading services.

```

i think this is because samba no longer installs correctly?

---

### Post by webweaver on 2011-12-09
Hey, I know this thread is fairly old, but I'm having the same (or similar) issue and was wondering if you ever found a solution?

Thanks!

---

