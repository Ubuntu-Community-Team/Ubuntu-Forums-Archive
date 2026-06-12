---
title: "Problem-Please Help!"
date: 2005-10-22
forum: Repositories &amp; Backports
---

### Post by galeon on 2005-10-22
When I installed Ubuntu It worked perfectly, however when i tried to update the repositories to allow me to add extra software, I ran apt-get update and it gave me a some backport errors,
```
bojan@Bojanov-Computer:~$ sudo apt-get update
Password:
Get:1 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Get:4 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Hit http://us.archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Get:5 http://security.ubuntu.com hoary-security Release [16.9kB]
Hit http://archive.ubuntu.com hoary Release
Hit http://us.archive.ubuntu.com hoary-updates Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
  404 Not Found
Hit http://security.ubuntu.com hoary-security/main Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
  404 Not Found
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
  404 Not Found
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Fetched 17.0kB in 22s (747B/s)
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
I am running Ubuntu 5.04 and Have never used linux before, so bear with me.
My sources.list file states
```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by landotter on 2005-10-22
sounds like the servers are down for a bit. Just wait an hour or two and try again. :)

---

### Post by codejunkie on 2005-10-22
the backports are now official so you have to change your /etc/apt/sources.list file a little you need to replace this line 
```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
``` with 
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
``` everything else looks ok though.

---

### Post by galeon on 2005-10-22
Thanks for all your help, I got the backports error fixed, but I still keep on getting the errors at the bottom (not sure if this is normal?) here take a look:
```
bojan@Bojanov-Computer:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary-backports Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Hit http://archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Get:4 http://security.ubuntu.com hoary-security Release [16.9kB]
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Get:5 http://archive.ubuntu.com hoary-backports Release [11.3kB]
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Get:6 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:7 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://us.archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security/main Packages
Get:8 http://archive.ubuntu.com hoary-backports/main Packages [11.5kB]
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates Release
Get:9 http://archive.ubuntu.com hoary-backports/universe Packages [26.3kB]
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Get:10 http://archive.ubuntu.com hoary-backports/multiverse Packages [1536B]
Get:11 http://archive.ubuntu.com hoary-backports/restricted Packages [14B]
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Fetched 67.9kB in 4s (15.0kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by codejunkie on 2005-10-22
[quote=galeon]Thanks for all your help, I got the backports error fixed, but I still keep on getting the errors at the bottom (not sure if this is normal?) here take a look:
```
bojan@Bojanov-Computer:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:2 http://archive.ubuntu.com hoary-backports Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Get:3 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Hit http://archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Get:4 http://security.ubuntu.com hoary-security Release [16.9kB]
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Get:5 http://archive.ubuntu.com hoary-backports Release [11.3kB]
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Get:6 http://us.archive.ubuntu.com hoary Release.gpg [189B]
Get:7 http://us.archive.ubuntu.com hoary-updates Release.gpg [189B]
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://us.archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security/main Packages
Get:8 http://archive.ubuntu.com hoary-backports/main Packages [11.5kB]
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates Release
Get:9 http://archive.ubuntu.com hoary-backports/universe Packages [26.3kB]
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Get:10 http://archive.ubuntu.com hoary-backports/multiverse Packages [1536B]
Get:11 http://archive.ubuntu.com hoary-backports/restricted Packages [14B]
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/main Packages
Hit http://us.archive.ubuntu.com hoary/restricted Packages
Hit http://us.archive.ubuntu.com hoary/main Sources
Hit http://us.archive.ubuntu.com hoary/restricted Sources
Hit http://us.archive.ubuntu.com hoary/universe Packages
Hit http://us.archive.ubuntu.com hoary/universe Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Hit http://us.archive.ubuntu.com hoary-updates/main Packages
Hit http://us.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://us.archive.ubuntu.com hoary-updates/main Sources
Hit http://us.archive.ubuntu.com hoary-updates/restricted Sources
Fetched 67.9kB in 4s (15.0kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```[/quote] you have the same line more than once in your sources.list file just run ```
sudo gedit /etc/apt/sources.list
``` and remove the duplicate entries save and then run apt-get update again.

---

### Post by galeon on 2005-10-23
Ok Thanks All Fixed! Mods you can close this thread

---

