---
title: "Backports and apt-get update wont work!"
date: 2005-12-13
forum: Ubuntu Backports
---

### Post by reloded on 2005-12-13
Hi guys.
Am as fresh as they come in Ubuntu and I am so stuck. I have googled, but no luck. I hope you guys can help me out.

I have been trying to install packages/codecs e.g mp3 support, but non so far has worked. I googled around and came to as far as opening backports etc. 
I do my thing and when I run "apt-get upgrade" I keep keep on getting errors the following as part of the long error;

[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

Then I came to this forum and read the "Getting started with Backports". I then edited the source.list file and added those two lines.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

When I ran the apt-get update command, I now get the following error

[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/binary-i386/Packages.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/source/Sources.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/source/Sources.gz:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

I feel that once I get this working then I will be able to install my packages and codecs especially Beep Media player which is what I was trying to do before I got stuck :confused: :mad: 

For your info, am using Breezy Badger (5.10). My internet connection is working fine and I can download anything through firefox.

My first post and is so long I doubt you can read to the end! sorry!

Thanks though.

---

### Post by ubuntu_demon on 2005-12-13
You can find my recommended breezy sources.list in my signature. It includes backports.

---

### Post by reloded on 2005-12-14
Thanks ubuntudeamon but I am still stuck. Could you decipher the following?

I got an automatically generated source.list from and it looks like this. The ftp links worked well and when I ran $apt-get update it installed some packages. But all the http:// won't work. I get the following error -after the source.list


SOURCE LIST

# Automatically generated sources.list
# [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

# Ubuntu supported packages (packages)
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu supported packages (sources)
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# Ubuntu community supported packages (packages)
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Ubuntu community supported packages (sources)
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

# Seveas' packages (packages)
deb [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas all

# Seveas' packages (sources)
deb-src [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas all

# Ubuntu backports project (packages)
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Ubuntu backports project (sources)
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) breezy main

# Cipherfunk multimedia packages (sources)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) breezy main


ERROR

@Loks:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy Release.gpg
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy Release
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates Release
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports Release
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/restricted Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/restricted Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/universe Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/multiverse Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/universe Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/multiverse Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/universe Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/multiverse Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/universe Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/multiverse Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/restricted Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/restricted Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/restricted Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/universe Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/multiverse Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/universe Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/multiverse Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/main Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/restricted Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/main Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/restricted Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/universe Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/multiverse Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/universe Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/multiverse Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/main Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/restricted Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/universe Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/multiverse Packages
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/main Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/restricted Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/universe Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/multiverse Sources
  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Err [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release.gpg
  Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26). - connect (111 Connection refused)
Ign [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas Release
Ign [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/all Packages
Ign [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/all Sources

Err [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/all Packages
  Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26). - connect (111 Connection refused)
Err [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/all Sources
  Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26). - connect (111 Connection refused)
Get:1 [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release.gpg [189B]
Hit [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release
Get:2 [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages
Get:3 [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Sources
Ign [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Sources
Hit [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Packages
Hit [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy/main Sources
Fetched 189B in 5s (32B/s)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg](http://seveas.ubuntulinux.nl/dists/breezy-seveas/Release.gpg)  Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/universe/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-updates/multiverse/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://jp.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  Could not connect to jp.archive.ubuntu.com:80 (133.11.205.121). - connect (111 Connection refused)
Failed to fetch [http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/binary-i386/Packages.gz](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/binary-i386/Packages.gz)  Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26). - connect (111 Connection refused)
Failed to fetch [http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/source/Sources.gz](http://seveas.ubuntulinux.nl/dists/breezy-seveas/all/source/Sources.gz)  Could not connect to seveas.ubuntulinux.nl:80 (83.160.7.26). - connect (111 Connection refused)
Reading package lists... Done
W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/universe Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-updates/multiverse Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/all Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_all_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/jp.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


My configuration.
I am in Japan thus am using jp country code and am behind a proxy, the internet (firefox-configured with proxy) is working well and I can download stuff. The ftp is working well. just that godamn http sources.

I have googled, looked at other similar problems in the forum but no. It just won't work. If I try to install .deb manually, then I will have to contend with getting the dependancies also which I don't think I can. Another 24 unproductive hours. I have learnt a lot of stuff in the process. But.... sigh.

cheers

---

### Post by ubuntu_demon on 2005-12-14
try removing the jp country code and use the general mirrors instead. Maybe it helps.

For the other repo's if they don't work try replacing them with some of mine.

Don't forget :
$sudo apt-get update

good luck!

---

### Post by reloded on 2005-12-15
**They finally have worked! yatta!**

That was one hell of a ride. It was a long awaited release. 
Here is the gospel.

My problem was in the proxy configuration. Unlike XP where when I set up internet explorer proxy settings then all other applications get the configuration, here no no no no.

Where to set up proxy:
1. mozilla: Edit-preferences-GeneralTab-Connections
2. Network proxy: System-preferences-Network Proxy
3. Synaptic manager: Settings-Preferences-NetworkTab
4. For the $ apt-get update to work; 
    i. you can keep on typing the following everytime before you run apt-get

export http_proxy="http://proxy.yourproxyname.xx.xx:8080"

or

   ii.  Edit the apt-get file
sudo gedit /etc/apt/apt.conf

Add the following line to that file

ACQUIRE {
http::proxy "http://proxy.yourproxyname.xx.xx:8080"
}

You can get a source.list file from the one recommended by ubuntudeamon above.

With that you are ready to roll!

I can now play mp3, dvd, wma. But thanks to Automatix which you can get the information here: -please read through carefully otherwise you will get stuck

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Thank arnie boy for that. It went flawlessly! Damn when will I have such skill?

Downside:
I tried to upgrade to firefox 1.5 using a wiki guide that you can get here;
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
But aftewards firefox would not start. I didn't have an alternative coz I couldn't even post my problem, or google about it so I did a fresh installation of Ubuntu! -something I thought I had left somewhere else.

So apart from that guide, what else can I do? I read somewhere this week that some hacker posted a warning this week to guys who haven't updated to firefox 1.5. He is targeting older users-just to make them upgrade. But that is not the issue. I just want 1.5.

Now, that I have my tunes set up-which was the goal in the first place- what next? I am a wannabe admin so can someone please tell me what is the next hurdle? All my hardware is configured correctly and things are looking flashy and dandy.

cheers.

---

### Post by ubuntu_demon on 2005-12-15
I'm glad. If pinging the servers hadn't worked next we would have dived together into your network settings (but I don't know much about proxies yet). Thnx for the info maybe this helps other users!

security fixes will always be "backported" into breezy using the official repos. So there's no need to go to firefox 1.5 for security. The reason firefox 1.5 isn't backported is that it may "break" your system since several applications depend on the 1.0.x core.

---

