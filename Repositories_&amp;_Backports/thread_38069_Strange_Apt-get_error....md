---
title: "Strange Apt-get error..."
date: 2005-05-29
forum: Repositories &amp; Backports
---

### Post by petesmc on 2005-05-29
Hi,

I'm new to all this, and i was trying to run apt-get update but i got lots of errors. It usually works, just not for the past few hours.

```

Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://security.ubuntu.com hoary-security Release [16.9kB]
Hit ftp://ftp.nerim.net stable Release.gpg
Hit ftp://ftp.nerim.net unstable Release.gpg
Ign http://backports.ubuntuforums.org hoary-backports Release.gpg
Ign http://backports.ubuntuforums.org hoary-extras Release.gpg
Hit ftp://ftp.nerim.net testing Release.gpg
Get:3 ftp://ftp.nerim.net stable Release [1348B]
Ign http://backports.ubuntuforums.org hoary-backports Release
Get:4 ftp://ftp.nerim.net unstable Release [2528B]
Ign http://backports.ubuntuforums.org hoary-extras Release
Ign http://backports.ubuntuforums.org hoary-backports/main Packages
Ign http://backports.ubuntuforums.org hoary-backports/universe Packages
Ign http://backports.ubuntuforums.org hoary-backports/multiverse Packages
Ign http://backports.ubuntuforums.org hoary-backports/restricted Packages
Ign http://backports.ubuntuforums.org hoary-extras/main Packages
Ign http://backports.ubuntuforums.org hoary-extras/universe Packages
Ign http://backports.ubuntuforums.org hoary-extras/multiverse Packages
Ign http://backports.ubuntuforums.org hoary-extras/restricted Packages
Err http://backports.ubuntuforums.org hoary-backports/main Packages
  403 Forbidden
Err http://backports.ubuntuforums.org hoary-backports/universe Packages
  403 Forbidden
Err http://backports.ubuntuforums.org hoary-backports/multiverse Packages
  403 Forbidden
Err http://backports.ubuntuforums.org hoary-backports/restricted Packages
  403 Forbidden
Err http://backports.ubuntuforums.org hoary-extras/main Packages
  403 Forbidden
Err http://backports.ubuntuforums.org hoary-extras/universe Packages
  403 Forbidden
Err http://backports.ubuntuforums.org hoary-extras/multiverse Packages
  403 Forbidden
Err http://backports.ubuntuforums.org hoary-extras/restricted Packages
  403 Forbidden
Hit ftp://ftp.nerim.net testing Release
Get:5 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Hit ftp://ftp.nerim.net stable/main Packages
Hit ftp://ftp.nerim.net unstable/main Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Hit ftp://ftp.nerim.net testing/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://us.archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/multiverse Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary/multiverse Sources
Fetched 20.9kB in 4s (4635B/s)
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz  403 Forbidden
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by equilibrium on 2005-05-29
I am getting 403 on backports atm also :( was just about to leave my system upgrading a few packages but all of them get 403  :? 

Browsing the backports repository does the same :( 'access denied'

---

### Post by lonetree on 2005-05-30
I am getting the same problem also, found this problem when I was about to install realplayer.

Btw, anyone has problem with mozilla Mplayer plugin problem here? It seems that firefox always being thrown out when plugin activated.

regards.

I like ubuntu, found this the best at the moment.

---

### Post by svizi on 2005-05-30
[QUOTE=lonetree]I am getting the same problem also, found this problem when I was about to install realplayer.

Btw, anyone has problem with mozilla Mplayer plugin problem here? It seems that firefox always being thrown out when plugin activated.

regards.

I like ubuntu, found this the best at the moment.[/QUOTE]
 Same problems here. Plus some more?


E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
stefanos@ubuntu:~$ sudo apt-get update
Password:
Ign [http://download.videolan.org](http://download.videolan.org) sid Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://download.videolan.org](http://download.videolan.org) sid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:5 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg [189B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release.gpg
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release.gpg
Ign [http://download.videolan.org](http://download.videolan.org) sid/main Packages
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release
Ign [http://download.videolan.org](http://download.videolan.org) sid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release
Hit [http://download.videolan.org](http://download.videolan.org) sid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://download.videolan.org](http://download.videolan.org) sid/main Sources
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages
  403 Forbidden
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages
  403 Forbidden
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages
  403 Forbidden
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages
  403 Forbidden
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
  403 Forbidden
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
  403 Forbidden
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
  403 Forbidden
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
  403 Forbidden
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages [2853kB]
99% [8 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 34.3kB in 29s (1165B/s)
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-backports/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/universe/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/ubp/dists/hoary-extras/restricted/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by kvidell on 2005-05-30
[http://ubuntuforums.org/showthread.php?t=37525](http://ubuntuforums.org/showthread.php?t=37525)

There's new mirrors for backports.
Read that thread and update your /etc/apt/sources.list files accordingly, and run an apt-get update
- Kev

---

