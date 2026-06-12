---
title: "I am looking for a working Repository list for Ubuntu Dapper Amd64"
date: 2007-02-06
forum: Repositories &amp; Backports
---

### Post by Ouroboros_Beast on 2007-02-06
I am soo tired of my repository lists failing left and right, but i am moderately new at ubuntu so donot know whento/whichto delete. my repository list is long and obnoxious, and I am looking to completely replace it. unfortunately, most of the premade lists either don't work or are for 32bit procs, and i cannot use them. My first problem with my repositories, is pritty much anything that mentions security doesn't work [and i tried switching to ftp; and i tried editing them to fit existing pages; or isolating them so that they were the only repositries that i had] . 


my latest problem is i have a 'Broken Package' and i have no clue how to fix it, but i think it may have to do with my repeated repositries, or my incomplete repositry downloads, or my non-working repositries.

so i am looking for a list of repositries that i can use to completely replace mine. 

here is my current repositry list [yeah i know its ****** up and repeatative i was trying to fix **** without deleting it] [also if you have a list that doesn't acknowlage my programs that is fine i can add them accordingly more carefully now that i know a little more]

```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse





#####################################[ Changed http to ftp ]#######################################################
# Ubuntu supported packages (packages, GPG key: 437D05B5)
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release amd64 (20060806.1)]/ dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security restricted universe multiverse

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu/dapper main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/dapper-security main restricted universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
##################################################################################################################




# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://mirror.ubuntulinux.nl/ dapper-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

# bzr nightly snapshots
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free


# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/kde-latest dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/koffice-latest dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/koffice-latest dapper main

# ###this is only for edgy###kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb http://kubuntu.org/packages/amarok-latest dapper main

# ###this is only for edgy###kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src http://kubuntu.org/packages/amarok-latest dapper main

# Bazaar-NG development (packages, GPG key: 1F44842D)
deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu dapper-commercial main

# Cinelerra
deb http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./

## Official Deluge Repository
deb http://espergreen.com/apt dapper main

# James Cameron's PPTP GUI packaging
deb http://quozl.netrek.org/pptp/pptpconfig ./

deb http://www.getautomatix.com/apt dapper main

# GLX
deb http://www.beerorkid.com/compiz/ dapper main aiglx
deb http://xgl.compiz.info/ dapper main aiglx
deb http://ubuntu.compiz.net/ dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglx

```

here is what i get when i update apt-get 

```

Get:1 http://www.beerorkid.com dapper Release.gpg [189B]
Hit http://www.beerorkid.com dapper Release
Err http://www.beerorkid.com dapper Release

Get:2 http://www.beerorkid.com dapper Release [5402B]
Ign http://www.beerorkid.com dapper Release
Get:3 http://mirror.ubuntulinux.nl dapper-seveas Release.gpg [307B]
Hit http://mirror.ubuntulinux.nl dapper-seveas Release
Hit http://mirror.ubuntulinux.nl dapper-seveas/all Packages
Ign http://www.beerorkid.com dapper/main Packages
Ign http://www.beerorkid.com dapper/aiglx Packages
Hit http://www.beerorkid.com dapper/main Packages
Hit http://www.beerorkid.com dapper/aiglx Packages
Ign http://quozl.netrek.org ./ Release.gpg
Ign http://quozl.netrek.org ./ Release
Ign http://espergreen.com dapper Release.gpg
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Ign http://security.ubuntu.com main Release.gpg
Ign http://kubuntu.org dapper Release.gpg
Ign http://kubuntu.org dapper Release.gpg
Ign http://kubuntu.org dapper Release.gpg
Ign http://www.kiberpipa.org ./ Release.gpg
Err http://xgl.compiz.info dapper Release.gpg
  Could not connect to xgl.compiz.info:80 (195.14.0.203). - connect (111 Connect ion refused)
Err http://ubuntu.compiz.net dapper Release.gpg
  Temporary failure resolving 'ubuntu.compiz.net'
Ign http://quozl.netrek.org ./ Packages
Hit http://espergreen.com dapper Release
Get:5 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:6 http://medibuntu.sos-sts.com dapper Release.gpg [191B]
Get:7 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:8 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com main Release.gpg
Ign http://us.archive.ubuntu.com main Release.gpg
Hit http://security.ubuntu.com dapper-security Release
Ign http://kubuntu.org dapper Release
Get:9 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Hit http://quozl.netrek.org ./ Packages
Get:10 http://us.archive.ubuntu.com dapper-backports Release.gpg [191B]
Get:11 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Ign http://www.kiberpipa.org ./ Release
Ign http://espergreen.com dapper/main Packages
Ign http://kubuntu.org dapper Release
Hit http://espergreen.com dapper/main Packages
Ign http://security.ubuntu.com main Release
Hit http://medibuntu.sos-sts.com dapper Release
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper Release
Ign http://www.kiberpipa.org ./ Packages
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Ign http://kubuntu.org dapper Release
Ign http://us.archive.ubuntu.com main Release
Ign http://us.archive.ubuntu.com main Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://medibuntu.sos-sts.com dapper/free Packages
Ign http://kubuntu.org dapper/main Packages
Ign http://kubuntu.org dapper/main Sources
Hit http://www.kiberpipa.org ./ Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://medibuntu.sos-sts.com dapper/non-free Packages
Hit http://kubuntu.org dapper/main Packages
Hit http://kubuntu.org dapper/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Ign http://kubuntu.org dapper/main Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://security.ubuntu.com main/restricted Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Ign http://kubuntu.org dapper/main Sources
Err http://kubuntu.org dapper/main Packages
  404 Not Found
Err http://kubuntu.org dapper/main Sources
  404 Not Found
Ign http://security.ubuntu.com main/universe Packages
Ign http://security.ubuntu.com main/multiverse Packages
Err http://kubuntu.org dapper/main Packages
  404 Not Found
Err http://security.ubuntu.com main/restricted Packages
  404 Not Found
Ign http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Sources
Ign http://archive.ubuntu.com dapper/multiverse Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Err http://kubuntu.org dapper/main Sources
  404 Not Found
Err http://security.ubuntu.com main/universe Packages
  404 Not Found
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Err http://security.ubuntu.com main/multiverse Packages
  404 Not Found
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://us.archive.ubuntu.com dapper/multiverse Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/universe Packages
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/universe Packages
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Get:12 http://archive.ubuntu.com dapper/universe Packages [3143kB]
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Get:13 http://archive.ubuntu.com dapper/multiverse Sources [57.5kB]
99% [12 Packages gzip 0] [Waiting for headers] [Connecting to people.ubuntu.com
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/universe Packages
  Sub-process gzip returned an error code (1)
99% [13 Sources gzip 0] [Waiting for headers] [Connecting to people.ubuntu.com]
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Sources
Ign http://us.archive.ubuntu.com main/restricted Packages
Ign http://us.archive.ubuntu.com main/universe Packages
Ign http://us.archive.ubuntu.com main/multiverse Packages
Ign http://us.archive.ubuntu.com main/restricted Packages
Ign http://us.archive.ubuntu.com main/universe Packages
Ign http://us.archive.ubuntu.com main/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Err http://us.archive.ubuntu.com main/restricted Packages
  404 Not Found [IP: 195.248.90.35 80]
Err http://us.archive.ubuntu.com main/universe Packages
  404 Not Found [IP: 195.248.90.35 80]
Err http://us.archive.ubuntu.com main/multiverse Packages
  404 Not Found [IP: 195.248.90.35 80]
Err http://us.archive.ubuntu.com main/restricted Packages
  404 Not Found [IP: 195.248.90.35 80]
Err http://us.archive.ubuntu.com main/universe Packages
  404 Not Found [IP: 195.248.90.35 80]
Err http://us.archive.ubuntu.com main/multiverse Packages
  404 Not Found [IP: 195.248.90.35 80]
Get:14 http://www.getautomatix.com dapper Release.gpg [189B]
Get:15 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Ign http://people.ubuntu.com ./ Release.gpg
Hit http://www.getautomatix.com dapper Release
Hit http://archive.canonical.com dapper-commercial Release
Hit http://www.getautomatix.com dapper/main Packages
Hit http://people.ubuntu.com ./ Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Ign http://people.ubuntu.com ./ Packages
Ign http://people.ubuntu.com ./ Packages
Ign http://people.ubuntu.com ./ Sources
Hit http://people.ubuntu.com ./ Packages
Hit http://people.ubuntu.com ./ Packages
Hit http://people.ubuntu.com ./ Sources
Err http://media.blutkind.org dapper Release.gpg
  Could not connect to media.blutkind.org:80 (216.55.142.216), connection timed out
Fetched 5604B in 2m11s (43B/s)
Failed to fetch http://xgl.compiz.info/dists/dapper/Release.gpg Could not connec t to xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Failed to fetch http://ubuntu.compiz.net/dists/dapper/Release.gpg Temporary fail ure resolving 'ubuntu.compiz.net'
Failed to fetch http://media.blutkind.org/xgl/dists/dapper/Release.gpg Could not  connect to media.blutkind.org:80 (216.55.142.216), connection timed out
Failed to fetch http://kubuntu.org/packages/kde-latest/dists/dapper/main/binary- amd64/Packages.gz 404 Not Found
Failed to fetch http://kubuntu.org/packages/kde-latest/dists/dapper/main/source/ Sources.gz 404 Not Found
Failed to fetch http://kubuntu.org/packages/amarok-latest/dists/dapper/main/bina ry-amd64/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dapper-security/dists/main/res tricted/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://kubuntu.org/packages/amarok-latest/dists/dapper/main/sour ce/Sources.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dapper-security/dists/main/uni verse/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dapper-security/dists/main/mul tiverse/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-am d64/Packages.gz Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/ Sources.gz Sub-process gzip returned an error code (1)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper/dists/main/restricted /binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.35 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper/dists/main/universe/b inary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.35 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper/dists/main/multiverse /binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.35 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper-updates/dists/main/re stricted/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.35 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper-updates/dists/main/un iverse/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.35 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper-updates/dists/main/mu ltiverse/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.35 80]
Reading package lists... Done
W: GPG error: http://www.beerorkid.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97F ED8A569E
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used  instead.
probinso@probinso:~$ sudo apt-get update
Get:1 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Ign http://quozl.netrek.org ./ Release.gpg
Get:2 http://www.getautomatix.com dapper Release.gpg [189B]
Ign http://quozl.netrek.org ./ Release
Get:3 http://www.beerorkid.com dapper Release.gpg [189B]
Err http://xgl.compiz.info dapper Release.gpg
  Could not connect to xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Ign http://espergreen.com dapper Release.gpg
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Ign http://security.ubuntu.com main Release.gpg
Hit http://www.getautomatix.com dapper Release
Hit http://www.beerorkid.com dapper Release
Err http://www.beerorkid.com dapper Release

Ign http://quozl.netrek.org ./ Packages
Get:5 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:6 http://us.archive.ubuntu.com dapper-updates Release.gpg [191B]
Ign http://people.ubuntu.com ./ Release.gpg
Get:7 http://www.beerorkid.com dapper Release [5402B]
Hit http://espergreen.com dapper Release
Hit http://quozl.netrek.org ./ Packages
Hit http://security.ubuntu.com dapper-security Release
Ign http://www.beerorkid.com dapper Release
Hit http://www.getautomatix.com dapper/main Packages
Ign http://espergreen.com dapper/main Packages
Ign http://kubuntu.org dapper Release.gpg
Get:8 http://mirror.ubuntulinux.nl dapper-seveas Release.gpg [307B]
Get:9 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:10 http://archive.ubuntu.com dapper-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com main Release.gpg
Ign http://us.archive.ubuntu.com main Release.gpg
Get:11 http://us.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://people.ubuntu.com ./ Release
Ign http://www.kiberpipa.org ./ Release.gpg
Ign http://security.ubuntu.com main Release
Hit http://espergreen.com dapper/main Packages
Err http://ubuntu.compiz.net dapper Release.gpg
  Temporary failure resolving 'ubuntu.compiz.net'
Ign http://kubuntu.org dapper Release.gpg
Ign http://kubuntu.org dapper Release.gpg
Hit http://mirror.ubuntulinux.nl dapper-seveas Release
Ign http://people.ubuntu.com ./ Packages
Get:12 http://archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Ign http://us.archive.ubuntu.com main Release
Ign http://us.archive.ubuntu.com main Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Ign http://www.kiberpipa.org ./ Release
Ign http://kubuntu.org dapper Release
Ign http://people.ubuntu.com ./ Packages
Ign http://people.ubuntu.com ./ Sources
Hit http://mirror.ubuntulinux.nl dapper-seveas/all Packages
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Hit http://security.ubuntu.com dapper-security/main Packages
Ign http://kubuntu.org dapper Release
Hit http://people.ubuntu.com ./ Packages
Ign http://www.kiberpipa.org ./ Packages
Hit http://archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Ign http://kubuntu.org dapper Release
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/multiverse Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://security.ubuntu.com main/restricted Packages
Hit http://people.ubuntu.com ./ Packages
Hit http://www.kiberpipa.org ./ Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Ign http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Ign http://kubuntu.org dapper/main Packages
Ign http://security.ubuntu.com main/universe Packages
Ign http://security.ubuntu.com main/multiverse Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Ign http://archive.ubuntu.com dapper/multiverse Sources
Hit http://people.ubuntu.com ./ Sources
Hit http://archive.ubuntu.com dapper-updates/main Packages
Hit http://archive.ubuntu.com dapper-updates/restricted Packages
Err http://security.ubuntu.com main/restricted Packages
  404 Not Found
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://archive.ubuntu.com dapper-updates/main Sources
Hit http://archive.ubuntu.com dapper-updates/restricted Sources
Hit http://archive.ubuntu.com dapper-updates/universe Sources
Hit http://archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://archive.ubuntu.com dapper-backports/main Packages
Ign http://www.beerorkid.com dapper/main Packages
Err http://security.ubuntu.com main/universe Packages
  404 Not Found
Hit http://archive.ubuntu.com dapper-backports/restricted Packages
Hit http://us.archive.ubuntu.com dapper/multiverse Sources
Ign http://us.archive.ubuntu.com main/restricted Packages
Hit http://archive.ubuntu.com dapper-backports/universe Packages
Hit http://archive.ubuntu.com dapper-backports/multiverse Packages
Err http://security.ubuntu.com main/multiverse Packages
  404 Not Found
Ign http://kubuntu.org dapper/main Sources
Hit http://kubuntu.org dapper/main Packages
Hit http://kubuntu.org dapper/main Sources
Ign http://kubuntu.org dapper/main Packages
Hit http://archive.ubuntu.com dapper-backports/main Sources
Ign http://us.archive.ubuntu.com main/universe Packages
Ign http://us.archive.ubuntu.com main/multiverse Packages
Ign http://us.archive.ubuntu.com main/restricted Packages
Ign http://us.archive.ubuntu.com main/universe Packages
Ign http://us.archive.ubuntu.com main/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/universe Packages
Ign http://kubuntu.org dapper/main Sources
Hit http://archive.ubuntu.com dapper-backports/restricted Sources
Hit http://archive.ubuntu.com dapper-backports/universe Sources
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Get:13 http://archive.ubuntu.com dapper/universe Packages [3143kB]
Get:14 http://archive.ubuntu.com dapper/multiverse Sources [57.5kB]
99% [13 Packages gzip 0] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Connecting to media.blutkind.org (216.55.142.216)]   37.5kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/universe Packages
  Sub-process gzip returned an error code (1)
99% [14 Sources gzip 0] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Connecting to media.blutkind.org (216.55.142.216)]    37.5kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Err http://kubuntu.org dapper/main Packages
  404 Not Found
Err http://kubuntu.org dapper/main Sources
  404 Not Found
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/universe Packages
Err http://kubuntu.org dapper/main Packages
  404 Not Found
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Packages
Err http://kubuntu.org dapper/main Sources
  404 Not Found
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-updates/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/multiverse Sources
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Err http://us.archive.ubuntu.com main/restricted Packages
  404 Not Found [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com main/universe Packages
  404 Not Found [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com main/multiverse Packages
  404 Not Found [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com main/restricted Packages
  404 Not Found [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com main/universe Packages
  404 Not Found [IP: 195.248.90.38 80]
Err http://us.archive.ubuntu.com main/multiverse Packages
  404 Not Found [IP: 195.248.90.38 80]
Ign http://www.beerorkid.com dapper/aiglx Packages
Get:15 http://medibuntu.sos-sts.com dapper Release.gpg [191B]
Hit http://www.beerorkid.com dapper/main Packages
Hit http://www.beerorkid.com dapper/aiglx Packages
Hit http://medibuntu.sos-sts.com dapper Release
Hit http://medibuntu.sos-sts.com dapper/free Packages
Hit http://medibuntu.sos-sts.com dapper/non-free Packages
Err http://media.blutkind.org dapper Release.gpg
  Could not connect to media.blutkind.org:80 (216.55.142.216), connection timed out
Fetched 5604B in 2m0s (47B/s)
Failed to fetch http://xgl.compiz.info/dists/dapper/Release.gpg Could not connect to xgl.compiz.info:80 (195.14.0.203). - connect (111 Connection refused)
Failed to fetch http://ubuntu.compiz.net/dists/dapper/Release.gpg Temporary failure resolving 'ubuntu.compiz.net'
Failed to fetch http://media.blutkind.org/xgl/dists/dapper/Release.gpg Could not connect to media.blutkind.org:80 (216.55.142.216), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dapper-security/dists/main/restricted/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-amd64/Packages.gz Sub-process gzip returned an error code (1)
Failed to fetch http://kubuntu.org/packages/kde-latest/dists/dapper/main/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dapper-security/dists/main/universe/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://security.ubuntu.com/ubuntu/dapper-security/dists/main/multiverse/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz Sub-process gzip returned an error code (1)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper/dists/main/restricted/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://kubuntu.org/packages/kde-latest/dists/dapper/main/source/Sources.gz 404 Not Found
Failed to fetch http://kubuntu.org/packages/amarok-latest/dists/dapper/main/binary-amd64/Packages.gz 404 Not Found
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper/dists/main/universe/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper/dists/main/multiverse/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper-updates/dists/main/restricted/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper-updates/dists/main/universe/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dapper-updates/dists/main/multiverse/binary-amd64/Packages.gz 404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://kubuntu.org/packages/amarok-latest/dists/dapper/main/source/Sources.gz 404 Not Found
Reading package lists... Done
W: GPG error: http://www.beerorkid.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.

```


unfortunately it looks like alot of them work but there are many doubles and i have a lot of trouble identifying most of them 

help?





additionall

i have run into this while trying to use apt-get as of late, it looks like something about the broken file, 


```

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.

```

but i've tried force installs for the package listed and nothing happens

---

### Post by nalioth on 2007-02-06
You can find a default sources.list at [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by Ouroboros_Beast on 2007-02-06
Thank you for pointing me to that site, i have cleaned up my repositry list and it seems to at least update much cleaner; now my only problem is that i cannot 
```
 apt-get upgrade 
```

i end up with 

```


sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed

[INDENT][/INDENT]:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
16 not fully installed or removed.
Need to get 0B/3399kB of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::SpacerItem', <> line 1 during global destruction.
Preconfiguring packages ...
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 4.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 6.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.
(Reading database ... 147163 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu3.2_amd64.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
probinso@probinso:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  samba: Depends: samba-common (= 3.0.22-1ubuntu3.1) but 3.0.22-1ubuntu3.2 is installed
E: Unmet dependencies. Try using -f.
[INDENT][/INDENT]:~$




```

---

### Post by Ouroboros_Beast on 2007-02-06
horray, ok sorry for the reposts, i fixed the samba problem from another forum discussion


[http://www.ubuntuforums.org/showthread.php?t=215070&highlight=broken+package+samba](http://www.ubuntuforums.org/showthread.php?t=215070&highlight=broken+package+samba)

---

