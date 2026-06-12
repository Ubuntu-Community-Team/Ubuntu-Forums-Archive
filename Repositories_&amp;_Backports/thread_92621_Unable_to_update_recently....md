---
title: "Unable to update recently..."
date: 2005-11-20
forum: Repositories &amp; Backports
---

### Post by analox on 2005-11-20
Here are the error messages I got after updating the packages list by Synaptic
> [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Bad header line
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release:) Unable to find expected entry  restrict/source/Sources in Meta-index file (malformed Release file?)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

Then another window pop-up with:
> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

I choose Smart Upgrade to upgrade the system for some packages, here comes the last error message
> E: The package index files are corrupted. No Filename: field for package bum.
E: Unable to lock the download directory

The problem just appeared 2-3 days ago and I can't get rid of it until now. Have you guys encountered the same problem and anyone knows how to fixed it...?
Please help :smile: . Thanks!

Btw, this my sources.list...
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restrict

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) breezy-updates main restricted universe multiverse
#deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) breezy-updates main restricted universe multiverse

##Security Mirrors
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe

##Backup Security Mirrors
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe

---

### Post by aysiu on 2005-11-20
See the first link in my sig.

---

### Post by analox on 2005-11-20
Thanks aysiu, 
I have update sources.list according to your link and there is no error message anymore :D 
Yet, the list of upgradable packages I got before doesn't appear... Does it mean that these upgradable packages are not ready yet and have been deleted from the repository :confused:

---

