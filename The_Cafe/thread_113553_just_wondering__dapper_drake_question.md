---
title: "just wondering  dapper drake question"
date: 2006-01-06
forum: The Cafe
---

### Post by dosed150 on 2006-01-06
when dapper drake comes out will i have to install it from scratch or can i just update the system so i wouldnt have to recopy all my music on to my pc

---

### Post by Perfect Storm on 2006-01-06
You can update. No need for reinstall :)

---

### Post by dosed150 on 2006-01-06
yay

---

### Post by beercz on 2006-01-06
You can update now if you like.

Just change your /etc/apt/sources.list replacing each occurance of 'breezy' to 'dapper' (without the quotes).

Here's mine for example:

> 
## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricteddeb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse


Have fun ...

---

### Post by AlexandreP on 2006-01-06
[QUOTE=beercz]You can update now if you like.[/QUOTE]
Yes, you can, but have to know what you're doing, since it's a **development** and unstable version ;)

---

### Post by majikstreet on 2006-01-06
[QUOTE=AlexandreP]Yes, you can, but have to know what you're doing, since it's a **development** and unstable version ;)[/QUOTE]
underline italic bold...

**_*DAPPER DRAKE IS THE DEVELOPMENT VERSION!!*_**

---

### Post by dosed150 on 2006-01-06
im not planning on updating till april but i just thought about it

---

