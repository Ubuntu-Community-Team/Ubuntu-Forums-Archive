---
title: "Server 10.04.3 kernel CONFIG_HZ=100HZ no more?"
date: 2011-08-19
forum: Server Platforms
---

### Post by binary.koala on 2011-08-19
hi all,

according to [https://help.ubuntu.com/community/Server/TechSpecs/1004LTS](https://help.ubuntu.com/community/Server/TechSpecs/1004LTS) Ubuntu Server 10.04 LTS supposed to run 100HZ kernel. This has been a tradition in Ubuntu server kernel images and some things seem to rely on this configuration. 

$ sudo apt-get update
$ sudo apt-get install linux-server
$ grep "CONFIG_HZ" /boot/config-2.6.32-33-generic-pae
# CONFIG_HZ_100 is not set
CONFIG_HZ_250=y

is there no more specialized server-kernel in 10.04.3?
after recent upgrade from 8.04 to 10.04.3 i'm having issues with MD RAID IO overload on a production server. at several forums i read this can be caused by higher kernel clock. 
i went to check if CONFIG_HZ changed between the versions (linux-image-2.6.24-28-server and linux-server on 10.04) and was shocked to see that it did.

also, i'm not able to install any linux-image-*-server only meta linux-server package - is there no more server kernel or is my apt screwed up?

any comments?

---

### Post by iissmart on 2011-08-21
This is what I see from my 10.04 server...

```
$ sudo apt-cache search linux*-server
linux-image-2.6.32-21-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-22-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-23-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-24-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-25-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-26-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-27-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-28-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-29-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-30-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-31-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-32-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.32-33-server - Linux kernel image for version 2.6.32 on x86_64
linux-image-2.6.35-22-server - Linux kernel image for version 2.6.35 on x86_64
linux-image-2.6.35-23-server - Linux kernel image for version 2.6.35 on x86_64
linux-image-2.6.35-25-server - Linux kernel image for version 2.6.35 on x86_64
linux-image-2.6.35-30-server - Linux kernel image for version 2.6.35 on x86_64
linux-image-2.6.38-10-server - Linux kernel image for version 2.6.38 on x86_64
linux-server - Complete Linux kernel on Server Equipment.
```

You're looking at the -generic-pae kernel, only the -server kernels are at 100HZ.

---

### Post by ian dobson on 2011-08-21
Hi,

I don't know if this helps but my server running 11.04 I'm seeing :-
grep "CONFIG_HZ" /boot/config-2.6.38-11-generic
CONFIG_HZ_100=y
# CONFIG_HZ_250 is not set
# CONFIG_HZ_300 is not set
# CONFIG_HZ_1000 is not set
CONFIG_HZ=100

So maybe the pae kernel doesn't support 100Hz. Why not just compile your own kernel. It's abit of a pain in the butt, but no pain no gain.

Also why do you want the pae kernel?

Regards
Ian Dobson

---

