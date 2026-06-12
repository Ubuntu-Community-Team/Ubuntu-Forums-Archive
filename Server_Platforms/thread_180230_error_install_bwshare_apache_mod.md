---
title: "error install bwshare apache mod"
date: 2006-05-21
forum: Server Platforms
---

### Post by pataphysician on 2006-05-21
hi, i'm trying to install bwshare:

[http://www.topology.org/src/bwshare/README.html#dso](http://www.topology.org/src/bwshare/README.html#dso)

when i do: apxs -c mod_bwshare.c

i get the following:

gcc -DLINUX=22 -DEAPI -DTARGET="apache" -DHAVE_SET_DUMPABLE -DDB_DBM_HSEARCH=1 -DDEV_RANDOM=/dev/random -DUSE_HSREGEX -O1  -g -Wall -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -fPIC -DSHARED_MODULE -I/usr/include/apache-1.3  -c mod_bwshare.c
mod_bwshare.c: In function âsem_initâ:
mod_bwshare.c:1669: error: âunixd_configâ undeclared (first use in this function)
mod_bwshare.c:1669: error: (Each undeclared identifier is reported only once
mod_bwshare.c:1669: error: for each function it appears in.)
mod_bwshare.c: In function âshm_initâ:
mod_bwshare.c:2772: error: âunixd_configâ undeclared (first use in this function)
apxs:Break: Command failed with rc=1

and uh, i have no idea what that means. anyone have any experience getting this running under ubuntu, or know what i can do here? i'm running apache 2.0.54.

---

