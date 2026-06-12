---
title: "Why still an old version of net-tools / netstat?"
date: 2013-08-31
forum: Ubuntu Development Version
---

### Post by sanderj on 2013-08-31
Hi,

Saucy (just like Raring and earlier Ubuntu version) ships with an old netstat (part of net-tools). My questions:

1) why do Ubuntu (and Debian) still use this old version (including it's bugs) instead of the current version?
2) if no special reason, is there a process to get Ubuntu to ship the current version of net-tools

More details:

```
$ netstat --version
net-tools 1.60
netstat 1.42 (2001-04-15)
```

The current version of net-tools ([http://sourceforge.net/projects/net-tools/](http://sourceforge.net/projects/net-tools/)) is 
```
$ ./netstat --version
net-tools 2.10-alpha
```

I need the updated version of netstat as the old, Ubuntu version of netstat has a 32-bit counter, including a rollover to -2GB after 2GB of traffic. The 2.x version solves that.

Example of rollover-bug:
```
$ netstat -s  | grep -i octet | grep -vi cast
    InOctets: -249959401
    OutOctets: 72041351
```

FWIW: as the installed version is old, I need to update it manually like this:

git clone git://net-tools.git.sourceforge.net/gitroot/net-tools/net-tools
```
cd net-tools/
make config
make
sudo make install
```

---

