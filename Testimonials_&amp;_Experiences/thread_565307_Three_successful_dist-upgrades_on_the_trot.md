---
title: "Three successful dist-upgrades on the trot"
date: 2007-10-02
forum: Testimonials &amp; Experiences
---

### Post by Steve1961 on 2007-10-02
I've been using Ubuntu since Hoary, and Hoary, Breezy and Dapper were all clean installs.  However, by the time I'd got to Dapper I felt I'd gained sufficient experience to try a dist-upgrade when Edgy was released - I'd also got my system just the way  I wanted it and didn't particularly relish setting everything up from scratch again.

The Dapper to Edgy upgrade seemed to go reasonably well, although there were a few bits and pieces to fix and I had to run apt-get -f install several times before everything was as it should be.  But the upgrade from Edgy to Feisty was seamless.  I should perhaps also say that for both dist-upgrades I just ran aptitude dist-upgrade rather than using the officially sanctioned update manager method - mainly because I also run debian testing and I've had a very few problems when using this on a regular basis. 

Anyway, yesterday I decided to upgrade to Gutsy - I usually upgrade when the beta is released - and decided to use the official update manager method for the first time.  Everything downloaded and the process started, but after about five minutes into the installation stage I started getting lots of dependency error messages stating such and such package couldn't be installed.  Eventually this culminated in a message saying the upgrade would have to be aborted. I clicked OK in the expectation that I'd just borked my system and would have to start from scratch, but rather than aborting the installation just seemed to continue until, after about an hour, the update manager closed down.  There were no notifications about a restart being required, so on the off-chance I ran a manual aptitude dist-upgrade and an apt-get -f install.  There were no error messages, no additional packages to install, just a message about using autoremove to get rid of packages that were no longer necessary.  Better still, after rebooting, everything fired up properly, and from what I can tell the dist-upgrade seems to have been successful.

So this last upgrade has been a bit strange, but on the plus side that's three dist-upgrades that have now been successful.  This is why, after doing my fair share of distro-hopping, I now stick with Ubuntu and Debian.

---

### Post by wolfen69 on 2007-10-02
i'm glad to hear the upgrades went well. as far as myself, ive never upgraded any OS at any time.(ive probably done well over 300 installs) :-)  clean installs for me is always the way to go. lately, ive been trying alot of different distros, and since i never keep any worthwhile documents or media on my OS drives, installing different flavors of linux on a whim has become a common occurance.  i find linux mint to be best lazy mans' debian. it only took 25 min. from start to finish, including all tweaking. not bad. and it's been pretty stable too.

---

### Post by Steve1961 on 2007-10-22
Just to update my first post, I waited until Gutsy was officially released before upgrading my Thinkpad.  This has also been dist-upgraded since Dapper, and on this occasion the update manager method of upgrading was almost flawless (thought I'd give it another shot).  Only minor issue I encountered was that the upgrade process changed my default gdm login theme and background, but this was easily fixed.  Other than that, everything seems to have gone well - the restricted drivers manager even offered to install a driver for the onboard dial-up modem - not that I ever use it.  Hope the next upgrade to Hardy goes just as well :)

---

