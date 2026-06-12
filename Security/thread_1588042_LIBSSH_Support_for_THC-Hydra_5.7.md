---
title: "LIBSSH Support for THC-Hydra 5.7"
date: 2010-10-04
forum: Security
---

### Post by zuyx on 2010-10-04
Don't know if this is about security, but I think it is. 

Alright, so I downloaded the tar ball from the site.
compiled it all fine. 

But when I try to run the line 
```

./hydra -C Combo001.txt 10.0.6.100 ssh2
```

I end with 
```

Error: Compiled without LIBSSH support, module not available.
```

./configure gives the following, and I see nothing wrong since it says ssh is found.

```
medusa@Cerberus:~/Desktop/hydra-5.7-src$ sudo ./configure

Starting hydra auto configuration ...

Checking for openssl (libssl/ssl.h) ...
                                    ... found
Checking for Postgres (libpq.so) ...
                                 ... NOT found, module postgres disabled
Checking for SVN (libsvn_client-1 libapr-0.so libaprutil-0.so) ...
                              ... NOT found, module svn disabled
Checking for firebird (libfbclient.so) ...
                                       ... NOT found, module firebird disabled
Checking for NCP (libncp.so / nwcalls.h) ...
                                         ... NOT found, module NCP disabled
Checking for SAP/R3 (librfc/saprfc.h) ...
                                      ... NOT found, module sapr3 disabled
Get it from http://www.sap.com/solutions/netweaver/linux/eval/index.asp
Checking for libssh (libssh/libssh.h) ...
                                      ... found
NOTE: ensure that you have libssh v0.4.x installed!! Get it from http://www.libssh.org !
Checking for GUI req's (pkg-config) ...
                                    ... found

Hydra will be installed into .../bin of: /usr/local
  (change this by running ./configure --prefix=path)

Writing Makefile.in ...
now type "make"

```

---

