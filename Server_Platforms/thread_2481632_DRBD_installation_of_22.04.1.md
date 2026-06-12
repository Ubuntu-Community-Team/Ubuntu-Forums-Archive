---
title: "DRBD installation of 22.04.1"
date: 2022-12-05
forum: Server Platforms
---

### Post by mormops on 2022-12-05
Hi All,

I'm currently trying to install DRBD 9 on a pair of servers running Ubuntu 22.04.1 LTS and have run into a problem where the software throws parse errors when starting.  

I'm trying to find out the version number of DRBD that I'm using and have found, through dpkg that it's drbd-utils that's installed, rather than drbd8-utils so it looks like V9.   Cat /proc/drbd however returns version: 8.4.11 (api:1/proto:86-101) which, were it correct, would be a pretty good indication of why the parse error seems to relate to features not in v8.  dpkg 

Can anyone clarify what DRBD version is installed?

Cheers,

Jools

---

### Post by LHammonds on 2022-12-06
On my 22.04.1 LTS server, I ran this command:

```
apt search drbd-utils
Sorting... Done
Full Text Search... Done
drbd-utils/jammy 9.15.0-1build2 amd64
```
So it looks like version 9.15.0 is the version in the official repositories.

LHammonds

---

