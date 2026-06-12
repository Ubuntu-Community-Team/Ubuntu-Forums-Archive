---
title: "Can't load apache2 mod_security"
date: 2010-05-04
forum: Server Platforms
---

### Post by eXDee on 2010-05-04
I'm attempting to use mod_security with apache2 but it doesnt seem to load. Running Ubuntu 9.10.

```
$ ls -a mods-enabled/
.                     authz_host.load  dir.load           php5.load
..                    authz_user.load  env.load           setenvif.conf
alias.conf            autoindex.conf   mime.conf          setenvif.load
alias.load            autoindex.load   mime.load          status.conf
auth_basic.load       cgi.load         mod-security.load  status.load
authn_file.load       deflate.conf     negotiation.conf   unique_id.load
authz_default.load    deflate.load     negotiation.load
authz_groupfile.load  dir.conf         php5.conf
```
```
$ cat mods-enabled/mod-security.load
LoadFile /usr/lib/libxml2.so.2
LoadModule security2_module /usr/lib/apache2/modules/mod_security2.so
```

```
$ ls -a /usr/lib/apache2/modules | grep mod_security
mod_security2.so
```

Yet even after service apache2 restart...
```
$ apache2 -l
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```

So what am i doing wrong?

Thanks.

---

### Post by Tommetje on 2010-05-04
I'm possible wrong here but isn't there a different between the modules you load when starting apache and the modules that are compiled into the apache server?
 
```

$ apache2 -l
Compiled in modules:
  core.c
  mod_log_config.c
  mod_logio.c
  prefork.c
  http_core.c
  mod_so.c

```
 
These are - I think - modules compiled into the server using **./configure** and **make**, not dynamically loaded modules. These are also C source files (as noted by their extension) and not compiled library files (.so).

---

