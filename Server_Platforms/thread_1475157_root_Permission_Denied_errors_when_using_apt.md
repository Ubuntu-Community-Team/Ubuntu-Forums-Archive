---
title: "root Permission Denied errors when using apt"
date: 2010-05-06
forum: Server Platforms
---

### Post by shavenlunatic on 2010-05-06
Hi,

Just had a new VPS installed running Ubuntu Server 8.04

Getting some errors when I connect to the server and try to use apt.. only trying to install nano and after messing around I've managed to get the error to change.. but still can't get any further.

error

```
# sudo apt-get install nano
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  spell
The following NEW packages will be installed:
  nano
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 296kB of archives.
After this operation, 1753kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com hardy/main nano 2.0.7-1ubuntu1 [296kB]
Fetched 296kB in 0s (2623kB/s)
(Reading database ... 38801 files and directories currently installed.)
Unpacking nano (from .../nano_2.0.7-1ubuntu1_i386.deb) ...
Setting up libpq5 (8.3.10-0ubuntu8.04.1) ...

Setting up nano (2.0.7-1ubuntu1) ...
update-alternatives: unable to make /usr/bin/pico.dpkg-tmp a symlink to /etc/alt                                                                                                                       ernatives/pico: Permission denied
dpkg: error processing nano (--configure):
 subprocess post-installation script returned error exit status 2
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nano
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
# dk
-bash: dk: command not found
root@damagestudios-1:/var/cache/apt/archives# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/vzfs             10485760   9645868    839892  92% /
tmpfs                   131072        56    131016   1% /var/run
tmpfs                   131072         0    131072   0% /var/lock
/dev/vzfs             10485760   9645868    839892  92% /dev/.static/dev
udev                    131072         0    131072   0% /dev
tmpfs                   131072         0    131072   0% /dev/shm
tmpfs                   131072         0    131072   0% /opt/psa/handlers/before-local
tmpfs                   131072         0    131072   0% /opt/psa/handlers/before-queue
tmpfs                   131072         0    131072   0% /opt/psa/handlers/before-remote
tmpfs                   131072         0    131072   0% /opt/psa/handlers/info
tmpfs                   131072       108    130964   1% /opt/psa/handlers/spool

```

Any help?

---

### Post by CharlesA on 2010-05-06
Isn't nano already installed by default?

---

### Post by windependence on 2010-05-06
> **CharlesA said:**
> Isn't nano already installed by default?
Indeed I believe it is.

This error could also be caused by not having the development packages installed. Sounds like make is not installed.

-Tim

---

### Post by shavenlunatic on 2010-05-06
nah, it was an issue of space.  It seems my brand-new VPS came pre-installed with a rootkit which was downloading files every second.. awesome

avoid switchlink.co.uk if possible :)

---

### Post by Dayofswords on 2010-05-06
> **shavenlunatic said:**
> nah, it was an issue of space.  It seems my brand-new VPS came pre-installed with a rootkit which was downloading files every second.. awesome

avoid switchlink.co.uk if possible :)

fun

```
# sudo apt-get install nano

```why are you doing sudo as root?

---

