---
title: "Apt-mirror question"
date: 2012-04-15
forum: Server Platforms
---

### Post by hotstovejer on 2012-04-15
Can mirror.list host packages from different releases? Like if I am running 10.04 server, can I mirror the packages for 12.04?

I am assuming I can, because the packages for the 10.04 install (/var/apt/cache) isn't the same place as the mirror packages, right?

---

### Post by Irregular Joe on 2012-04-15
It sure can! And you can also get different chipset architectures, as well.  Here's a few sample lines to give you the idea:

```

# Just a few sample lines from an /etc/apt/mirror.list file
# Precise on i386
deb-i386 http://archive.ubuntu.com/ubuntu/ precise main restricted
deb-i386 http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
# Precise on amd64
deb-amd64 http://archive.ubuntu.com/ubuntu/ precise main restricted
deb-amd64 http://archive.ubuntu.com/ubuntu/ precise-updates main restricted
# Oneiric on i386
deb-i386 http://archive.ubuntu.com/ubuntu oneiric main restricted universe multiverse
#
# Source file entries can also be used
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted universe multiverse
# Even Debian Squeeze (since Debian also uses .deb packages)
deb-armel http://ftp.us.debian.org/debian squeeze main contrib non-free
deb-armel http://security.debian.org/ squeeze/updates main contrib non-free

```
Just use your /apt/sources.list file as a  model, changing the 'deb' prefix, as well as the codename for the release.  I currently mirror 4 releases and 3 architectures (use 'deb-armel' for the ARM processors).

Remember that the default architecture (if you just use 'deb' is for the architecture of the machine where apt-mirror is running, so if you have old and new machines, you may want to get both.  You can determine which architectures you need by typing
```
uname -m
```
Which will return 'x86_64' (deb-amd64), or 'i686' (deb-i386), or 'armv5tel' (deb-armel).

For each distribution ('precise', 'oneiric'...) and architecture, you will need to plan on downloading and storing about 30G.  At least apt-mirror makes that pretty efficient.

---

