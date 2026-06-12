---
title: "unable to fix repository problems"
date: 2005-11-29
forum: Repositories &amp; Backports
---

### Post by Beau on 2005-11-29
Hello,

I'm unable to fetch all repositories. I tried different ones, tried the static DNS thing I found on this forum but nothing seems to help.

Below is the output of sudo apt-get update

```
sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security/restricted Packages
Get:6 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Hit http://security.ubuntu.com breezy-security/main Sources
Get:7 http://archive.ubuntu.com breezy-backports Release [19.6kB]
Hit http://security.ubuntu.com breezy-security/restricted Sources
Ign http://archive.ubuntu.com breezy-backports Release
Ign http://archive.ubuntu.com breezy/main Packages
Hit http://security.ubuntu.com breezy-security/universe Packages
Ign http://archive.ubuntu.com breezy/restricted Packages
Ign http://archive.ubuntu.com breezy/main Sources
Ign http://archive.ubuntu.com breezy/restricted Sources
Hit http://security.ubuntu.com breezy-security/universe Sources
Get:8 http://archive.ubuntu.com breezy/universe Packages [2238kB]
Ign http://archive.ubuntu.com breezy/universe Packages
Get:9 http://archive.ubuntu.com breezy/universe Sources [914kB]
Ign http://archive.ubuntu.com breezy/universe Sources
Ign http://archive.ubuntu.com breezy/multiverse Packages
Ign http://archive.ubuntu.com breezy/multiverse Sources
Ign http://archive.ubuntu.com breezy-updates/main Packages
Ign http://archive.ubuntu.com breezy-updates/restricted Packages
Get:10 http://archive.ubuntu.com breezy-updates/main Sources [5088B]
Ign http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Ign http://archive.ubuntu.com breezy-backports/universe Packages
Ign http://archive.ubuntu.com breezy-backports/multiverse Packages
Get:11 http://archive.ubuntu.com breezy/main Packages [764kB]
20% [11 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/main Packages
  Sub-process gzip returned an error code (1)
Hit http://archive.ubuntu.com breezy/restricted Packages
Get:12 http://archive.ubuntu.com breezy/main Sources [305kB]
26% [12 Sources gzip 0] [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/main Sources
  Sub-process gzip returned an error code (1)
Err http://archive.ubuntu.com breezy/restricted Sources
  416 Requested Range Not Satisfiable [IP: 82.211.81.182 80]
Err http://archive.ubuntu.com breezy/universe Packages
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Get:13 http://archive.ubuntu.com breezy/universe Sources [1223kB]
Err http://archive.ubuntu.com breezy/universe Sources
  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Get:14 http://archive.ubuntu.com breezy/multiverse Packages [99.1kB]
21% [14 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/multiverse Packages
  Sub-process gzip returned an error code (1)
Get:15 http://archive.ubuntu.com breezy/multiverse Sources [58.0kB]
22% [15 Sources gzip 0] [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:16 http://archive.ubuntu.com breezy-updates/main Packages [20.4kB]
23% [16 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy-updates/main Packages
  Sub-process gzip returned an error code (1)
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Get:17 http://archive.ubuntu.com breezy-updates/main Sources [5058B]
23% [17 Sources gzip 0] [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy-updates/main Sources
  Sub-process gzip returned an error code (1)
Get:18 http://archive.ubuntu.com breezy-backports/universe Packages [21.5kB]
23% [18 Packages gzip 0] [Connecting to archive.ubuntu.com (82.211.81.182)]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com breezy-backports/universe Packages
  Sub-process gzip returned an error code (1)
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 43.4kB in 10s (4083B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-amd64/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz  416 Requested Range Not Satisfiable [IP: 82.211.81.182 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-amd64/Packages.gz  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz  Error reading from server - read (104 Connection reset by peer) [IP: 82.211.81.182 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-amd64/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-amd64/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-amd64/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

This is my sources.list

```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 
```

I'm running kubuntu breezy amd64
What could be the problem?


Thanks,
Beau

---

### Post by jvictor on 2005-11-29
Have u disabled ipv6 ? I too had this problem, I disabled IPV6 and used static DNS now things work fine .. Plz search the forum "disable ipv6" HTH

---

### Post by Beau on 2005-11-29
I disabled IPv6 but still get the same error :???:

---

### Post by dudus on 2005-11-29
I found this a common issue. Juyst wait a few hours and then try again. The repos are down sometimes

---

### Post by Beau on 2005-11-30
Hi,

The errors remain today so I guess the problem must lay somewhere else.:(

---

