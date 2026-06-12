---
title: "Tuxedo Client Error Compiling on Ubuntu Server 11.10"
date: 2012-02-09
forum: Server Platforms
---

### Post by lmayora on 2012-02-09
When compiling a Tuxedo client source code (using the command
buildclient or cc-gcc) shows me the following error

This error occurs compiling on ubuntu server 11.10 (oneiric ocelot)

tuxfyc@fycservora:/usr/lib/oracle/tuxedo11gR1/samples/atmi/simpapp$ cc   -I$TUXDIR/include -o simpcl   -L${TUXDIR}/lib -m32 simpcl.c -ltux -lbuft  -lfml -lfml32 -lengine -lpthread -ldl
/usr/lib/oracle/tuxedo11gR1/lib/libengine.so: undefined reference to `dlopen'
/usr/lib/oracle/tuxedo11gR1/lib/libengine.so: undefined reference to `dlclose'
/usr/lib/oracle/tuxedo11gR1/lib/libengine.so: undefined reference to `dlerror'
/usr/lib/oracle/tuxedo11gR1/lib/libengine.so: undefined reference to `dlsym'
collect2: ld devolvió el estado de salida 1

This error occurs compiling on ubuntu server 11.10 (Oneiric Ocelot)

I appreciate all the help you can give me. Since Oracle Tuxedo 11g environment I'm setting up Ubuntu Server 11.10

Luis Mayora
Caracas - Venezuela

---

