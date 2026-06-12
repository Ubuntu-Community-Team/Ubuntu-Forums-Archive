---
title: "Kernel Sources"
date: 2005-04-17
forum: Repositories &amp; Backports
---

### Post by sbm on 2005-04-17
Are the kernel sources installed by default on Ubuntu hoary?
if yes: Where can I find them.

if no: How do I do it? And where will they be installed to?

/SBM

---

### Post by hardwarder on 2005-04-17
The kernel sources have the package name of linux-source.

---

### Post by maqi on 2005-04-17
```
sudo apt-get install linux-source-2.6.10
```

Will be installed to /usr/src/linux-source-2.6.10.tar.bz2

You should probably install your kernel headers as well.
 maqi

P.S - Do you read stickies when you enter a forum? :-P

---

### Post by az on 2005-04-17
If you need to make a module, just use the linux-headers package for your kernel.  That is usually enough.  If you need the source, install the linux-tree package.

The headers are on your cd, the other sources are in the archive on the net.

They will be in /usr/src once installed

---

### Post by sbm on 2005-04-17
Thanx for all your answers..

---

### Post by Sniper PT on 2005-07-23
I try: sudo apt-get install linux-source-2.6.10
but that doesn't work... can i just copy the folder linux-source-2.6.10 of Ubuntu CD to /usr/src/ folder?

Thanks

P.S.: When i use: sudo apt-cache search linux-source 2.6
it return:
linux-image-xxxxx (i don't remember the numbers...  O:) )

---

### Post by Xian on 2005-07-23
The CD method should work but you might post the apt errors.
That is the correct package name.

```
$ sudo apt-get install linux-source-2.6.10
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  libncurses-dev kernel-package libqt3-dev
The following NEW packages will be installed:
  linux-source-2.6.10
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.5MB of archives.
After unpacking 37.6MB of additional disk space will be used.
Get:1 http://security.ubuntu.com hoary-security/main linux-source-2.6.10 2.6.10-34.3 [37.5MB]
```

---

### Post by Sniper PT on 2005-07-23
I have try make that, but it said there isn't linux-source-2.6.10 package...

I have dowload linux-source-2.6.10_2.6.10-34.3_all.deb, i now i will install... is that the right way?

---

### Post by Xian on 2005-07-23
[QUOTE=Sniper PT]I have try make that, but it said there isn't linux-source-2.6.10 package...[/QUOTE]
Backup your current /etc/apt/sources.list file.
Then use mine as your own.

When you have copy/pasted mine over run an '$ sudo apt-get update' session.
Then again try to download the kernel source package.

```
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

##Backup Ubuntu Mirrors
#deb http://mirrors.xmission.com/ubuntu hoary-updates main restricted universe multiverse
#deb-src http://mirrors.xmission.com/ubuntu hoary-updates main restricted universe multiverse

##Security Mirrors
deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

##Backup Security Mirrors
#deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
#deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

#Kubuntu KDE341 Updates
deb http://kubuntu.org/hoary-kde341 hoary-updates main

##Backports
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-backports main universe multiverse restricted

## Backports (Alternate Mirror)
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by Sniper PT on 2005-07-23
I don't have Internet access in the PC with Linux...

---

### Post by Xian on 2005-07-23
You might have mentioned that.
Just install the [linux-source-2.6.10_2.6.10-34.3](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.10/linux-source-2.6.10_2.6.10-34.3_all.deb) you have downloaded.

---

### Post by Sniper PT on 2005-07-23
Thanks!!!  ;-)

---

