---
title: "VMWare on Ubuntu 8.04.1"
date: 2008-11-06
forum: Server Platforms
---

### Post by yield999 on 2008-11-06
Hi everyone,

I am currently running a server with 8.0.4.1 version of Ubuntu and I have some problems installing VMware-server-1.0.6-91891.

Here are some informations about my system :

It's a Dell PE 2960 with RAID bla, bla, bla...

> Linux hostname 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686 GNU/Linux

Here is about the **Ubuntu version and CPU**.

> LSB Version:    core-2.0-ia32:core-3.0-ia32:core-3.1-ia32:core-3.2-ia32:core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-3.2-noarch
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

[B]And the CPU:
P.S : There is 2 Xeon so it look like 8 CPU.[/B]

> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Xeon(R) CPU            5130  @ 2.00GHz
stepping        : 6
cpu MHz         : 1995.052
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx tm2 ssse3 cx16 xtpr dca lahf_lm
bogomips        : 3992.50
clflush size    : 64


**When I get to install VMWare I get this :**

> The correct version of one or more libraries needed to run VMware Server may be
missing.  This is the output of ldd /usr/bin/vmware:
        linux-gate.so.1 =>  (0xb7fb4000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7f89000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7f85000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7f6c000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb7e85000)
        libXtst.so.6 => /usr/lib/libXtst.so.6 (0xb7e80000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb7e72000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb7e21000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb7e09000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb7e00000)
        libXrender.so.1 => not found
        libz.so.1 => /usr/lib/libz.so.1 (0xb7deb000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c9c000)
        /lib/ld-linux.so.2 (0xb7fb5000)
        libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7c9a000)
        libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7c81000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7c7e000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7c79000)

This program cannot tell for sure, but you may need to upgrade libc5 to glibc 
before you can run VMware Server.


**Where can I get theses stupid libraries ??? :confused:**


Pleas help

---

### Post by RealPSL on 2008-11-07
Have you tried install libxrender1 with ```
sudo apt-get install libxrender1
```

---

### Post by yield999 on 2008-11-07
Thanks for the reply but, no, it's not that...

> libxrender1 is already the newest version

---

### Post by yield999 on 2008-11-08
Anyone ????????? :confused:

---

### Post by Zeosa on 2008-11-08
EDIT:

Nevermind, stupid question which was answered by re-reading the OP

---

### Post by yield999 on 2008-11-11
So, anyone with an ansert other then ia32-libs...
Any voodoo tricks... Hey ! We never know ! :guitar:

---

### Post by yield999 on 2008-11-11
Ok, I installed VMWare version 1.0.8 and it worked perfectly.
Thanks Anyway ! :)

---

