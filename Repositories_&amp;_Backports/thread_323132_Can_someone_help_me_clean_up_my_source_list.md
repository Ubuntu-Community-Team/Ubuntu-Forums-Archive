---
title: "Can someone help me clean up my source list?"
date: 2006-12-21
forum: Repositories &amp; Backports
---

### Post by maddbaron on 2006-12-21
I ran 

Sudo apt-get update

and got

Failed to fetch [http://mrpouit.tuxfamily.org/dists/edgy-pouit/extra/source/Sources.gz](http://mrpouit.tuxfamily.org/dists/edgy-pouit/extra/source/Sources.gz)  404 Not Found
Failed to fetch [http://mrpouit.tuxfamily.org/dists/edgy-pouit/extra/binary-i386/Packages.gz](http://mrpouit.tuxfamily.org/dists/edgy-pouit/extra/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


When everything was done.

I have my adept update icon on my toolbar all the time now b/c it won't update Brasero.

This is my source list

---

### Post by maddbaron on 2006-12-21
> deb-src [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra 
deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra 
# Treviño's Beryl-SVN Ubuntu Repository
# GPG key: 81836EBF
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
#automatix
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main



deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END


what do i remove or change anyone please?

---

### Post by matthew on 2006-12-21
> **maddbaron said:**
> what do i remove or change anyone please?
Put this in place of what you have.

```
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

## Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu edgy main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe multiverse

## Ubuntu backports project (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## Ubuntu supported packages (sources, GPG key: 437D05B5)
# deb-src http://archive.ubuntu.com/ubuntu edgy main restricted
# deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted
# deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
# deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu edgy-updates universe multiverse
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

## Ubuntu commercial packages
# deb http://archive.canonical.com/ubuntu edgy-commercial main
```

---

### Post by arnieboy on 2006-12-21
simply change the following line
> deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra 
to
> #deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra 
and do
```
sudo apt-get update
```

---

