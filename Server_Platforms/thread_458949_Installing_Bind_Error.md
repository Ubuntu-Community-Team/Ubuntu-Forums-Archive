---
title: "Installing Bind Error"
date: 2007-05-30
forum: Server Platforms
---

### Post by a.d.gardiner on 2007-05-30
Hey all,

I think i've managed to screw up BIND9 on my box! :( 

I made a really bad attempt at doing the whole chroot thing ([http://tldp.org/HOWTO/Chroot-BIND-HOWTO-2.html#ss2.1](http://tldp.org/HOWTO/Chroot-BIND-HOWTO-2.html#ss2.1)), so I removed bind and now I'm having a lot of trouble installing it again.

I've looked in /etc/ but there isn't a 'Bind' folder there anymore.

When trying to install with 'sudo apt-get install bind 9' i get this readout:

```
portal@tinkerbell:~$ sudo apt-get install bind9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  bind9-doc
The following NEW packages will be installed:
  bind9
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/322kB of archives.
After unpacking 864kB of additional disk space will be used.
Selecting previously deselected package bind9.
(Reading database ... 115990 files and directories currently installed.)
Unpacking bind9 (from .../bind9_1%3a9.3.4-2ubuntu2_amd64.deb) ...
Setting up bind9 (9.3.4-2ubuntu2) ...
Adding group `bind' (GID 122) ...
Done.
Adding system user `bind' (UID 112) ...
Adding new user `bind' (UID 112) with group `bind' ...
Not creating home directory `/var/cache/bind'.
wrote key file "/etc/bind/rndc.key"
chgrp: cannot access `/etc/bind/named.conf*': No such file or directory
dpkg: error processing bind9 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bind9
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I don't really want to reinstall Ubuntu because I've got everything else setup really nice, any ideas how to sort this out?

---

