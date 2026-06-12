---
title: "Installing Cubit on Ubuntu Server 6.06 - PostgreSQL Problems"
date: 2006-09-08
forum: Server Platforms
---

### Post by LeeVee on 2006-09-08
Anyone successfully setup a Cubit Accounting Server on Ubuntu 6.06 Server?
I've done everything to the tee, and can't get it working.
The problem lies in the fact that Cubit does not load all the needed dependancies.

I have tried a totally fresh Ubuntu install with no extra updates or upgrades, and when I run the Cubit installation, it bombs out on the PostgreSQL.
"Failed to install PostgreSQL"

If I run apt-get install upgrade, then the Cubit installs successfully (there is an error  message while it's installing, but it goes through so quickly that i can't see what it is). However, I get an error message,
"/usr/local/cubit/bin/httpd: error while loading shared libraries: libssl.so.0.9.7: cannot open shared object file: No such file or directory"
 when I try to run it.

It is to do with the dependancies, libssl.so.0.9.7, libcrypto.so.0.9.7, libexpat.so.0
When I run an upgrade, these get upgraded to the latest version 0.9.8a
But if I don't run the upgrade, the Cubit won't install, as it doesn't have these dependancies in it's package.

Catch 20?  :(

Is there anyway to install these versions alone into the library?
If I use apt-get install libssl-dev, I get the latest version.

---

