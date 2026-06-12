---
title: "Gazp6 wired ethernet (jme) no longer working (pre and post Natty)"
date: 2011-05-16
forum: System76 Support
---

### Post by criswell on 2011-05-16
At some point in the last couple of weeks leading up to Natty, during some system upgrade, the ethernet support on my gazp6 inexplicably stopped working under Linux. What's really baffling about it is that it's stopped working under *every* Linux I put on it (even if I roll back and re-install 10.10, or do a fresh install of 11.04). It's not a hardware issue, however, as I am dual-booting successfully and the other OS is able to use the JMicron ethernet just fine.

What I have noticed, however, is that the following messages are spammed in dmesg over and over and over again (while the system apparently tries to re-up the interface):

```

[  236.418753] jme 0000:03:00.0: eth0: Link is down
[  247.069563] jme 0000:03:00.0: eth0: Link is up at ANed: 100 Mbps, Half-Duplex, MDI
[  432.426701] jme 0000:03:00.0: eth0: Link is down
[  443.086205] jme 0000:03:00.0: eth0: Link is up at ANed: 100 Mbps, Half-Duplex, MDI
[ 1198.182788] jme 0000:03:00.0: eth0: Link is down
[ 1208.838275] jme 0000:03:00.0: eth0: Link is up at ANed: 100 Mbps, Half-Duplex, MDI

```

I'm using Kubuntu, but to eliminate that as a possible problem, I've re-installed with stock Ubuntu (11.04 and 10.10) and gotten the same results (always installing the system76-driver package, obviously).

Snooping in the system76-driver package, I noticed there is some jme module customization going on. Any documentation or links someone could point me to or at least advice to help me diagnose the problem I'm having? I'm completely out of ideas...

Other misc. items concerning the system:
```

03:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
        Subsystem: CLEVO/KAPOK Computer Device 5102
        Kernel driver in use: jme
        Kernel modules: jme

root@scorpius:/home/sam/Downloads# dpkg-query -s system76-driver
Package: system76-driver
Status: install ok installed
Priority: optional
Section: drivers
Installed-Size: 1404
Maintainer: System76, Inc. <dev@system76.com>
Architecture: all
Version: 2.6.5
<snip>

```

I have a vague suspicion that the "Other OS" (Windows 7) might have done some strange hardware setting or maybe even a firmware upgrade (?) to mess the JMicron ethernet support under Linux simply because it's odd that it *only* works there... But I'll admit that this fear may be a bit irrational... Until I hear otherwise I'll assume that didn't happen :-)

---

### Post by criswell on 2011-05-17
So, I guess I wasn't *completely* out of ideas...

After posting the above, I searched around some more. I had found the jme driver author's page 404 in the past, but noticed tonight that he's apparently using github: [https://github.com/cooldavid/jme](https://github.com/cooldavid/jme)

So, I cloned the above, did a real simple build:
```


[sam@scorpius ~/work/external/jme]
$ make                                                                                                                                                                                                                                       
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/sam/work/external/jme/jme.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sam/work/external/jme/jme.mod.o
  LD [M]  /home/sam/work/external/jme/jme.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'

```

then rmmod the existing jme and insmod the above built jme:

```

root@scorpius:/opt/system76/system76-driver/src# insmod /home/sam/work/external/jme/jme.ko 

```

and that seemed to solve the problem entirely.

Is the problem simply with either the stock Ubuntu jme drivers, the system76-driver jme-patching, or some combination? Or am I the absolutely only person to encounter this issue?

---

### Post by isantop on 2011-05-19
After installing the System76 Driver, did you run the restore function? Otherwise, it won't actually change anything.

---

### Post by cdrant on 2011-06-07
Pleased to report that after following what you did my ethernet works in ubuntu! Made this account just to say thanks!

---

