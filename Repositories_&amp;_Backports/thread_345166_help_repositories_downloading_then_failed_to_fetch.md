---
title: "help repositories downloading then failed to fetch"
date: 2007-01-23
forum: Repositories &amp; Backports
---

### Post by michie86 on 2007-01-23
hello.. i tried to add extra repositories on my ubuntu 6.06.. i followed the instructions from editing my sources/list to finally typing 
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
sudo apt-get update
at the terminal and this is what happened.. at first there were 'err..' and 'could not resolve..' lines but then i think the process proceeded.. then when it was almost done, i think, i came acrros to these messages

gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:32 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages [24.8kB]
97% [32 Packages gzip 0]                                            2045B/s 58s
gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 4821kB in 42m0s (1913B/s)
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not resolve 'ph.security.ubuntu.com'

these are just some of the lines..
heres what's in my terminal during the whole process..

Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security Release.gpg
  Could not resolve 'ph.security.ubuntu.com'
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security Release
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/main Packages
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/restricted Packages
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/universe Packages
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/main Sources
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/restricted Sources
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/universe Sources
Ign [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/multiverse Sources
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/main Packages
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/restricted Packages
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/universe Packages
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/multiverse Packages
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/main Sources
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/restricted Sources
  Could not resolve 'ph.security.ubuntu.com'
Err [http://ph.archive.canonical.com](http://ph.archive.canonical.com) dapper-commercial Release.gpg
  Could not resolve 'ph.archive.canonical.com'
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/universe Sources
  Could not resolve 'ph.security.ubuntu.com'
Ign [http://ph.archive.canonical.com](http://ph.archive.canonical.com) dapper-commercial Release
Err [http://ph.security.ubuntu.com](http://ph.security.ubuntu.com) dapper-security/multiverse Sources
  Could not resolve 'ph.security.ubuntu.com'
Ign [http://ph.archive.canonical.com](http://ph.archive.canonical.com) dapper-commercial/main Packages
Err [http://ph.archive.canonical.com](http://ph.archive.canonical.com) dapper-commercial/main Packages
  Could not resolve 'ph.archive.canonical.com'
Get:1 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper Release.gpg [189B]
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper Release.gpg
  Could not resolve 'ph.medibuntu.sos-sts.com'
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper Release
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/free Packages
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/non-free Packages
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/free Sources
Ign [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/non-free Sources
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/free Packages
  Could not resolve 'ph.medibuntu.sos-sts.com'
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/non-free Packages
  Could not resolve 'ph.medibuntu.sos-sts.com'
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/free Sources
  Could not resolve 'ph.medibuntu.sos-sts.com'
Err [http://ph.medibuntu.sos-sts.com](http://ph.medibuntu.sos-sts.com) dapper/non-free Sources
  Could not resolve 'ph.medibuntu.sos-sts.com'
Get:2 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper Release [34.8kB]
Get:5 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release [50.9kB]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates Release
Get:6 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports Release [38.4kB]
Get:7 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/main Packages [619kB]
Get:8 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:9 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:10 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Get:11 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/main Sources [255kB]
Get:12 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:13 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/universe Sources [975kB]
Get:14 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources
Get:15 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/main Packages [131kB]
Get:16 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:17 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages [21.6kB]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages
Get:18 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/multiverse Packages [964B]
Get:19 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/main Sources [48.3kB]
Get:20 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:21 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Sources [3530B]
Get:22 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Get:23 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/main Packages [13.0kB]
Get:24 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:25 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/universe Packages [43.5kB]
Get:26 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/multiverse Packages [2486B]Get:27 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/main Sources [4308B]
Get:28 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:29 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/universe Sources [10.9kB]
Get:30 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-backports/multiverse Sources [2126B]
Get:31 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
97% [31 Sources gzip 0] [Connecting to ph.archive.ubuntu.com (195.248.90.35)]
gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:32 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages [24.8kB]
97% [32 Packages gzip 0]                                            2045B/s 58s
gzip: stdin: not in gzip format
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) dapper-updates/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 4821kB in 42m0s (1913B/s)
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/Release.gpg)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://ph.archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg)  Could not resolve 'ph.archive.canonical.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz](http://ph.security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz)  Could not resolve 'ph.security.ubuntu.com'
Failed to fetch [http://ph.archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz](http://ph.archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz)  Could not resolve 'ph.archive.canonical.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/free/binary-i386/Packages.gz)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.gz)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz](http://ph.medibuntu.sos-sts.com/repo/dists/dapper/non-free/source/Sources.gz)  Could not resolve 'ph.medibuntu.sos-sts.com'
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://ph.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://ph.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://ph.archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

i checked the synaptic manager and new things are there such as the one i need which is gnome-bluetooth.. but i'm wondering wether these "failed to fetch messages" would have some effects afterwards.. help? please? thanks in advance :D

---

### Post by gerdt on 2007-02-23
Hello, I have a similar problem, I've been looking for an answer for quite some time now, but I have only found a partial solution to my problem.

I have Kubuntu installed, Dapper.
This is my sources.list:

```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

deb ftp://nl.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src ftp://nl.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb ftp://nl.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src ftp://nl.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb ftp://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src ftp://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb ftp://nl.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src ftp://nl.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## Medibuntu - Ubuntu 6.06 LTS "dapper drake"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
[B]deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free
[/B]
```

And this is what I get after doing an apt-get update:

```
Get:1 http://medibuntu.sos-sts.com dapper Release.gpg [191B]
Hit http://medibuntu.sos-sts.com dapper Release
Hit ftp://nl.archive.ubuntu.com dapper Release.gpg
Hit ftp://nl.archive.ubuntu.com dapper-updates Release.gpg
Hit ftp://security.ubuntu.com dapper-security Release.gpg
Hit ftp://nl.archive.ubuntu.com dapper-backports Release.gpg
Get:2 ftp://nl.archive.ubuntu.com dapper Release [34.8kB]
Get:3 ftp://security.ubuntu.com dapper-security Release [50.9kB]
Get:4 ftp://nl.archive.ubuntu.com dapper-updates Release [50.9kB]
Hit ftp://security.ubuntu.com dapper-security/main Packages
Hit ftp://security.ubuntu.com dapper-security/restricted Packages
Hit http://medibuntu.sos-sts.com dapper/free Packages
Hit ftp://security.ubuntu.com dapper-security/universe Packages
Get:5 ftp://nl.archive.ubuntu.com dapper-backports Release [38.4kB]
Hit ftp://security.ubuntu.com dapper-security/multiverse Packages
Hit ftp://security.ubuntu.com dapper-security/main Sources
Hit ftp://security.ubuntu.com dapper-security/restricted Sources
Hit ftp://security.ubuntu.com dapper-security/universe Sources
Hit ftp://nl.archive.ubuntu.com dapper/main Packages
Hit ftp://nl.archive.ubuntu.com dapper/restricted Packages
Hit ftp://security.ubuntu.com dapper-security/multiverse Sources
Hit ftp://nl.archive.ubuntu.com dapper/universe Packages
Hit ftp://nl.archive.ubuntu.com dapper/multiverse Packages
Get:6 http://medibuntu.sos-sts.com dapper/non-free Packages [1671B]
Ign http://medibuntu.sos-sts.com dapper/non-free Packages
Hit ftp://nl.archive.ubuntu.com dapper/main Sources
Hit ftp://nl.archive.ubuntu.com dapper/restricted Sources
Get:7 http://medibuntu.sos-sts.com dapper/free Sources [880B]
Hit ftp://nl.archive.ubuntu.com dapper/universe Sources
99% [7 Sources bzip2 0] [Query] [Waiting for headers]
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://medibuntu.sos-sts.com dapper/free Sources
  Sub-process bzip2 returned an error code (2)
Hit ftp://nl.archive.ubuntu.com dapper/multiverse Sources
Hit http://medibuntu.sos-sts.com dapper/non-free Sources
Hit ftp://nl.archive.ubuntu.com dapper-updates/main Packages
Hit ftp://nl.archive.ubuntu.com dapper-updates/restricted Packages
Hit ftp://nl.archive.ubuntu.com dapper-updates/universe Packages
Hit ftp://nl.archive.ubuntu.com dapper-updates/multiverse Packages
Hit ftp://nl.archive.ubuntu.com dapper-updates/main Sources
Hit ftp://nl.archive.ubuntu.com dapper-updates/restricted Sources
Err http://medibuntu.sos-sts.com dapper/non-free Packages
  416 Unknown [IP: 88.191.30.43 80]
Hit ftp://nl.archive.ubuntu.com dapper-updates/universe Sources
Hit ftp://nl.archive.ubuntu.com dapper-updates/multiverse Sources
Hit ftp://nl.archive.ubuntu.com dapper-backports/main Packages
Hit ftp://nl.archive.ubuntu.com dapper-backports/restricted Packages
Hit ftp://nl.archive.ubuntu.com dapper-backports/universe Packages
Hit ftp://nl.archive.ubuntu.com dapper-backports/multiverse Packages
Hit ftp://nl.archive.ubuntu.com dapper-backports/main Sources
Hit ftp://nl.archive.ubuntu.com dapper-backports/restricted Sources
Hit ftp://nl.archive.ubuntu.com dapper-backports/universe Sources
Hit ftp://nl.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 176kB in 2s (72.9kB/s)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/free/source/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch http://medibuntu.sos-sts.com/repo/dists/dapper/non-free/binary-i386/Packages.gz  416 Unknown [IP: 88.191.30.43 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

These "bzip2"-problems have been partially solved. The problem I had een couple of weeks ago is that almost all sources gave the same problem. I solved it by changing my sources.list, I changed all http's into ftp's. This works perfectly now, with the exception of 
```
## Medibuntu - Ubuntu 6.06 LTS "dapper drake"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free
```
I suspect Medibunto not to have an ftp mirror. 

So my problem is: How can I solve this? And why does (K)ubuntu have problems with http in its sources.list???

I would appreciate it very much if someone could help me out! Thanx in advance!

---

### Post by MepisReign on 2007-02-24
I have no problems fetching the repos (all of them have been enabled, by me), but when I try to update the system or install, for example, skype, I receive a BREAK error. Are the repos down? or at least some of them?

MepisReign

Solution: Ok, I managed a way to get this working, just go here --> [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) 
Choose your location and OS version, then create the list, make a backup of your original list and replace it with the one created from the website above. Some of the repos provided by source-0-matic may not work, just delete them or disable them on the sources list (by placing # in front of the deb..).
You can edit your sources.list, if running ubuntu type: sudo gedit /etc/apt/sources.list
if your are running kubuntu (I do) type: sudo kate /etc/apt/sources.list

That way your are going to be able to update your system and also even install the W32 codecs ;)

Hoping this help someone and avoid people to smash their heads against a wall :)

Regards,

MepisReign

---

