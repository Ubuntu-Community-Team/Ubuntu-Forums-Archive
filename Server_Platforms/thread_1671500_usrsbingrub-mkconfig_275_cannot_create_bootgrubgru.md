---
title: "/usr/sbin/grub-mkconfig: 275: cannot create /boot/grub/grub.cfg.new: Read-only file s"
date: 2011-01-20
forum: Server Platforms
---

### Post by Link_ on 2011-01-20
Hi people.

i have fresh ubuntu install on dell 2850
i`ve just made fresh install and have not touched server for several days.
for me seems that error appeared due to automatic security update.
uname -a:

```
Linux patent 2.6.35-22-server #35-Ubuntu SMP Sat Oct 16 22:02:33 UTC 2010 x86_64 GNU/Linux
```

error itself:
when i`ve logged in i`ve got:

```
root@patent:~# w
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/ubuntu/+source/command-not-found
Please include the following information with the report:

command-not-found version: 0.2.21
Python version: 2.6.6 final 0
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick
Exception information:

[Errno 5] Input/output error: '/usr/share/command-not-found/programs.d'
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/util.py", line 43, in crash_guard
  File "/usr/lib/command-not-found", line 27, in main
    cnf = CommandNotFound(options.data_dir)
  File "/usr/lib/python2.6/dist-packages/CommandNotFound/CommandNotFound.py", line 88, in __init__
OSError: [Errno 5] Input/output error: '/usr/share/command-not-found/programs.d'
root@patent:~# 

```

ls said:
```

root@patent:~# ls /
ls: reading directory /: Input/output error
```

i`ve restarted server and tried to investigate problem.
nothing was found about faulty hardware in logs.
finally i`ve found that:

```
root@patent:~# dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libisccfg60          Config File Handling Library used by BIND
 libbind9-60          BIND9 Shared Library used by BIND
 dnsutils             Clients provided with BIND
 libgssapi-krb5-2     MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
 openssl              Secure Socket Layer (SSL) binary and related cryptographi
 libisc60             ISC Shared Library used by BIND
 libk5crypto3         MIT Kerberos runtime libraries - Crypto Library
 libisccc60           Command Channel Library used by BIND
 ifupdown             high level tools to configure network interfaces
 linux-image-2.6.35-24-server Linux kernel image for version 2.6.35 on x86_64
 libdns66             DNS Shared Library used by BIND
 liblwres60           Lightweight Resolver Library used by BIND
 linux-headers-server Linux kernel headers on Server Equipment.
 libkrb5support0      MIT Kerberos runtime libraries - Support library
 bind9-host           Version of 'host' bundled with BIND 9.X
 linux-headers-2.6.35-22-server Linux kernel headers for version 2.6.35 on x86_
 apparmor-utils       Utilities for controlling AppArmor
 linux-image-server   Linux kernel image on Server Equipment.
 linux-server         Complete Linux kernel on Server Equipment.
 linux-headers-2.6.35-24-server Linux kernel headers for version 2.6.35 on x86_
 libapparmor-perl     AppArmor library Perl bindings
 apparmor             User-space parser utility for AppArmor
 linux-headers-2.6.35-22 Header files related to Linux kernel version 2.6.35
 linux-headers-2.6.35-24 Header files related to Linux kernel version 2.6.35
 libapparmor1         changehat AppArmor library
 libkrb5-3            MIT Kerberos runtime libraries

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-image-2.6.35-22-server Linux kernel image for version 2.6.35 on x86_64

The following packages have been triggered, but the trigger processing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 libc-bin             Embedded GNU C Library: Binaries

```

that`s why i think it was caused by autoupdate.

also:
```

root@patent:~# update-grub

/usr/sbin/grub-mkconfig: 275: cannot create /boot/grub/grub.cfg.new: Read-only file system
root@patent:~# 
root@patent:~# ls
ls: reading directory .: Input/output error
root@patent:~# 
```

so that means that /usr/sbin/grub-mkconfig causes some error resulting in "Input/output error"

help me please if you have any ideas.

---

### Post by SeijiSensei on 2011-01-20
> /usr/sbin/grub-mkconfig: 275: cannot create /boot/grub/grub.cfg.new: Read-only file system

Quick guess is that the root filesystem has errors so it's being mounted read-only at boot.  Try booting from a CD, then open a terminal and run fsck against the filesystem.  (You can't repair a mounted filesystem, so you need to run off a live CD.)

---

### Post by Link_ on 2011-01-21
thanks for your guess, but i`ve checked that.
after reboot machine is fully operational. read-write filesystem, etc...
only after executing
# update-grub
it filesystem become readonly. so my guess is that "update-grub" script is making / readonly for some purpose, and at that point some bug happens.

---

