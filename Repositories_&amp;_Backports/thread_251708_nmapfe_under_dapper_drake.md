---
title: "nmapfe under dapper drake"
date: 2006-09-05
forum: Repositories &amp; Backports
---

### Post by cccc on 2006-09-05
hi

I need repository to install nmapfe on dapper drake with GNOME

greetings
cccc

---

### Post by cccc on 2006-09-07
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

