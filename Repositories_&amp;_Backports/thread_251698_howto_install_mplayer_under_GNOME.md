---
title: "howto install mplayer under GNOME"
date: 2006-09-05
forum: Repositories &amp; Backports
---

### Post by cccc on 2006-09-05
hi

howto install mplayer under GNOME without KDE components ?
with apt-cache I can find only KDE mplayer:```

# apt-cache search mplayer
kmplayer-base - Base files for KMPlayer
kmplayer-doc - Handbook for KMPlayer
kmplayer-konq-plugins - KMPlayer plugin for KHTML/Konqueror
```
I have dapper drake.

---

### Post by qamelian on 2006-09-05
Make sure you have multiverse repositories active in your /etc/apt/sources.list. Do ```
sudo apt-get update
``` and search with apt-cache again. You should see it now.

---

### Post by cccc on 2006-09-05
this /etc/apt/sources.list solved this problem:```

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://ch.archive.ubuntu.com/ubuntu dapper main restricted
deb http://ch.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://ch.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://ch.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ch.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://ch.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
#deb http://mirror.ubuntulinux.nl dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
#deb-src http://mirror3.ubuntulinux.nl dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
#deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# Penguin Liberation Front (packages)
#deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Penguin Liberation Front (sources)
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# The Opera browser (packages)
deb http://deb.opera.com/opera etch non-free

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

```

---

