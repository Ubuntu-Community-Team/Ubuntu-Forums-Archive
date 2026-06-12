---
title: "Ubuntu for Servers ? I don´t think so..."
date: 2006-09-23
forum: Server Platforms
---

### Post by xMbx on 2006-09-23
I serioesly don´t think Ubuntu is ready for server usage. We installed now Ubuntu on many system due hardware reasons.

So far i can tell, not a day without a crash. And no, we didn`t had these problems ever on Debian.

Very often MySQL Servers crush out of nowhere. I tried alot, but i couldn`t trace it back.

For Apache Servers... that is less often, still it happens around all 3 days. For errors, i even get a segfault while restarting the HTTP. Looks like this:

Sep 22 23:38:48 ubuntu kernel: [316831.327039] httpd[26908]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a158 error 14
Sep 22 23:38:49 ubuntu kernel: [316828.120656] httpd[26790]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a158 error 14
Sep 22 23:38:49 ubuntu kernel: [316831.475413] httpd[26962]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a148 error 14
Sep 22 23:38:49 ubuntu kernel: [316831.503874] httpd[26427]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a008 error 14
Sep 22 23:38:49 ubuntu kernel: [316828.254555] httpd[26851]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a148 error 14
Sep 22 23:38:49 ubuntu kernel: [316831.519531] httpd[26853]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a148 error 14
Sep 22 23:38:49 ubuntu kernel: [316833.583876] httpd[25854]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a0f8 error 14
Sep 22 23:38:50 ubuntu kernel: [316835.457800] httpd[12814]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a0f8 error 14
Sep 22 23:38:51 ubuntu kernel: [316836.560995] httpd[12876]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a0e8 error 14
Sep 22 23:46:28 ubuntu kernel: [317289.610727] httpd[27608]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a128 error 14
Sep 22 23:46:28 ubuntu kernel: [317289.625671] httpd[27593]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a128 error 14
Sep 22 23:46:28 ubuntu kernel: [317289.653599] httpd[27344]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a0c8 error 14
Sep 22 23:46:28 ubuntu kernel: [317286.419565] httpd[27432]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a238 error 14
Sep 22 23:46:28 ubuntu kernel: [317289.713567] httpd[27065]: segfault at 00002aaaac2a4680 rip 00002aaaac2a4680 rsp 00007fffff33a238 error 14

Still, i couldn`t trace it back yet too.

So, anyone who thinks, who can fix that ?

---

### Post by colo on 2006-09-23
Seems like you hardware is broken. Give memtest and the mersenne prime stresstest a shot to make sure.

---

### Post by xMbx on 2006-09-23
I did memtest86+ on system start. No error.

Hardware is AMD 64 X2 3800+, 2x1GB RAM (800mhz) in DualChannel.

Apache Compiler Flags:

CFLAGS='-O3 -ffast-math -mtune=athlon64 -march=athlon64 -fomit-frame-pointer -msse3'

The "mersenne prime stresstest" is ?

And this is not a single server problems; alot...

---

### Post by colo on 2006-09-23
Oh, a ricer... ;)

-O3 is evil, and -ffast-math already implied by it. -march overrules -mtune. Seriously, try again with less insane CFLAGS.

The mersenne prime stresstest is to be found at [http://www.mersenne.org/](http://www.mersenne.org/) and will spot potential errors in the FPU-Units of your CPU or your memory subsystem (when run with the "-t"-parameter for "torture test").

---

### Post by xMbx on 2006-09-23
> **colo said:**
> Oh, a ricer... ;)

-O3 is evil, and -ffast-math already implied by it. -march overrules -mtune. Seriously, try again with less insane CFLAGS.

The mersenne prime stresstest is to be found at [http://www.mersenne.org/](http://www.mersenne.org/) and will spot potential errors in the FPU-Units of your CPU or your memory subsystem (when run with the "-t"-parameter for "torture test").

Ok, how about CFLAGS="-march=athlon64 -O2 -msse3" ? Happy then ?

---

### Post by colo on 2006-09-23
Yeah, seem a LOT more rational to me :)

---

### Post by xMbx on 2006-09-24
> **colo said:**
> Yeah, seem a LOT more rational to me :)

I did it. Not any better. The MySQL Servers still crush.

Jun 2 16:59:55 localhost kernel: factorial[24181]: segfault at 0000000000020f51 rip 0000000000402dba rsp 00007fffffd127d0 error 4
Jun 2 16:59:55 localhost kernel: factorial[24184]: segfault at 0000000000020f51 rip 0000000000402dba rsp 00007fffffb00c90 error 4
Jun 2 16:59:55 localhost kernel: factorial[24187]: segfault at 0000000000020f51 rip 0000000000402dba rsp 00007fffffb434b0 error 4
Jun 2 16:59:55 localhost kernel: factorial[24190]: segfault at 0000000000020f51 rip 0000000000402dba rsp 00007fffffbf3f80 error 4
Jun 2 16:59:55 localhost kernel: factorial[24193]: segfault at 0000000000020f51 rip 0000000000402dba rsp 00007ffffffa44d0 error 4

And so far i see... the CPU load seems to be always at 100% or ven bigger for the MySQL process.

So, what is factorial and what todo ?

---

### Post by rastilin on 2006-09-25
Very strange, I got a mysql database running with apache2 on Ubuntu with no problems. Without the LAMP autosetup function.

My first question is why you need to compile apache? I'd like to hear more about how your server is set up.

---

