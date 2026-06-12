---
title: "server 7.01 and BackupPC  problem"
date: 2008-04-20
forum: Server Platforms
---

### Post by pardi_krk on 2008-04-20
HI all,
I've got problem to install backuppc. 
before I used that aplication to backup my files. After that I unistalled it.
Now I want to install again, aftar type apt-get install backuppc
I recieve a massages:

```
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  libarchive-zip-perl libfile-rsyncp-perl perl-suid
The following NEW packages will be installed
  backuppc libarchive-zip-perl libfile-rsyncp-perl perl-suid
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/714kB of archives.
After unpacking 3035kB of additional disk space will be used.
Do you want to continue [Y/n]? Preconfiguring packages ...
Selecting previously deselected package libarchive-zip-perl.
(Reading database ... 40978 files and directories currently installed.)
Unpacking libarchive-zip-perl (from .../libarchive-zip-perl_1.18-1_all.deb) ...
Selecting previously deselected package libfile-rsyncp-perl.
Unpacking libfile-rsyncp-perl (from .../libfile-rsyncp-perl_0.68-1_amd64.deb) ..
.
Selecting previously deselected package perl-suid.
Unpacking perl-suid (from .../perl-suid_5.8.8-7ubuntu3.1_amd64.deb) ...
Selecting previously deselected package backuppc.
Unpacking backuppc (from .../backuppc_3.0.0-3ubuntu2_all.deb) ...
Setting up libarchive-zip-perl (1.18-1) ...
Setting up libfile-rsyncp-perl (0.68-1) ...
Setting up perl-suid (5.8.8-7ubuntu3.1) ...
Setting up backuppc (3.0.0-3ubuntu2) ...
This module is already enabled!
 * Starting backuppc...                                                                                                                        grep: /etc/backuppc/config.pl: No such file or directory
BackupPC cannot be started because important parameters are missing from config.pl.
If you just upgraded BackupPC, please update /etc/backuppc/config.pl.
invoke-rc.d: initscript backuppc, action "start" failed.
dpkg: error processing backuppc (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 backuppc
```

Where is a problem, haw can i solve it?
Plase any advise.
Peter

---

### Post by ikonia on 2008-04-20
it's complaining that the config.pl script did not get enough parameter passed to it, so it therefore could not start the application.

If the application is installed but not started, look at the config.pl script and see what it needs and run it, if the config.pl script is part of the ubuntu package installer, log a bug.

---

### Post by pardi_krk on 2008-04-20
Hi,
thank for info, I already tried to see in that file, but I couldn't find it.
It looks like backuppc is not fully installed. 
How can I clear server from any logs, files etc from last worked installation. maybe it is a problem. I didnt restart the server after unistall process. is that necessary?? 
thx for any info
Peter

---

### Post by ikonia on 2008-04-20
do a purge remove though synaptic or a apt-get remove --purge on the packge, clear the logs and re-install, same problem = log a bug, [http://www.launchpad.net](http://www.launchpad.net)

---

### Post by pardi_krk on 2008-04-21
Hi,
Thanks a lot. It was very helpful!  Now is everything fine.

Peter

---

### Post by pardi_krk on 2008-04-21
HI,
I have one more question...
How to setup backuppc for samba server on localhost.
everything was fine before I setup rights for folders,
afte that I cant do full backup, i received error log:
```
2008-04-21 08:20:09 Got fatal error during xfer (No files dumped for share /home/PP1)
2008-04-21 08:20:15 Backup aborted (No files dumped for share /home/PP1)
2008-04-21 08:20:15 Saved partial dump 0
```

I tried to add user backuppc to any groups (i setup rigts for groups) 
It doesnt work. 
(I setup server as "small bussines server"  OpenLDAP + samba)

Peter

---

### Post by ikonia on 2008-04-21
see if there are any files in the dump area it's in question.

If not make sure the group your adding the backup user to has write access to where it wants to write.

---

