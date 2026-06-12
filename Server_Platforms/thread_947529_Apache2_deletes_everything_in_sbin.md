---
title: "Apache2 deletes everything in sbin?"
date: 2008-10-14
forum: Server Platforms
---

### Post by typically on 2008-10-14
Hi,

So I installed Apache2 using synaptic and it apparently removed a lot of stuff randomly, including apt-get, synaptic, and OpenOffice.

Why would it do this? How do I recover this stuff?

Using Ubuntu 7.10

---

### Post by Vegan on 2008-10-14
Sounds like you have major problems. I installed apache2 easily from a terminal window:

sudo apt-get install apache2

and its run on the server version, never tried with the desktop

to fix your system

sudo apt-get update
sudo apt-get upgrade

if that fails, you will need to erase your disk and start over

---

### Post by hessiess on 2008-10-14
if youve lost the pacage manager, theres not a lot you can do. try compiling apt-get from source code?

---

### Post by typically on 2008-10-14
Wow, really weird. I simply used synaptic manager to install it, and it works fine. Not sure which repository it came from...

Anyways, I really didn't want to reinstall Ubuntu, or erase my disk, so I found the apt package at [http://packages.ubuntu.com/feisty/base/apt](http://packages.ubuntu.com/feisty/base/apt) and ran 

```
dpkg --force-conflicts apt apt_0.6.46.4ubuntu10_i386.deb
sudo apt-get -f install
```

Now I at least have apt and synaptic back... still a warning to anyone who's downloading Apache2, check before installing apache2 metapackage 2.2.9-10

In what may be related, I'm getting a lot of "cannot be authenticated" warnings when installing things like OpenOffice (I believ I got one with apache2 as well). Do any of these repositories look suspect?


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) gutsy universe

## Minc-2 repository
## deb [http://packages.bic.mni.mcgill.ca/deb-minc2](http://packages.bic.mni.mcgill.ca/deb-minc2)	./ 
# deb [http://packages.bic.mni.mcgill.ca/deb](http://packages.bic.mni.mcgill.ca/deb) ./

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) feisty main 
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
## deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
## deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
## deb [http://packages.bic.mni.mcgill.ca/ubuntu-gutsy/](http://packages.bic.mni.mcgill.ca/ubuntu-gutsy/) ./
deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) lenny main non-free contrib
deb [http://apsy.gse.uni-magdeburg.de/debian](http://apsy.gse.uni-magdeburg.de/debian) sid main non-free


ADDED:
Trying to reinstall openoffice tells me I need libldap2. Trying to install libldap2 tells me I need to uninstall pretty much everything, including nautilus, apache2, all the gnome stuff, etc. I'm new to Ubuntu and Debian, but is this not a malicious package?? What's going on?

[email]ubuntu-devel-discuss@lists.ubuntu.com[/email]

---

### Post by mbeach on 2008-10-14
did you do anything else between having a working system and one that is failing.  Installing apache from the repos is unlikely to cause such issues.

---

### Post by cariboo on 2008-10-14
Your sources list is a bit of a dog's breakfast, youre pulling packages from from Fiesty, Gutsy, lennie and sid.

It might be better to stick to one version, and upgrade to a supported version Fiesty packages will no longer be available after the end of October, and Itrepid Ibex will become available at the samer time.

Jim

---

