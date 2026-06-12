---
title: "Coldfusion MX 7 Server"
date: 2006-06-16
forum: Server Platforms
---

### Post by ruomyes90 on 2006-06-16
Installing Coldfusion on 6.06 LTS,  Server Edition,
has anyone got it working??

installed fine but server log has a error on start up:

"Error","main","06/16/06","10:42:05",,"Unable to initialize Graphing service: java.lang.UnsatisfiedLinkError: /opt/coldfusionmx7/runtime/jre/lib/i386/libawt.so: libXp.so.6: cannot open shared object file: No such file or directory"

problem with coldfusion finding xlibs but the xlibs have been replaced by another package, when trying to install the xlibs package get message:

xlibs Package xlibs is not available, but is referred to by another package.
tried installing other libraries but did not work

is there a work around or anything to point me in the right direction.

thanks

---

### Post by ruomyes90 on 2006-06-20
found it, 
just install

libxp6
libxt6
libxtst6

---

