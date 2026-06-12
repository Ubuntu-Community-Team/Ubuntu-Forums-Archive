---
title: "Repository down?"
date: 2006-10-26
forum: Repositories &amp; Backports
---

### Post by evilmonkey on 2006-10-26
Hello, 

I've been trying for the past over 12 hours to connect to the archive repository. I've tried to connect through a number of different countries. Nothing, I cannot connect. Here's the output from apt-get update.

```
root@vitali-server:~# apt-get update
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://archive.ubuntu.com dapper Release [34.8kB]
Get:4 http://archive.ubuntu.com dapper-updates Release [30.9kB]
Get:5 http://archive.ubuntu.com dapper/main Packages [619kB]
Get:6 http://archive.ubuntu.com dapper/restricted Packages [4571B]
Get:7 http://archive.ubuntu.com dapper/main Sources [255kB]
Get:8 http://archive.ubuntu.com dapper/restricted Sources [1478B]
Get:9 http://archive.ubuntu.com dapper-updates/main Packages [126kB]
Get:10 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:11 http://archive.ubuntu.com dapper-updates/main Sources [47.4kB]
Get:12 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Fetched 1120kB in 2m9s (8675B/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Can someone tell me what's wrong? I'm posting my sources.list as well (this is an ubuntu server)

```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted unive$
## deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted u$

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
## deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
## deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

Can someone please tell me what's wrong? I cannot do anything without these repos.

Thanks.

---

