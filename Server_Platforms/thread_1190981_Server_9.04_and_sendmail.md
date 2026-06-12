---
title: "Server 9.04 and sendmail?"
date: 2009-06-18
forum: Server Platforms
---

### Post by FrankShafer on 2009-06-18
Hi All,

I'm about intermediate level user with Ubuntu and am having a heck of a time installing sendmail on Ubuntu Server 9.04.  Here are the outputs of the error messages I am receiving.

```
sudo apt-get install 

Reading package lists...
Building dependency tree...
Reading state information...
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  exim4-daemon-light: Depends: exim4-base (>= 4.69) but it is not going to be installed
  sendmail: Depends: sendmail-base but it is not going to be installed
            Depends: sendmail-bin but it is not going to be installed
            Depends: sendmail-cf but it is not going to be installed
            Depends: sensible-mda but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```reading that message, i try the 'apt-get -f install' which results in this :

```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@uwebserver:/# sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  exim4-config
The following NEW packages will be installed:
  exim4-config
0 upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
1 not fully installed or removed.
Need to get 0B/1291kB of archives.
After this operation, 1053kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package exim4-config.
(Reading database ... 123431 files and directories currently installed.)
Unpacking exim4-config (from .../exim4-config_4.69-2_all.deb) ...
Selecting previously deselected package exim4-base.
Preparing to replace exim4-base 4.69-2 (using .../exim4-base_4.69-2_i386.deb) ...
Unpacking replacement exim4-base ...
Setting up exim4-config (4.69-2) ...
Error: Unsplit config selected and /etc/exim4/exim4.conf.template missing ... exiting
dpkg: error processing exim4-config (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of exim4-base:
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however:
  Package exim4-config is not configured yet.
  Package exim4-config-2 is not installed.
  Package exim4-config which provides exim4-config-2 is not configured yet.
dpkg: error processing exim4-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 exim4-config
 exim4-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
```I've tried using aptitude as well and trying some of the higher rated solutions that it suggests with no luck.  I've googled the issues I've run into extensively and nothing has helped so far.  Any ideas/tutorials would be highly appreciated.  Thanks guys.

- Cheers

I'd also like to mention I combed through all mentions of send mail in the forums and nothing seemed to help - just in case anyone tells me to search :P

---

