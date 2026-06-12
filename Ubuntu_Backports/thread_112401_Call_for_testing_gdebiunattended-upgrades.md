---
title: "Call for testing gdebi/unattended-upgrades"
date: 2006-01-04
forum: Ubuntu Backports
---

### Post by mvo on 2006-01-04
Dear Friends,

the current development version of ubuntu ("dapper") contains the new packages "gdebi" and "unattended-upgrades". I backported them to breezy and would like to ask for testing of those two packages. Please note that they are development software and may have bugs that can do bad things to your system. So don't run it on your production server and keep backups (I think they are pretty ok and shouldn't have major problems, but you have been warned). 

unattended-upgrades is a python-apt based script that will download and install security upgrades automatically and unattended. It does all sorts of checks to ensure that the upgrade can be performed unattended and that only security upgrades are fetched (for details see [https://wiki.ubuntu.com/AutomaticUpdates)](https://wiki.ubuntu.com/AutomaticUpdates)). I would like to ask interested people to test it on their breezy system. To do that, please install the package "unattended-upgrades" from the repository below (it will also pull in a new python2.4-apt). This particular package dosn't do the upgrade automatically but needs to be run by hand  with "sudo unattended-upgrade" (the version in dapper integrates with cron). It will log what it does in /var/log/unattended-upgrades/unattended-upgrades.log (and shouldn't have any output on the terminal). Please run it and look into the logfile if it is doing sensible things. I would be interested in failure/success stories.

gdebi is a application that can install deb packages (that are e.g. downloaded from the net). It will do dependency resolution and some basic checks to make sure that the system doesn't contain broken packages afterwards. To test it just install the "gdebi" and "libvte4" packages. Then you can right-click on deb packages and select "Deb Package Installer". Please let me know if it makes sensible descisions about the dependency resolution and if it installs the debs correctly. If you experience problems (crashes) please run it from a terminal with "gdebi-gtk foo.deb" and send me the output. 

The packages are available from (add this to your sources.list):
deb [http://people.ubuntu.com/~mvo/backports/breezy](http://people.ubuntu.com/~mvo/backports/breezy) /

The archive is signed with my gpg-key (0x5662C734). 

If you want your old packages back, please run:
```
$ sudo apt-get install libvte4=1:0.11.15-0ubuntu2 libvte-common=1:0.11.15-0ubuntu2 python2.4-apt=0.6.13.1ubuntu1 python-apt=0.6.13.1ubuntu1 gdebi- unattended-upgrades- python-vte=1:0.11.15-0ubuntu2

```

thanks,
 Michael

---

### Post by UbuWu on 2006-01-04
Is it possible/do you want us to test unattended-upgrades on dapper as well?

---

### Post by UbuWu on 2006-01-04
You might also want to post this on the dapper development forums as people interested in ubuntu development will be more likely wanting to test things out.

---

