---
title: "au.archive.ubuntu.com down??"
date: 2007-07-25
forum: Repositories &amp; Backports
---

### Post by tim356 on 2007-07-25
I've been trying to install several things this morning and every time I try to get a package, I get an error something along the lines of:

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/](http://au.archive.ubuntu.com/ubuntu/pool/universe/)[package here]
Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)

Is there a server down or something, does anyone know??

---

### Post by mrgnash on 2007-07-25
I had the same problem yesterday; necessitating that I remove the 'au' prefix. Haven't checked it again today.

---

### Post by claw123 on 2007-07-26
It appears that au.archive.ubuntu.com resolves to an Optus mirror, which responds to pings but rejects HTTP requests.  It's been unavailable for a few days now, so bear with it for a little while longer, or switch to another ubuntu mirror.

Incidently, the same server is used as the AU mirror for sourceforge.  If you ask me, it's silly that AU has only one mirror, but one is better than none :lolflag:

---

### Post by Seisen on 2007-07-26
As of right now its still down and has been down for about two days.

---

### Post by zanglang on 2007-07-26
Had the same problem, you could probably trying using one of the local universities' mirrors (I'm on [http://mirrors.uwa.edu.au](http://mirrors.uwa.edu.au)), or either one of these:
[http://ftp.iinet.net.au/pub/ubuntu](http://ftp.iinet.net.au/pub/ubuntu)
[http://www.planetmirror.com/pub/ubuntu](http://www.planetmirror.com/pub/ubuntu)
[http://ftp.filearena.net/pub/ubuntu](http://ftp.filearena.net/pub/ubuntu)
[http://mirror.pacific.net.au/linux/ubuntu](http://mirror.pacific.net.au/linux/ubuntu)

---

### Post by oz_ollie on 2007-07-26
The au archive is still down Friday 20070727 0945 EST and has been inaccessible for a few days.

The easiest way to overcome this is edit the /etc/apt/sources.list and remove the "au." from the front of each repository. Then run "sudo apt-get update" and then you can do any upgrades or installations directly from the repositories.

---

### Post by Barney on 2007-07-28
I have been getting the following error message(s), without the "au" here in NY:

Any help for this?

[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by Seisen on 2007-07-30
> **Barney said:**
> I have been getting the following error message(s), without the "au" here in NY:

Any help for this?

[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

Post your source list by opening up a terminal and putting this in it.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Barney on 2007-07-30
sources list follows:

## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3

---

### Post by Seisen on 2007-07-30
Delete all the ones in bold then ```
sudo apt-get update
``` if you still get the same errors let me know.

```
## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

[B]deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper restricted
[/B]
[B]deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe
[/B]
[B]deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
[/B]
# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

[B]deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse[/B]

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

[B]deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse[/B]

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

[B]deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse[/B]

deb http://archive.canonical.com/ubuntu dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb http://www.getautomatix.com/apt dapper main
```

---

### Post by Barney on 2007-07-30
Getting closer, only one error code:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

---

### Post by Seisen on 2007-07-30
Change this line ```
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```
so it looks like this

```
#deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
``` then run ```
sudo apt-get update
``` if you don't get any errors then go back and take the **#** out of that line so it looks like this

```
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
``` then run ```
sudo apt-get update
``` again and let me know if that got rid of the error.

---

### Post by Barney on 2007-07-30
Followed above guidance; and

Same error code(s):

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/sou](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/sou) rce/Sources.bz2  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/sou](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/sou) rce/Sources.bz2  Sub-process bzip2 returned an error code (2)

---

### Post by Barney on 2007-07-30
Seisen,

Does this look better?

earlygirl@Dell3000:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 6B in 1s (4B/s)
Reading package lists... Done

....no errors!

---

### Post by Barney on 2007-07-30
Perhaps a little more explanation for how I worked around my problem.  I went into synaptic and found duplicates in the /Settings/Repositories, which I then "unchecked," and this seemed to add a # sign in front of the line where I had duplicates in my sources list ...to negate the lines  ??

Fumbling along here trying to learn!

Thanks for your help, and any more suggestions.

Barney

---

### Post by Seisen on 2007-07-30
> Fumbling along here trying to learn!

Sometimes that is the best way to learn.:lolflag:

---

