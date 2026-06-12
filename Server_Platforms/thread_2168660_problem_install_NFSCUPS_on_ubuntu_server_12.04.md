---
title: "problem install NFS/CUPS on ubuntu server 12.04"
date: 2013-08-18
forum: Server Platforms
---

### Post by bryan.sailer on 2013-08-18
I have recently rebuilt my home server and I installed 12.04 server. When I attempt the following commands I get the output saying that the package has unmet dependencies. 

sudo apt-get install nfs-kernel-server  

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 nfs-kernel-server : Depends: libgssglue1 but it is not going to be installed
                     Depends: libnfsidmap2 but it is not going to be installed
                     Depends: libtirpc1 but it is not going to be installed
                     Depends: nfs-common (= 1:1.2.5-3ubuntu3.1) but it is not going to be installed
 perl : Depends: perl-base (= 5.14.2-6ubuntu2.2) but 5.14.2-6ubuntu2.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

The same thing happens with this command:

sudo apt-get install cups

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cups : Depends: libcupscgi1 (>= 1.4.2) but it is not going to be installed
        Depends: libcupsimage2 (>= 1.4.0) but it is not going to be installed
        Depends: libcupsmime1 (>= 1.5.0) but it is not going to be installed
        Depends: libcupsppdc1 (>= 1.4.0) but it is not going to be installed
        Depends: libpaper1 but it is not going to be installed
        Depends: libslp1 but it is not going to be installed
        Depends: poppler-utils (>= 0.12) but it is not going to be installed
        Depends: ghostscript (>= 9.02~) but it is not going to be installed
        Depends: cups-common (>= 1.5.3) but it is not going to be installed
        Depends: cups-client (>= 1.5.3-0ubuntu8) but it is not going to be installed
        Depends: ssl-cert (>= 1.0.11) but it is not going to be installed
        Depends: cups-ppdc but it is not going to be installed
        Depends: cups-filters but it is not going to be installed
        Recommends: avahi-daemon but it is not going to be installed
        Recommends: colord but it is not going to be installed
        Recommends: foomatic-filters (>= 4.0) but it is not going to be installed
        Recommends: printer-driver-gutenprint but it is not going to be installed
        Recommends: ghostscript-cups (>= 9.02~) but it is not going to be installed
 perl : Depends: perl-base (= 5.14.2-6ubuntu2.2) but 5.14.2-6ubuntu2.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have tried the suggested apt-get -f install but that does nothing. What have I done wrong? What do I need to do next to install these packages?

---

