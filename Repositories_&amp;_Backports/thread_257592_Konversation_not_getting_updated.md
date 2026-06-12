---
title: "Konversation not getting updated"
date: 2006-09-14
forum: Repositories &amp; Backports
---

### Post by Pointwood on 2006-09-14
I recently installed Kubuntu Dapper and it's been running pretty well so far :)

I think I have some kind of odd problem though since Konversation is not getting updated from ver. 0.19 to 1.0 and as far as I can see, it should.

Here is what I think is various relevant information:

My sources:
 
 ## Add comments (##) in front of any line to remove it from being checked.
 ## Use the following sources.list at your own risk.
 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
 
 ## MAJOR BUG FIX UPDATES produced after the final release
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
 
 ## UBUNTU SECURITY UPDATES
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
 
 ## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
 
 ## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
 deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
 deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
 
 ## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
 ## servers. RealPlayer10, Opera and more to come.)
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
 
 ## KDE 3.5.4
 deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main
 
 ## Amarok 1.4.3
 deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) dapper main
 
 ===
 
 apt-cache madison konversation
 konversation | 0.19-0ubuntu4 | [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
 konversation | 0.19-0ubuntu4 | [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
 konversation | 1.0-0ubuntu1~dapper1 | [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
 
 ======
 
 apt-cache policy konversation
 konversation:
   Installed: 0.19-0ubuntu4
   Candidate: 0.19-0ubuntu4
   Version table:
  *** 0.19-0ubuntu4 0
         500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
         100 /var/lib/dpkg/status
 
 ===========
 
 apt-get install konversation
 Reading package lists... Done
 Building dependency tree... Done
 konversation is already the newest version.
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

