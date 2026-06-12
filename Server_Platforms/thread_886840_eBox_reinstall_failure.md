---
title: "eBox reinstall failure"
date: 2008-08-11
forum: Server Platforms
---

### Post by sebald on 2008-08-11
A first install of eBox was successful from the apt-get command line, but then for some reason I removed it.

Now on trying to reinstall it I get an error message and I can't connect to it

```
The ebox group has not been set in the config file.Creating the eboxlogs database
dpkg: error processing ebox (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ebox
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I did delete the previous intall's /var/lib/ebox directory with ssl keys, no dice.

---

