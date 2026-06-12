---
title: "Having trouble with 'apt-get update' after editing /etc/apt/sources.list"
date: 2005-04-22
forum: Repositories &amp; Backports
---

### Post by ed_agamemnon on 2005-04-22
Hi!

right, i'm having some trouble downloading packages from the repository servers after editing my sources.list file (in /etc/apt) in the way that ubuntuguide.org suggests...


firstly
this is what i get before i make the change my .sources file:


the UNCHANGED file:
>  
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


and this is the output it gives me...

> 
ed@ubuntu:/etc/apt$ sudo apt-get update
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/restricted Sources
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Fetched 2B in 6s (0B/s)
Reading package lists... Done


all well and good so far...

however ubuntuguide.org wants me to edit this sources.list file (i'm not really sure why)... so i change my file to (as suggested, but possibly mis-interpreted) to:

(the EDITED version of sources.list)
> 
#deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main


but this new file produces the following output when i run 'apt-get update':

(output from NEW sources.list:)
> 
ed@ubuntu:/etc/apt$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages [14B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources [14B]
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary/restricted Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release [19.9kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages [490kB]
Get:10 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg [189B]
Get:11 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg [189B]
Get:12 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg [189B]
Get:13 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release [1348B]
Get:14 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release [2528B]
Get:15 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release [1349B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:17 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages [16.5kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release.gpg
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources [175kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release.gpg
Get:19 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages [17.8kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release
Get:20 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages [14.8kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras Release
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources [1320B]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages [2169kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release [19.9kB]
Ign [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages [88.4kB]
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/main Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/universe Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/multiverse Packages
  500 Internal Server Error
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources [48.4kB]
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports/restricted Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/main Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/universe Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages
  500 Internal Server Error
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages
  500 Internal Server Error
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources [857kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages [2837B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages [14B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources [885B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources [14B]
Fetched 3949kB in 60s (65.7kB/s)
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz)  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz)  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz)  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz)  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz)  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz)  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz)  500 Internal Server Error
Failed to fetch [http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz)  500 Internal Server Error
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



what are all thes 500 Internal Server Error messages? - a problem my end? with the servers? anything to worry about?

all the other times i have installed ubuntu i have never encountered this problem and every time i have edited the sources.list file in the manner that ubuntuguide.org suggests.

the only differences with this install are:

1 - installing to a laptop
2 - not installing from CD but a net install (works fine though)

someone please put me on the right lines, i'm a little confused :S

thanks :)
-ed.

---

### Post by A-star on 2005-04-22
At this moment there are some problems with the backports servers.
Don't worry about the error messages as they are normal at this moment.

They will go away as the servers will come back online.

---

### Post by ed_agamemnon on 2005-04-22
ahh thankyou :)

---

