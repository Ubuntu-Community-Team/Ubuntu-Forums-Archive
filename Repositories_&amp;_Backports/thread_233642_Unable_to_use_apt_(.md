---
title: "Unable to use apt :("
date: 2006-08-10
forum: Repositories &amp; Backports
---

### Post by dmacdonald95 on 2006-08-10
Alright. I'd consider myself a Windows power-user, and a Linux newbie. I can use the command line, I understand CHMOD, CHOWN, and CAT, but I'm still learning stuff. This problem has stumped me though, so I thought I'd come to the Ubuntu forums.

I'm using Dapper. I downloaded the CD ISO, burned it, and installed it on my laptop. (1.7Ghz Pentium M, 256MB RAM, 40GB HD, ipw2200 built-in wireless & built-in ethernet).

Everything worked fine, I'm using a virgin sources.list, and I can't update.

I sudo apt-get update and I get "Connection failed errors". I thought it was just my installation (since I did it before on Kubuntu, then I switched to Suse, hated it, and decided to come to Ubuntu)...so I reinstalled. No luck.

I can browse the Internet just fine. I can ping "ca.archive.ubuntu.com".

Here's my sources.list:

```

deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Here's my terminal output: ```
dustin@dustin-laptop:~$ sudo apt-get update
Err http://ca.archive.ubuntu.com dapper Release.gpg
  Connection failed
Err http://ca.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed
Ign http://ca.archive.ubuntu.com dapper Release
Ign http://ca.archive.ubuntu.com dapper-updates Release
Ign http://ca.archive.ubuntu.com dapper/main Packages
Ign http://ca.archive.ubuntu.com dapper/restricted Packages
Ign http://ca.archive.ubuntu.com dapper/main Sources
Ign http://ca.archive.ubuntu.com dapper/restricted Sources
Ign http://ca.archive.ubuntu.com dapper-updates/main Packages
Ign http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://ca.archive.ubuntu.com dapper-updates/main Sources
Ign http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Err http://ca.archive.ubuntu.com dapper/main Packages
  Connection failed
Err http://ca.archive.ubuntu.com dapper/restricted Packages
  Connection failed
Err http://ca.archive.ubuntu.com dapper/main Sources
  Connection failed
Err http://ca.archive.ubuntu.com dapper/restricted Sources
  Connection failed
Err http://ca.archive.ubuntu.com dapper-updates/main Packages
  Connection failed
Err http://ca.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed
Err http://ca.archive.ubuntu.com dapper-updates/main Sources
  Connection failed
Err http://ca.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz Connection failed
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz Connection failed
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
dustin@dustin-laptop:~$

```

Here's my resolv.conf:

```

nameserver 192.168.1.1

```

I'm using a Router (NETGEAR WGR614).

Can anyone help? :(

---

### Post by MrHorus on 2006-08-10
Are you actually in Canada first of all?

If not, chance the ca part of the URL to whichever country you are in.

If you ARE in Canada it might also be worth trying to change them to different mirrors as well.

---

### Post by dmacdonald95 on 2006-08-10
Yes, I am in Canada, I've tried using other mirrors (cl, be, us) to no avail.

---

### Post by Ellidi on 2006-08-10
I have the same problem.
I don't think it has anything to do with the country code.
I'm in Denmark and up-until 3 days ago or so au.archive.ubuntu worked fine for me.
'$ sudo apt-get update' returns this:
```

Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Ign http://security.ubuntu.com dapper-security Release
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://security.ubuntu.com dapper-security/universe Packages
Err http://au.archive.ubuntu.com dapper Release.gpg
  Connection failed
Ign http://security.ubuntu.com dapper-security/universe Sources
Err http://au.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports Release.gpg
  Connection failed
Ign http://au.archive.ubuntu.com dapper Release
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://au.archive.ubuntu.com dapper-updates Release
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://au.archive.ubuntu.com dapper-backports Release
Ign http://au.archive.ubuntu.com dapper/main Packages
Ign http://au.archive.ubuntu.com dapper/restricted Packages
Ign http://au.archive.ubuntu.com dapper/main Sources
Ign http://au.archive.ubuntu.com dapper/restricted Sources
Ign http://au.archive.ubuntu.com dapper/universe Packages
Ign http://au.archive.ubuntu.com dapper/universe Sources
Ign http://au.archive.ubuntu.com dapper-updates/main Packages
Ign http://au.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://au.archive.ubuntu.com dapper-updates/main Sources
Ign http://au.archive.ubuntu.com dapper-updates/restricted Sources
Ign http://au.archive.ubuntu.com dapper-backports/main Packages
Ign http://au.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://au.archive.ubuntu.com dapper-backports/universe Packages
Ign http://au.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://au.archive.ubuntu.com dapper-backports/main Sources
Ign http://au.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://au.archive.ubuntu.com dapper-backports/universe Sources
Ign http://au.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://au.archive.ubuntu.com dapper/main Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper/restricted Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper/main Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper/restricted Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper/universe Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper/universe Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper-updates/main Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper-updates/main Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports/main Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports/universe Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports/main Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports/universe Sources
  Connection failed
Err http://au.archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz  Connection failed
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz  Connection failed
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
It's quite annoying not knowing what's wrong :mad:

---

### Post by Ellidi on 2006-08-11
[This ]("http://www.ubuntuforums.org/showpost.php?p=1364819&postcount=4")fixed my problem.

---

### Post by dmacdonald95 on 2006-08-11
> **Ellidi said:**
> [This ]("http://www.ubuntuforums.org/showpost.php?p=1364819&postcount=4")fixed my problem.
Woohoo, that fixed my problem too! Thank you! :D

---

