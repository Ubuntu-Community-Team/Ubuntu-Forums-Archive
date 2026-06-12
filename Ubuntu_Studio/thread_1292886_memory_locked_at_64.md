---
title: "memory locked at 64?"
date: 2009-10-16
forum: Ubuntu Studio
---

### Post by pyrael on 2009-10-16
I've googled for hours trying to find an answer to this. I'm not 100% new to linux and Pro Audio, but I am new to Ubuntu Studio. After finally getting the permissions setup for my firewire interface etc, I fired up Ardour to run a test. Well, Ardour is complaining that I have a memory lock in affect.  ulimit -l responds with 64, however in /etc/security/limits.conf there is no mlock in place. I have the mlock in jackd disabled as well.

here's the limits.conf contents:

```

#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

@audio          -       rtprio          99

# End of file

```I have 2GB Ram installed on a Q6600 machine, so a limit like this (If I am reading correctly) seems really bad.

Any and all help greatly appreciated

Py

---

