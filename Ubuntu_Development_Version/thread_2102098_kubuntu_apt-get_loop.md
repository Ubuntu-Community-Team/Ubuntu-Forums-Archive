---
title: "kubuntu apt-get loop"
date: 2013-01-06
forum: Ubuntu Development Version
---

### Post by damador on 2013-01-06
damador@ubuntu-dom:~$ sudo apt-get install -f
[sudo] password for damador: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  kbattleship
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  knavalbattle ksnakeduel picmi
The following packages will be REMOVED:
  ktron
The following NEW packages will be installed:
  knavalbattle ksnakeduel picmi
0 upgraded, 3 newly installed, 1 to remove and 137 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,983 kB of archives.
After this operation, 2,550 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 325126 files and directories currently installed.)
Unpacking knavalbattle (from .../knavalbattle_4%3a4.9.97-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/knavalbattle_4%3a4.9.97-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/games/kbattleship', which is also in package kbattleship 4:4.9.5-0ubuntu0.1~ubuntu12.10~ppa1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/knavalbattle_4%3a4.9.97-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
damador@ubuntu-dom:~$ sudo apt-get remove knavalbattle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'knavalbattle' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kdegames : Depends: knavalbattle (>= 4:4.9.97) but it is not going to be installed
            Depends: ksnakeduel (>= 4:4.9.97) but it is not going to be installed
            Depends: picmi (>= 4:4.9.97) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
damador@ubuntu-dom:~$ sudo apt-get remove kdegames
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kubuntu-full : Depends: kdegames but it is not going to be installed
                Recommends: libreoffice-kde but it is not going to be installed
                Recommends: libreoffice-style-oxygen but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
damador@ubuntu-dom:~$ sudo apt-get remove kubuntu-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kdegames : Depends: knavalbattle (>= 4:4.9.97) but it is not going to be installed
            Depends: ksnakeduel (>= 4:4.9.97) but it is not going to be installed
            Depends: picmi (>= 4:4.9.97) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
damador@ubuntu-dom:~$ sudo apt-get remove kubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kubuntu
damador@ubuntu-dom:~$ sudo apt-get remove kubuntu-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kdegames : Depends: knavalbattle (>= 4:4.9.97) but it is not going to be installed
            Depends: ksnakeduel (>= 4:4.9.97) but it is not going to be installed
            Depends: picmi (>= 4:4.9.97) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
damador@ubuntu-dom:~$ sudo apt-get purge kubuntu-full
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kdegames : Depends: knavalbattle (>= 4:4.9.97) but it is not going to be installed
            Depends: ksnakeduel (>= 4:4.9.97) but it is not going to be installed
            Depends: picmi (>= 4:4.9.97) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
damador@ubuntu-dom:~$ 


its raring ringtail - seems taht something in middle of upgrading is broken 

cant fix and purge it ;/

---

### Post by oldos2er on 2013-01-06
Moved to Ubuntu +1 (Raring Ringtail).

---

