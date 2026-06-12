---
title: "Unique error regarding postgresql and the root.crt"
date: 2008-06-29
forum: Security
---

### Post by fbuchele on 2008-06-29
I'm not sure when I got this error, but the other day I was surfing the net and I got the dreaded yellow explosion-exclaimation point saying that postgresql crashed. I tried to send the error report and although firefox was already open it told me that it wasnt responding and couldn't send the error.

However! That is not my problem now. I can't seem to replicate the crash, I wasn't really doing anything special, just surfing the net. Now, when I do
```
sudo apt-get upgrade
```
I get
```
fox@fox-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  pcsx
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postgresql-8.3 (8.3.3-0ubuntu0.8.04) ...
 * Starting PostgreSQL 8.3 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2008-06-29 09:27:13 EDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2008-06-29 09:27:13 EDT DETAIL:  Will not verify client certificates.
2008-06-29 09:27:13 EDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2008-06-29 09:27:13 EDT WARNING:  could not create listen socket for "localhost"
2008-06-29 09:27:13 EDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.3; however:
  Package postgresql-8.3 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postgresql-8.3
 postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This wasn't such a big deal, as it didn't seem to mean anything to me, except a few lines on the end of an upgrade. But the other day I tried to install the playonlinux.deb and I got 
```
Could not install all dependencies
Usually this is related to an error of the software distributor. See the terminal window for more details.
```
I thought that this was a problem with a corrupt file or something, until I looked at the terminal window and saw a familiar error, one related to postgresql. Unfortunately I couldn't figure out how to copy it to this window, so I ran in the terminal:```

fox@fox-laptop:~/Desktop$ sudo dpkg -i PlayOnLinux_3.0.7.deb
[sudo] password for fox: 
Selecting previously deselected package playonlinux.
(Reading database ... 207435 files and directories currently installed.)
Unpacking playonlinux (from PlayOnLinux_3.0.7.deb) ...
Setting up playonlinux (3.0.7) ...

fox@fox-laptop:~/Desktop$
```

...and it worked...

... wtf?

I quickly went to the terminal and ran sudo apt-get upgrade

...and got the same error described as above.

What's going on? how can I get rid of this?

---

