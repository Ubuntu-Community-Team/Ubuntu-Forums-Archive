---
title: "precise - install crash from live session"
date: 2011-12-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by candtalan on 2011-12-19
Using todays available iso:

trying to install from a live session, I find that I get an almost immediate crash:
============================
ubi-language crashed
ubi-language failed with exit code 1. further information may be found in /var/log/syslog. do dyou want to try running this step again before continuing? 
If you do not, your installation may fail entirely or may be broken.
[quit] [continue anyway] [try again]
============================

I briefly attempted to  report as a bug but without the particular app running, (crashed) I do not have enough experience to report a bug usefully I think.


edit:
It also crashes the same when I attempt to install from the media (usb) using the initial boot menu rather than as previously, using the live session.
edit2:
am now downloading the original 12.04 Alpha-1, not the daily build, to try to install that.
edit3: Ubuntu 12.04 alpha 1, installed ok and the many updates in the form of a partial upgrade - all seems ok as installed

---

### Post by ventrical on 2011-12-19
> **candtalan said:**
> Using todays available iso:

trying to install from a live session, I find that I get an almost immediate crash:
============================
ubi-language crashed
ubi-language failed with exit code 1. further information may be found in /var/log/syslog. do dyou want to try running this step again before continuing? 
If you do not, your installation may fail entirely or may be broken.
[quit] [continue anyway] [try again]
============================

I briefly attempted to  report as a bug but without the particular app running, (crashed) I do not have enough experience to report a bug usefully I think.


edit:
It also crashes the same when I attempt to install from the media (usb) using the initial boot menu rather than as previously, using the live session.
edit2:
am now downloading the original 12.04 Alpha-1, not the daily build, to try to install that.
edit3: Ubuntu 12.04 alpha 1, installed ok and the many updates in the form of a partial upgrade - all seems ok as installed


eeek.. partial upgrade !! ? No ! Use synaptic or terminal is better:

sudo apt-get update
sudo apt-get upgrade
sudo update-grub

---

### Post by candtalan on 2011-12-20
> **ventrical said:**
> eeek.. partial upgrade !! ? No ! Use synaptic or terminal is better:

sudo apt-get update
sudo apt-get upgrade
sudo update-grub

Thank you yes it is 'better' in that it works (!) however, the alpha 1 is for testing, and if stuff is not tested as fully as possible, I think we are missing a trick.

---

### Post by jerrylamos on 2011-12-20
> **candtalan said:**
> Thank you yes it is 'better' in that it works (!) however, the alpha 1 is for testing, and if stuff is not tested as fully as possible, I think we are missing a trick.
Since this is alpha, I use

sudo aptitude update
sudo aptitude safe-upgrade

which on development unstable I've had far more success with than apt-get.  I've found apt-get to be quite happy to damage an Alpha installation.

Now sometimes safe-upgrade doesn't do all the packages and I warily do

sudo aptitude full-upgrade

Over time the installed precise uses more and more and more disk space and I'll do a re-install.  I do:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

but it is still likely to leave the old linux image and even headers around.  On the 3.2.0.6 update/upgrade it left the old 3.2.05 so I removed that with synaptic.  Blocks used is still creeping up.

Now the goal of precise is to be a LTS (maybe 5 years?) instead of introducing a lot of new stuff, so accordingly precise is less unstable than the last several ubuntu releases. 

Jerry

---

