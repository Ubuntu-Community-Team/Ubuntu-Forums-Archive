---
title: "how can I fix this in my source list?"
date: 2006-10-31
forum: Repositories &amp; Backports
---

### Post by maddbaron on 2006-10-31
> W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

its stopping me from upgrading and downloading correctly.

---

### Post by meng on 2006-10-31
According to the website itself:
wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -

---

### Post by maddbaron on 2006-10-31
same issue

> maddbaron@baronworks:~$ wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -
--19:28:51--  [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg)
           => `-'
Resolving 3v1n0.tuxfamily.org... 212.85.158.4
Connecting to 3v1n0.tuxfamily.org|212.85.158.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,374 (2.3K) [text/plain]

100%[====================================>] 2,374         --.--K/s

19:28:52 (119.04 KB/s) - `-' saved [2374/2374]

OK
maddbaron@baronworks:~$ sudo apt-get update

W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems



---

### Post by maddbaron on 2006-10-31
This is my soucelist

> deb-src [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra 
deb [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit extra 
# Treviño's Beryl-SVN Ubuntu Repository
# GPG key: 81836EBF
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn
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

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END


---

### Post by meng on 2006-10-31
Ah, *shrug* I don't know then. Is it really stopping you from upgrading though? I've not experienced problems even when there are missing keys.

---

### Post by maddbaron on 2006-10-31
yeah i keep getting broken when i try to add or upgrade programs.

---

### Post by meng on 2006-11-01
I think that problem may be separate from GPG authentication. Which package/s is/are reported broken?

---

