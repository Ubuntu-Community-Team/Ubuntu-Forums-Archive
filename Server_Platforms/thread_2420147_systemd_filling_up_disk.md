---
title: "systemd filling up disk"
date: 2019-05-30
forum: Server Platforms
---

### Post by sthlm08 on 2019-05-30
i have a newly installed ubuntu 18.04 server with apache runniing. 

For some reason there are a couple of folders in the /tmp folder that is filling up the server

/tmp/systemd-private-9221f7e7cd1a4c91a205501ac1935eae-apache2.service-HlAmNC
/tmp/systemd-private-9221f7e7cd1a4c91a205501ac1935eae-systemd-resolved.service-1BILoi
/tmp/systemd-private-9221f7e7cd1a4c91a205501ac1935eae-systemd-timesyncd.service-1BlMri
/tmp/vmware-root_847-4013198920

It fills up with about 15GB of data everyday. 

Why is this happening and how can i disable it? Restarting the server will clear the folder but i want to avoid restarting it every week.

---

### Post by TheFu on 2019-05-30
Google found this. I don't know if it is related. Seems to be.
[https://www.freedesktop.org/software/systemd/man/systemd-tmpfiles.html](https://www.freedesktop.org/software/systemd/man/systemd-tmpfiles.html)
The manpage for systemd-tmpfiles seems useful and clear.
```

$ more  /usr/lib/tmpfiles.d/tmp.conf

```has some /tmp/ specific settings and a manpage to explain.  Seems the underlying file system has huge impacts on what is possible or not.

I went to see if my single apache2 running system had the overflow issue. It doesn't, so 
```
$ sudo du -sh systemd-private*
8.0K    systemd-private-47cda145c5384dc88dcea4369a5788c5-apache2.service-StkfWp
8.0K    systemd-private-47cda145c5384dc88dcea4369a5788c5-redis-server.service-o3h7jL

```
My initial thought was that looking at the files inside there would provide a clue. On my system, there weren't **any** files stored in those directories at any level.  Have you looked at the files with a PAGER (read-only) on your system?  What do they contain?

By chance, do you use btrfs?

---

### Post by sthlm08 on 2019-05-31
This is how it looks at my end 
2.6G    /tmp/systemd-private-9221f7e7cd1a4c91a205501ac1935eae-apache2.service-HlAmNC
8.0K    /tmp/systemd-private-9221f7e7cd1a4c91a205501ac1935eae-systemd-resolved.service-1BILoi
8.0K    /tmp/systemd-private-9221f7e7cd1a4c91a205501ac1935eae-systemd-timesyncd.service-1BlMri

My tmp.conf looks like this:
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.


# See tmpfiles.d(5) for details


# Clear tmp directories separately, to make them easier to override
D /tmp 1777 root root -
#q /var/tmp 1777 root root 30d


# Exclude namespace mountpoints created with PrivateTmp=yes
x /tmp/systemd-private-%b-*
X /tmp/systemd-private-%b-*/tmp
x /var/tmp/systemd-private-%b-*
X /var/tmp/systemd-private-%b-*/tmp


# Remove top-level private temporary directories on each boot
R! /tmp/systemd-private-*
R! /var/tmp/systemd-private-*

File system is ext4

---

### Post by LHammonds on 2019-05-31
> **sthlm08 said:**
> there are a couple of folders in the /tmp folder that is filling up the server
I do not know the solution to this specific issue with Apache but if you installed your server as a single partition where runaway files in /tmp or /var or other places take every bit of space from your system, the system will crash.

This can be avoided if you separate the partitions during installation.  The link in my sig covers this in detail for future reference.

LHammonds

---

### Post by TheFu on 2019-05-31
Seems modifying the tmpfiles.d/ config as needed.  The manpage explains how.

---

