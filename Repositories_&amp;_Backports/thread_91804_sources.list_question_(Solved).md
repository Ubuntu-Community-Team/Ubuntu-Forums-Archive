---
title: "sources.list question? (Solved)"
date: 2005-11-18
forum: Repositories &amp; Backports
---

### Post by wargames on 2005-11-18
What are the us.archive.ubuntu.com repository for multiverse? I want to add the U.S. multiverse repository but can't find what repositories to enter into my sources.list in order to enable multiverse.

---

### Post by ubuntu_demon on 2005-11-18
I guess it's just :
```

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

```
My sources.list is in my signature.

---

### Post by aysiu on 2005-11-18
A lot of people have had problems with the us.archive.ubuntu.com repositories. If you are, too, look at the first link in my sig.

---

### Post by Footer on 2005-11-18
[QUOTE=aysiu]A lot of people have had problems with the us.archive.ubuntu.com repositories. If you are, too, look at the first link in my sig.[/QUOTE]

I used the sources.list (for Breezy 5.10) from the first link in your signature and after doing **sudo apt-get update** I get the following error at the end:

[INDENT]W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
[/INDENT]
What's up with that?

Thanks.

---

### Post by aysiu on 2005-11-18
[QUOTE=Footer]I used the sources.list (for Breezy 5.10) from the first link in your signature and after doing **sudo apt-get update** I get the following error at the end:

[INDENT]W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
[/INDENT]
What's up with that?

Thanks.[/QUOTE] I don't know. I got this just now: ```
sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Hit http://archive.ubuntu.com breezy Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 4B in 1s (3B/s)
Reading package lists... Done
```

---

### Post by Footer on 2005-11-18
I'm still getting the error:

```
sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Hit http://security.ubuntu.com breezy-security Release
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Ign http://archive.ubuntu.com breezy Release
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/main Sources
Hit http://security.ubuntu.com breezy-security/restricted Sources
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 192B in 1s (111B/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```

And here's my sources.list:

```
more sources.list
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe
deb-src http://archive.ubuntu.com/ubuntu breezy universe

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu breezy multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
```

What gives???

---

### Post by aysiu on 2005-11-18
I don't know. Someone suggested this on another thread, and it seemed to work for people. Back up the sources.list you got from my sig ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` Then edit the sources.list ```
sudo gedit /etc/apt/sources.list
``` and delete *everything*. Then, ```
sudo apt-get update
``` with the empty repositories. Then ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
sudo apt-get update
```

---

### Post by pete on 2005-11-18
Thanks, aysiu--  that cleared up the GPG problem for me.

---

### Post by Footer on 2005-11-18
[QUOTE=aysiu]I don't know. Someone suggested this on another thread, and it seemed to work for people. Back up the sources.list you got from my sig ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` Then edit the sources.list ```
sudo gedit /etc/apt/sources.list
``` and delete *everything*. Then, ```
sudo apt-get update
``` with the empty repositories. Then ```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
sudo apt-get update
```[/QUOTE]

**BRILLIANT!!!**  That worked:

```
sudo apt-get update
Get:1 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release [19.6kB]
Get:5 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Get:6 http://archive.ubuntu.com breezy Release [30.9kB]
Get:7 http://archive.ubuntu.com breezy-updates Release [19.6kB]
Get:8 http://archive.ubuntu.com breezy-backports Release [11.3kB]
Get:9 http://security.ubuntu.com breezy-security/main Packages [8884B]
Get:10 http://archive.ubuntu.com breezy/main Packages [585kB]
Get:11 http://security.ubuntu.com breezy-security/restricted Packages [14B]
Get:12 http://security.ubuntu.com breezy-security/main Sources [3980B]
Get:13 http://security.ubuntu.com breezy-security/restricted Sources [14B]
Get:14 http://security.ubuntu.com breezy-security/universe Packages [6984B]
Get:15 http://security.ubuntu.com breezy-security/universe Sources [1062B]
Get:16 http://archive.ubuntu.com breezy/restricted Packages [5061B]
Get:17 http://archive.ubuntu.com breezy/main Sources [232kB]
Get:18 http://archive.ubuntu.com breezy/restricted Sources [1454B]
Get:19 http://archive.ubuntu.com breezy/universe Packages [2304kB]
Get:20 http://archive.ubuntu.com breezy/universe Sources [915kB]
Get:21 http://archive.ubuntu.com breezy/multiverse Packages [91.6kB]
Get:22 http://archive.ubuntu.com breezy/multiverse Sources [46.9kB]
Get:23 http://archive.ubuntu.com breezy-updates/main Packages [17.0kB]
Get:24 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:25 http://archive.ubuntu.com breezy-updates/main Sources [4667B]
Get:26 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Get:27 http://archive.ubuntu.com breezy-backports/main Packages [14B]
Get:28 http://archive.ubuntu.com breezy-backports/restricted Packages [14B]
Get:29 http://archive.ubuntu.com breezy-backports/universe Packages [14B]
Get:30 http://archive.ubuntu.com breezy-backports/multiverse Packages [14B]
Fetched 4306kB in 27s (155kB/s)
Reading package lists... Done
```

Thanks much aysiu!!!

:D

---

### Post by aysiu on 2005-11-18
I don't know why, but apparently, there's some kind of residual "bad" signatures that need to be cleaned out...

---

### Post by wargames on 2005-11-18
Thanks guys! :)

---

### Post by magomago on 2005-11-19
[QUOTE=aysiu]I don't know why, but apparently, there's some kind of residual "bad" signatures that need to be cleaned out...[/QUOTE]

aww man you haveall pumped up to go home and try this out...I'd love to fix this problem, especially b/c it hit a new install of 5.10!   I thought it was because i had gone from preview to final, but was a little dissapointed when i burned 5.10 final

will let you guys know if it works

---

