---
title: "Problem installing bind9"
date: 2011-02-27
forum: Server Platforms
---

### Post by inckiekage on 2011-02-27
Fresh Ubuntu 10.10 server install 

```
kimse@matilde:~$ sudo apt-get install bind9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  bind9-doc resolvconf
The following NEW packages will be installed:
  bind9
0 upgraded, 1 newly installed, 0 to remove and 39 not upgraded.
Need to get 0B/350kB of archives.
After this operation, 1.081kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package bind9.
(Reading database ... 74790 files and directories currently installed.)
Unpacking bind9 (from .../bind9_1%3a9.7.1.dfsg.P2-2ubuntu0.2_amd64.deb) ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up bind9 (1:9.7.1.dfsg.P2-2ubuntu0.2) ...
Adding group `bind' (GID 110) ...
Done.
Adding system user `bind' (UID 103) ...
Adding new user `bind' (UID 103) with group `bind' ...
Not creating home directory `/var/cache/bind'.
wrote key file "/etc/bind/rndc.key"
#
 * Starting domain name service... bind9                                 [fail] 
invoke-rc.d: initscript bind9, action "start" failed.
dpkg: error processing bind9 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)
kimse@matilde:~$ sudo dpkg-reconfigure bind9
/usr/sbin/dpkg-reconfigure: bind9 is broken or not fully installed
```

---

### Post by davidneudorfer on 2012-01-23
I'm having the same problem. Any suggestions? Hopefully we can get this resolved.

---

### Post by s0c0 on 2012-03-01
I ran into this problem. Here's how I fixed it:

```

sudo apt-get autoclean
sudo apt-get purge bind9
sudo apt-get install bind9

```

---

