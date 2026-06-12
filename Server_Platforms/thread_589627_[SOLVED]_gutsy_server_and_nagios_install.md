---
title: "[SOLVED] gutsy server and nagios install"
date: 2007-10-24
forum: Server Platforms
---

### Post by inphektion on 2007-10-24
I just installed a gutsy server on a dell poweredge 1950.. went flawlessly.  Choose LAMP.  
I want to run nagios on it so did an aptitude install nagios-mysql and after the install realized it's quite an old version.  Should I run a newer version or is this the best one?  I hate being out of date. 
I think I noticed a nagios2 package, should I use that instead or just download the latest tarball from the nagios site and try a manual install?
Thanks for any tips in the right direction.

---

### Post by inphektion on 2007-10-24
ok I did an aptitude purge of nagios-mysql and then an aptitude install of nagios2.  then I created htaccess.user file and can login.  
this seems much newer now, 2.9 as opposed to 1.6.  
My only problem now is most documentation seems to referece nagios 1.x is there any good quickstart for nagios2?

---

### Post by inphektion on 2007-10-25
ok after my not so expert testing of nagios, removing it, and then installing nagios2.  I've determined the packages for debian/ubuntu suck.  I really hate how nagios2 was packaged up probably because of my unfamiliarity of nagios but the only way to learn is to read.  When you install the nagios2 package things go in different places than most documentation describes it, the samples are different, and some defaults (like setting up a gateway) are not ideal.  
So I removed that and followed the quickstart to manually installing the latest nagios from the tarball.  Even though 3.0xxx whatever is beta the best documentation or at least most updated seems to exist for it.  Also it was really killing me that using the package manager to install nagios2 made everything be called nagios2.  I just want it called nagios..  now it is even though i'm running nagios3.  

My point for anyone looking to install nagios, just grab the latest and do it manually.  I use apt-get for 98% of stuff but this is another app it just isn't worth it to use it for.

---

### Post by ceefour on 2008-02-11
> **inphektion said:**
> My point for anyone looking to install nagios, just grab the latest and do it manually.  I use apt-get for 98% of stuff but this is another app it just isn't worth it to use it for.


Definitely agreed with inphektion on this one! Me too had the same issues :popcorn:

---

### Post by ceefour on 2008-02-11
See:

[http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html](http://www.ubuntugeek.com/nagios-network-monitoring-system-setup-in-ubuntu.html)

for easy Ubuntu-friendly Nagios setup.

---

