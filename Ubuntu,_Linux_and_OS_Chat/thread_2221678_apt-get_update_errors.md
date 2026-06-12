---
title: "apt-get update errors"
date: 2014-05-03
forum: Ubuntu, Linux and OS Chat
---

### Post by robert_2 on 2014-05-03
Hi all

Just updated from Mint 16 to Pingguy Mini 14.04 and am getting some strange errors from apt-get update.

Ive tried adding the keys for each ID but with no luck.

```
[robert:/home/robert] $ sudo apt-get update
[sudo] password for robert: 
Ign http://archive.canonical.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Get:1 http://plex.r.worldssl.net lucid InRelease [2,146 B] 
Get:2 http://archive.canonical.com trusty Release.gpg [933 B] 
Get:3 http://extras.ubuntu.com trusty Release.gpg [72 B] 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://dl.google.com stable InRelease 
Get:4 http://repository.spotify.com stable InRelease [2,979 B] 
Ign http://plex.r.worldssl.net lucid InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Hit http://archive.canonical.com trusty Release 
Hit http://extras.ubuntu.com trusty Release 
Ign http://dl.google.com stable InRelease 
Ign http://repository.spotify.com stable InRelease 
Ign http://archive.canonical.com trusty Release 
Ign http://ppa.launchpad.net trusty InRelease 
Hit http://repo.steampowered.com alchemist InRelease 
Ign http://extras.ubuntu.com trusty Release 
Get:5 http://dl.google.com stable Release.gpg [198 B] 
Ign http://archive.canonical.com trusty/partner amd64 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://extras.ubuntu.com trusty/main amd64 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://archive.canonical.com trusty/partner i386 Packages/DiffIndex 
Get:6 http://dl.google.com stable Release.gpg [198 B] 
Ign http://extras.ubuntu.com trusty/main i386 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://plex.r.worldssl.net lucid/main amd64 Packages/DiffIndex 
Hit http://dl.google.com stable Release 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://dl.google.com stable Release 
Get:7 http://liquorix.net sid InRelease [6,714 B] 
Ign http://archive.ubuntu.com trusty InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://liquorix.net sid InRelease 
Hit http://dl.google.com stable Release 
Hit http://archive.canonical.com trusty/partner amd64 Packages 
Hit http://extras.ubuntu.com trusty/main amd64 Packages 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://dl.google.com stable Release 
Hit http://archive.canonical.com trusty/partner i386 Packages 
Ign http://plex.r.worldssl.net lucid/main i386 Packages/DiffIndex 
Hit http://extras.ubuntu.com trusty/main i386 Packages 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex 
Get:8 ftp://ftp.videolan.org ./ InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://packages.linuxmint.com debian InRelease 
Ign http://dl.google.com stable/main i386 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://liquorix.net sid/main amd64 Packages/DiffIndex 
Ign http://archive.ubuntu.com trusty-updates InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://linux.dropbox.com trusty InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Ign ftp://ftp.videolan.org ./ InRelease 
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex 
Ign http://archive.canonical.com trusty/partner Translation-en_GB 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://extras.ubuntu.com trusty/main Translation-en_GB 
Get:9 http://archive.getdeb.net trusty-getdeb InRelease [8,125 B] 
Ign http://archive.canonical.com trusty/partner Translation-en 
Ign http://liquorix.net sid/main i386 Packages/DiffIndex 
Ign http://archive.ubuntu.com trusty-backports InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://dl.google.com stable/main i386 Packages/DiffIndex 
Ign http://extras.ubuntu.com trusty/main Translation-en 
Ign http://archive.getdeb.net trusty-getdeb InRelease 
Get:10 http://packages.linuxmint.com debian Release.gpg [198 B] 
Ign http://ppa.launchpad.net trusty InRelease 
Get:11 ftp://ftp.videolan.org ./ Release.gpg [287 B] 
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex 
Ign http://ppa.launchpad.net saucy InRelease 
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://archive.ubuntu.com trusty-security InRelease 
Hit http://dl.google.com stable/main amd64 Packages 
Get:12 http://linux.dropbox.com trusty Release.gpg [489 B] 
Hit http://dl.google.com stable/main i386 Packages 
Ign http://ppa.launchpad.net trusty InRelease 
Get:13 http://packages.linuxmint.com debian Release [16.8 kB] 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Get:14 http://archive.ubuntu.com trusty Release.gpg [933 B] 
Ign http://ppa.launchpad.net trusty InRelease 
Hit http://dl.google.com stable/main amd64 Packages 
Ign http://ppa.launchpad.net trusty InRelease 
Hit ftp://ftp.videolan.org ./ Release 
Ign http://ppa.launchpad.net trusty InRelease 
Ign ftp://ftp.videolan.org ./ Release 
Hit http://dl.google.com stable/main i386 Packages 
Ign http://ppa.launchpad.net trusty InRelease 
Get:15 http://archive.ubuntu.com trusty-updates Release.gpg [933 B] 
Ign http://ppa.launchpad.net trusty InRelease 
Get:16 http://linux.dropbox.com trusty Release [2,601 B] 
Ign http://linux.dropbox.com trusty Release 
Ign http://ppa.launchpad.net trusty InRelease 
Err http://packages.linuxmint.com debian Release 
 
Get:17 ftp://ftp.videolan.org ./ Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty InRelease 
Ign http://ppa.launchpad.net trusty InRelease 
Get:18 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Get:19 http://archive.getdeb.net saucy-getdeb InRelease [8,129 B] 
Get:20 http://archive.ubuntu.com trusty-backports Release.gpg [933 B] 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign http://archive.getdeb.net saucy-getdeb InRelease 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign ftp://ftp.videolan.org ./ Packages/DiffIndex 
Get:21 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Hit http://repo.steampowered.com alchemist/non-free amd64 Packages 
Hit http://ppa.launchpad.net trusty Release.gpg 
Get:22 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Ign http://linux.dropbox.com trusty/main amd64 Packages/DiffIndex 
Get:23 http://archive.ubuntu.com trusty-security Release.gpg [933 B] 
Hit http://ppa.launchpad.net trusty Release.gpg 
Get:24 ftp://ftp.videolan.org ./ Translation-en_GB 
Get:25 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Hit http://ppa.launchpad.net trusty Release.gpg 
Get:26 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://archive.ubuntu.com trusty Release 
Ign http://archive.ubuntu.com trusty Release 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign http://linux.dropbox.com trusty/main i386 Packages/DiffIndex 
Ign http://dl.google.com stable/main Translation-en_GB 
Get:27 ftp://ftp.videolan.org ./ Translation-en 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign http://dl.google.com stable/main Translation-en 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign http://dl.google.com stable/main Translation-en_GB 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign http://dl.google.com stable/main Translation-en 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://archive.ubuntu.com trusty-backports Release 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign http://archive.ubuntu.com trusty-backports Release 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://ppa.launchpad.net saucy Release.gpg 
Hit http://plex.r.worldssl.net lucid/main amd64 Packages 
Hit ftp://ftp.videolan.org ./ Packages 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://plex.r.worldssl.net lucid/main i386 Packages 
Get:28 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://repo.steampowered.com alchemist/non-free i386 Packages 
Get:29 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Get:30 ftp://ftp.videolan.org ./ Translation-en_GB 
Get:31 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Get:32 http://ppa.launchpad.net trusty Release.gpg [316 B] 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign http://plex.r.worldssl.net lucid/main Translation-en_GB 
Ign http://archive.ubuntu.com trusty/main amd64 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://ppa.launchpad.net trusty Release.gpg 
Ign http://plex.r.worldssl.net lucid/main Translation-en 
Ign http://archive.ubuntu.com trusty/restricted amd64 Packages/DiffIndex 
Get:33 ftp://ftp.videolan.org ./ Translation-en 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://ppa.launchpad.net trusty Release.gpg 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Get:34 http://linux.dropbox.com trusty/main amd64 Packages [1,143 B] 
Ign http://archive.ubuntu.com trusty/universe amd64 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty Release 
Get:35 ftp://ftp.videolan.org ./ Translation-en_GB 
Hit http://ppa.launchpad.net trusty Release 
Ign http://archive.ubuntu.com trusty/multiverse amd64 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty Release 
Get:36 http://linux.dropbox.com trusty/main i386 Packages [1,143 B] 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://archive.ubuntu.com trusty/main i386 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://liquorix.net sid/main amd64 Packages 
Hit http://ppa.launchpad.net trusty Release 
Get:37 ftp://ftp.videolan.org ./ Translation-en 
Ign http://archive.ubuntu.com trusty/restricted i386 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty Release 
Hit http://liquorix.net sid/main i386 Packages 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://archive.ubuntu.com trusty/universe i386 Packages/DiffIndex 
Hit http://ppa.launchpad.net saucy Release 
Ign http://liquorix.net sid/main Translation-en_GB 
Get:38 ftp://ftp.videolan.org ./ Translation-en_GB 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://archive.ubuntu.com trusty/multiverse i386 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty Release 
Ign http://liquorix.net sid/main Translation-en 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Get:39 ftp://ftp.videolan.org ./ Translation-en 
Hit http://archive.ubuntu.com trusty/main Translation-en_GB 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Hit http://ppa.launchpad.net trusty Release 
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex 
Hit http://archive.ubuntu.com trusty/main Translation-en 
Get:40 ftp://ftp.videolan.org ./ Translation-en_GB 
Hit http://archive.ubuntu.com trusty/multiverse Translation-en_GB 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://archive.ubuntu.com trusty/multiverse Translation-en 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign ftp://ftp.videolan.org ./ Translation-en_GB 
Hit http://archive.ubuntu.com trusty/restricted Translation-en_GB 
Ign http://archive.getdeb.net trusty-getdeb/apps amd64 Packages/DiffIndex 
Get:41 ftp://ftp.videolan.org ./ Translation-en 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://archive.ubuntu.com trusty/restricted Translation-en 
Ign http://linux.dropbox.com trusty/main Translation-en_GB 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign ftp://ftp.videolan.org ./ Translation-en 
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex 
Hit http://archive.ubuntu.com trusty/universe Translation-en_GB 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Ign http://linux.dropbox.com trusty/main Translation-en 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty/universe Translation-en 
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex
Ign http://archive.getdeb.net trusty-getdeb/apps i386 Packages/DiffIndex
Get:42 http://archive.ubuntu.com trusty-updates Release [58.5 kB]
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex 
Err http://archive.ubuntu.com trusty-updates Release 
 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://archive.ubuntu.com trusty-backports/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex 
Ign http://archive.ubuntu.com trusty-backports/restricted amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://archive.ubuntu.com trusty-backports/universe amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages/DiffIndex
Ign http://archive.getdeb.net saucy-getdeb/games amd64 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://archive.ubuntu.com trusty-backports/main i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://archive.getdeb.net saucy-getdeb/games i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Ign http://archive.ubuntu.com trusty-backports/restricted i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Ign http://archive.ubuntu.com trusty-backports/universe i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://archive.ubuntu.com trusty-backports/multiverse i386 Packages/DiffIndex
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty-backports/main Translation-en
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://ppa.launchpad.net saucy/main amd64 Packages
Hit http://ppa.launchpad.net saucy/main i386 Packages
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex 
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Get:43 http://archive.ubuntu.com trusty-security Release [58.5 kB] 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Err http://archive.ubuntu.com trusty-security Release 
 
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty/universe amd64 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty/main i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://archive.ubuntu.com trusty/restricted i386 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.getdeb.net saucy-getdeb/games amd64 Packages 
Hit http://archive.ubuntu.com trusty/universe i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.getdeb.net saucy-getdeb/games i386 Packages 
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages 
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages 
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages 
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages 
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Hit http://ppa.launchpad.net trusty/main amd64 Packages 
Hit http://ppa.launchpad.net trusty/main i386 Packages 
Ign http://archive.ubuntu.com trusty-backports/main Translation-en_GB 
Ign http://archive.ubuntu.com trusty-backports/multiverse Translation-en_GB 
Ign http://archive.ubuntu.com trusty-backports/restricted Translation-en_GB 
Ign http://archive.ubuntu.com trusty-backports/universe Translation-en_GB 
Hit http://repository.spotify.com stable/non-free amd64 Packages 
Hit http://repository.spotify.com stable/non-free i386 Packages 
Ign http://repository.spotify.com stable/non-free Translation-en_GB 
Ign http://repository.spotify.com stable/non-free Translation-en 
Ign http://repo.steampowered.com alchemist/non-free Translation-en_GB 
Ign http://repo.steampowered.com alchemist/non-free Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://archive.getdeb.net saucy-getdeb/games Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://ppa.launchpad.net trusty/main Translation-en 
Ign http://ppa.launchpad.net trusty/main Translation-en_GB 
Ign http://archive.getdeb.net saucy-getdeb/games Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net saucy/main Translation-en_GB
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_GB
Ign http://ppa.launchpad.net trusty/main Translation-en
Fetched 176 kB in 13s (13.4 kB/s)
Reading package lists... Done
W: GPG error: http://plex.r.worldssl.net lucid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43525C28E533491A
W: GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://liquorix.net sid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EFF4F272FB2CD80
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://archive.getdeb.net trusty-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: ftp://ftp.videolan.org ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9
W: GPG error: http://linux.dropbox.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://packages.linuxmint.com debian Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3EE67F3D0FF405B2

W: GPG error: http://archive.getdeb.net saucy-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: GPG error: http://archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.ubuntu.com trusty-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 608BF7B93528AE20
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D2BF771175034BEC
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C1C5C63BF0E0B4E7
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2B3F92F902D65EFF
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 596D65AB5F0D930C
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

W: Failed to fetch http://packages.linuxmint.com/dists/debian/Release 

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release 

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty-security/Release 

W: Some index files failed to download. They have been ignored, or old ones used instead.
[robert:/home/robert] 20s $ 
```


Any ideas?

---

### Post by bapoumba on 2014-05-03
Moved to Other OS Chat.

---

