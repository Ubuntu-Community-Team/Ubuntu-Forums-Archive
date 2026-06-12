---
title: "apt-get update problem"
date: 2009-03-05
forum: Server Platforms
---

### Post by bellalamb on 2009-03-05
Hi 

I am using server v7.04

When I try and use

apt-get update (or any other apt-get functions)

I get a lot of errors - mostly "file not found"

any ideas please?

```

paul@ubuntu2:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_GB
Ign cdrom://Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty Release.gpg
Ign http://gb.archive.ubuntu.com feisty/main Translation-en_GB
Ign http://security.ubuntu.com feisty-security Release.gpg
Ign http://security.ubuntu.com feisty-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates Release.gpg
Ign http://gb.archive.ubuntu.com feisty-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com feisty Release
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_GB
Ign http://security.ubuntu.com feisty-security/universe Translation-en_GB
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com feisty-security Release
Ign http://gb.archive.ubuntu.com feisty-updates Release
Ign http://security.ubuntu.com feisty-security/main Packages
Ign http://gb.archive.ubuntu.com feisty/main Packages
Ign http://gb.archive.ubuntu.com feisty/restricted Packages
Ign http://gb.archive.ubuntu.com feisty/main Sources
Ign http://gb.archive.ubuntu.com feisty/restricted Sources
Ign http://gb.archive.ubuntu.com feisty/universe Packages
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://security.ubuntu.com feisty-security/restricted Sources
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://gb.archive.ubuntu.com feisty/universe Sources
Ign http://gb.archive.ubuntu.com feisty/multiverse Packages
Ign http://gb.archive.ubuntu.com feisty/multiverse Sources
Ign http://gb.archive.ubuntu.com feisty-updates/main Packages
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://gb.archive.ubuntu.com feisty-updates/main Sources
Ign http://security.ubuntu.com feisty-security/universe Sources
Ign http://gb.archive.ubuntu.com feisty-updates/restricted Sources
Err http://gb.archive.ubuntu.com feisty/main Packages
  404 Not Found
Ign http://security.ubuntu.com feisty-security/multiverse Packages
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Err http://gb.archive.ubuntu.com feisty/restricted Packages
  404 Not Found
Err http://gb.archive.ubuntu.com feisty/main Sources
  404 Not Found
Err http://security.ubuntu.com feisty-security/main Packages
  404 Not Found
Err http://security.ubuntu.com feisty-security/restricted Packages
  404 Not Found
Err http://security.ubuntu.com feisty-security/main Sources
  404 Not Found
Err http://security.ubuntu.com feisty-security/restricted Sources
  404 Not Found
Err http://gb.archive.ubuntu.com feisty/restricted Sources
  404 Not Found
Err http://gb.archive.ubuntu.com feisty/universe Packages
  404 Not Found
Err http://gb.archive.ubuntu.com feisty/universe Sources
  404 Not Found
Err http://gb.archive.ubuntu.com feisty/multiverse Packages
  404 Not Found
Err http://gb.archive.ubuntu.com feisty/multiverse Sources
  404 Not Found
Err http://gb.archive.ubuntu.com feisty-updates/main Packages
  404 Not Found
Err http://gb.archive.ubuntu.com feisty-updates/restricted Packages
  404 Not Found
Err http://gb.archive.ubuntu.com feisty-updates/main Sources
  404 Not Found
Err http://security.ubuntu.com feisty-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com feisty-security/universe Sources
  404 Not Found
Err http://security.ubuntu.com feisty-security/multiverse Packages
  404 Not Found
Err http://gb.archive.ubuntu.com feisty-updates/restricted Sources
  404 Not Found
Err http://security.ubuntu.com feisty-security/multiverse Sources
  404 Not Found
Get: 1 http://download.webmin.com sarge Release.gpg [189B]
Ign http://download.webmin.com sarge/contrib Translation-en_GB
Hit http://download.webmin.com sarge Release
Err http://download.webmin.com sarge Release

Get: 2 http://download.webmin.com sarge Release [4367B]
Ign http://download.webmin.com sarge Release
Ign http://download.webmin.com sarge/contrib Packages
Hit http://download.webmin.com sarge/contrib Packages
Fetched 4556B in 6s (682B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  404 Not Found
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  404 Not Found
Reading package lists... Done
W: GPG error: http://download.webmin.com sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D97A3AE911F63C51
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.




```

---

### Post by utnubuuser on 2009-03-05
Are these repositories still active?  I was under the impression Feisty's repos were closed now.  Quite sure they are for the desktop (closed), but couldn't tell ya for sure about the server version

---

### Post by seppl82 on 2009-03-05
I would also recomend to update to Hardy Heron (8.04)

---

### Post by matey3 on 2009-03-05
add these lines to your /etc/apt/sources.list file;

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse 

7.04 has been discontinued.

---

