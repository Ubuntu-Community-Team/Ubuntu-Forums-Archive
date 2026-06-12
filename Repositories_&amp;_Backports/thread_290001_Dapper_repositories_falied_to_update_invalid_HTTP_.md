---
title: "Dapper repositories falied to update: invalid HTTP reply header"
date: 2006-10-31
forum: Repositories &amp; Backports
---

### Post by Roobert on 2006-10-31
Does anyone know what's going on with the dapper repositories? I just did a fresh install from the Dapper live cd, and all of the default repository sites returned 

```
The HTTP server sent an invalid reply header
```

I haven't messed with my /etc/apt/sources.list at all, this is a fresh install! I also checked it against Ubuntu_Demons' and it matches as well.

---

### Post by Roobert on 2006-11-01
Here's the output from ```
sudo apt-get update
``` in case it is at all diagnostic of the problem:

```
$ sudo apt-get update
Err http://archive.ubuntu.com dapper Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  The HTTP server sent an invalid reply header
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/main Sources
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Packages
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/restricted Packages
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/main Sources
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/restricted Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/multiverse Packages
Ign http://archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/universe Packages
  The HTTP server sent an invalid reply header
Err http://security.ubuntu.com dapper-security/multiverse Packages
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper/multiverse Sources
Err http://security.ubuntu.com dapper-security/universe Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/multiverse Sources
  The HTTP server sent an invalid reply header
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/main Sources
Ign http://archive.ubuntu.com dapper-backports/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://archive.ubuntu.com dapper/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/main Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/universe Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper/universe Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/main Sources
  The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Err http://archive.ubuntu.com dapper-backports/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 85.133.25.23 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg The HTTP server sent an invalid reply header [IP: 85.133.25 .23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg The HTTP server sent an invalid reply header [IP: 1 95.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg The HTTP server sent an invalid reply header [IP:  85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz The HTTP server sent an in valid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz The HTTP server sent an invalid reply head er [IP: 85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz The HTTP server sent an inva lid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz The HTTP server sent an invalid repl y header [IP: 195.248.90.54 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz The HTTP server sent an in valid reply header
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz The HTTP server sent an invalid re ply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz The HTTP server sent an invalid reply header [IP : 85.133.25.23 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz The HTTP server sent an invalid reply header
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz The HTTP server sent an invalid reply head er [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz The HTTP server sent an invalid repl y header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz The HTTP server sent an invalid reply header  [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz The HTTP server sent an invalid reply head er [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz The HTTP server sent an invalid re ply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz The HTTP server sent an inva lid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz The HTTP server sent an invalid reply he ader [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz The HTTP server sent an invalid re ply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz The HTTP server sent an in valid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz The HTTP server sent an inva lid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz The HTTP server sent an in valid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz The HTTP server sent an invalid reply header [IP: 195.248.90.54 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz Connection failed [IP: 85.133.25.2 3 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz The HTTP server sent an invalid reply header [IP: 85.133.25.23 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

