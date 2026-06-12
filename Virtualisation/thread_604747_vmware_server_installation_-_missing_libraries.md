---
title: "vmware server installation - missing libraries"
date: 2007-11-06
forum: Virtualisation
---

### Post by woja on 2007-11-06
Hi, I have a Gutsy AMD64 machine, trying to install VMware-server-1.0.4-56528. 

I get the following error while running vmware-config.pl:

The correct version of one or more libraries needed to run VMware Server may be
missing.  This is the output of ldd /usr/bin/vmware:
       linux-gate.so.1 =>  (0xffffe000)
       libm.so.6 => /lib32/libm.so.6 (0xf7ed6000)
       libdl.so.2 => /lib32/libdl.so.2 (0xf7ed2000)
       libpthread.so.0 => /lib32/libpthread.so.0 (0xf7eb9000)
       libX11.so.6 => not found
       libXtst.so.6 => not found
       libXext.so.6 => not found
       libXt.so.6 => not found
       libICE.so.6 => not found
       libSM.so.6 => not found
       libXrender.so.1 => not found
       libz.so.1 => not found
       libc.so.6 => /lib32/libc.so.6 (0xf7d6e000)
       /lib/ld-linux.so.2 (0xf7f0e000)


And the fresh license key not being accepted is the other symptom.  Trying to start vmware gives the same missing library indication as above:

root@gemini:/tmp/vmware-server-distrib# /usr/bin/vmware
/usr/lib/vmware/bin/vmware: error while loading shared libraries: libX11.so.6: cannot open shared object file: No such file or directory 

 I have build-essential, xinetd, libX11-6 installed.  Can anyone offer any suggestions?

Cheers,
Roger

---

### Post by woja on 2007-11-07
I'll answer my own question as this has now been solved.  I needed to install (Adept or apt-get install) the ia32-libs package.  While the libraries reported by the installation as missing are actually on the system, they are the 64bit versions and the installer is looking for 32bit ones.

---

### Post by greengaroo on 2008-04-23
So how did you get your 64-bit librairies to work?

Thanks!
greengaroo


"Operator! Give me the number for 911!"
-- Omer

---

### Post by woja on 2008-04-23
at the command line:

sudo apt-get install ia32-libs

or via Adept, search for and install the ia32-libs package.

---

