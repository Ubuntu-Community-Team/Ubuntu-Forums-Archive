---
title: "Repositorie Help For Newbie (Not Another!!)"
date: 2005-09-04
forum: Repositories &amp; Backports
---

### Post by Javabean on 2005-09-04
Hi All, Thanks in advance to all the good people who help in these forums for Newbies like myself.
I am on my third install of Ubuntu/Kubuntu. The first time just Ubuntu, but broke it while trying to get a Wifi 
card & Compro DVB set up,Along with Wine and W32codecs. The Second was Kubuntu and same problems 
but i found Kubuntu nice to look at, But sparse on Programs.This time im running Ubuntu with KDE desktop
Front End and it runs nice and has most of what i want(Cant wait for Breezy in October.) After reading some advice LNW & Linux Questions and in these forums i decided to add more Repositories. start by backing up my 
sources.list and add a new list with extra Repositories, Saved this list as sources.list and Sudo apt-get updated
 but Synaptic  does not work and sudo apt-get no longer works. I include the parser line from sudo(including the last apt-get update try for anyone to pick the bones out of .) Hoping some one can help as i dont want to
have to do a full reinstall again to fix. Thanks in Advance for any advice & help..     
```
Javabeanjames@JABUNTU:~$ sudo apt-get update
Password:
E: The method driver /usr/lib/apt/methods/htp could not be found.
james@JABUNTU:~$ sudo dpkg --configure -a
Setting up mythtv-database (0.17-3) ...
Failed to connect to database: Access denied for user: 'root@localhost' (Using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.17-3); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
james@JABUNTU:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mythtv-database (0.17-3) ...
Failed to connect to database: Access denied for user: 'root@localhost' (Using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.17-3); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list htp://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list htp://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list htp://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list htp://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
james@JABUNTU:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up mythtv-database (0.17-3) ...
Failed to connect to database: Access denied for user: 'root@localhost' (Using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.17-3); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list htp://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list htp://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list htp://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list htp://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
james@JABUNTU:~$
```

Plus when i start Synaptic I get this message:   E: The method driver /usr/lib/apt/methods/htp could not be found.

---

### Post by evilghost on 2005-09-04
My first reaction is you have a typo in /etc/apt/sources.list with something like htp:// instead of http://

Can you post what your /etc/apt/sources.list looks like?

---

### Post by Javabean on 2005-09-04
[QUOTE=evilghost]My first reaction is you have a typo in /etc/apt/sources.list with something like htp:// instead of http://

Can you post what your /etc/apt/sources.list looks like?[/QUOTE]
Looks like this..
```

#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted multiverse
 deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) hoary universe

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe main restricted multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#This repository contains source code for both Hoary & Breezy
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe
  
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://http://security.ubuntu.com/ubuntu](http://http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb htp://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

```
Yep your right Typo error at us  restricted url just fixed it now.. 1.48 pm

Fixed typo Synaptic now has over 125.. repositories ? to download from but still reports unable to connect or fails..
```

ttp://http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg: Could not resolve 'http'
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/Release.gpg:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/Release.gpg:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/Release.gpg:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/Release.gpg:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz:](http://http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz:) Could not resolve 'http'
[http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:) Sub-process bzip2 returned an error code (2)
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.138 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 82.211.81.138 80]
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:) Could not connect to backports.ubuntuforums.org:80 (69.46.19.12). - connect (111 Connection refused)

Also get this warnig but i dont think it means much. Just a public key out of date or something like that.

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

```

 Thanks for any help..

Update 3.25 pm Synaptic Now works after reinstall. Upgradeded all packages still a glitch in 
the repositorie urls and synapticwith error mrssages that read...
E: Sub process  /usr/bin/dpkg returned an error code (1)

 Any thoughts/advice..

 Thanks Evilghost, Ive mucked around with this install for two weeks and have had
 a hell of a time getting things up and running. Ive decided to start fresh and back up 
 everything before I install any new progs or change any settings. At least  I can smile
 and say I learnt a little more.and with windows i would have to ring up and tell them 
 that it was a reinstall so i can run MY software on My puter. thanks..




















9

---

### Post by bdn01 on 2005-09-18
Open the url in your browser and re-try. This worked for me.

---

### Post by elfgoh on 2005-10-09
Hi, I'm a newbie too. Synaptic keeps looking for my Hoary cd for updates in my cdrom drv whcih is faulty. I want it to look for the cd in my other cdrw drv. 

Can anyone teach me how to add a repositry in this case? 

I've tried to delete the original hoary cd repositry. Then, I've tried to use "sudo apt-cdrom -d /media/cdrom1 add", where "/media/cdrom1" is the mount point of my cdrw (I think)

The output is:

Using CD-ROM mount point /media/cdrom1/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [7340c3e4349fe3792b92f8f71cfe7ab3-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
Copying package lists...gpgv: Signature made Thursday 07,April,2005 11:30:36 AM SGT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.

******

But the original "faulty repositry" reappears and still tries to llok for hoary cd in my cdrom.

Can any1 help me out?

---

### Post by Some_Bored_Dude on 2005-11-13
Here is some information on adding reps;

[http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories)

If your cd roms faulty, comment out "deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted" (by adding a # in front of the line) in the source.list, and then run 'sudo apt-get update'.

but the link above should helpout =)

---

### Post by aysiu on 2005-11-13
> **Some_Bored_Dude]Here is some information on adding reps said:**
> http://www.ubuntuguide.org/#repositories[/url] That guide's horribly out of date. For up-to-date repositories, look at the first link in my sig.

---

### Post by marshcast on 2008-06-08
thanks evilghost - typo got it ;)

---

### Post by monarchheels on 2010-10-02
> **evilghost said:**
> My first reaction is you have a typo in /etc/apt/sources.list with something like htp:// instead of http://

Can you post what your /etc/apt/sources.list looks like?

Today I noticed that my 10.04 desktop has been getting a lot of updates but my netbook also running 10.04 hasn't. I had a similar error message and, thanks to this post, checked my Software Sources list and noticed a missing "h" on the start of an address (so it was ttp://...ect.)
Had it fixed within 2 minutes. Thanks evilghost!!!

---

