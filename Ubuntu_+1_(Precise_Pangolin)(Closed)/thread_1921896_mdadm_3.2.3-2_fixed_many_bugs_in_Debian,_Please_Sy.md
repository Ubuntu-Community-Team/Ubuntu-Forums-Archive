---
title: "mdadm 3.2.3-2 fixed many bugs in Debian, Please Sync"
date: 2012-02-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nutznboltz on 2012-02-07
[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/920324](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/920324)

Format: 1.8
Date: Wed, 18 Jan 2012 22:33:01 +0400
Source: mdadm
Binary: mdadm mdadm-udeb
Architecture: source i386
Version: 3.2.3-2
Distribution: unstable
Urgency: low
Maintainer: Debian mdadm maintainers <pkg-mdadm-devel@lists.alioth.debian.org>
Changed-By: Michael Tokarev <mjt@tls.msk.ru>
Description: 
 mdadm      - tool to administer Linux MD arrays (software RAID)
 mdadm-udeb - tool to administer Linux MD arrays (software RAID) (udeb)
Closes: 607375 628667 633880 637068 641584 641886 641972 645563 650630 651737 651880 652547 655212
Changes: 
 mdadm (3.2.3-2) unstable; urgency=low
 .
   [ Michael Tokarev ]
   * new upstream bugfix/stable version, with lots of fixes all over.
     Closes: #641886, #628667, #645563, #651880, #607375, #633880
   * update Neil's email (Closes: #650630)
   * update mdadd.sh to version 1.52 (Closes: #655212)
   * fixed a typo (RAID6 vs RAID10) in FAQ (Closes: #637068)
   * declare ordering dependency for multipath-tools-boot in
     mdadm-raid init script (Closes: #641584)
     While at it, remove mention of devfsd
   * added Slovak (sk.po) po-debconf translation from Slavko <linux@slavino.sk>
     (Closes: #641972)
   * set nice value of the check/resync thread too, together with I/O
     scheduling class, based on patch by Sergey B Kirpichev (Closes: #652547)
   * small changes for debian/checkarray
   * (internal) move files from contrib/* topgit branches into debian directory
   * remove dh_testroot from clean target
   * add myself to uploaders
 .
   [ Peter Eisentraut ]
   * Added support for "status" action to mdadm init script (Closes: #651737)

---

### Post by xyzzyman on 2012-02-07
You've already found where to go on launchpad. What would you like from any of us?

---

### Post by tekstr1der on 2012-02-07
> **xyzzyman said:**
> You've already found where to go on launchpad. What would you like from any of us?

Me-too's?

> **nutznboltz said:**
> [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/920324](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/920324)

Good catch, but we're way past the import freeze. Hope for an exception!

---

### Post by nutznboltz on 2012-02-08
> **tekstr1der said:**
> Good catch, but we're way past the import freeze. Hope for an exception!

> [b][Requesting a new package for Ubuntu](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)
Ubuntu wiki / scraped February 8, 2012[/b]

Packages that have recently been added to Debian unstable will be automatically synced into Ubuntu prior to the Debian Import Freeze (DIF). After the Debian Import Freeze, you will have to file a bug with the summary field "Please sync <packagename> from debian <distro>" where <packagename> is the package you would like to see. Find the date for Debian Import Freeze on the release schedule page. 
So I updated the title of the bug.  I also added a test case and set the testcase tag.  Is there anything else to do?

---

### Post by dino99 on 2012-02-08
> **nutznboltz said:**
> So I updated the title of the bug.  I also added a test case and set the testcase tag.  Is there anything else to do?

well, we are in frozen archives time now, so you only can cross your fingers & pray than a dev sponsor see this report :(
or be more active:
- download the deb package from debian and install it with gdebi (hoping that ubuntu have not tweaked too much that package compared to the debian one)
- send a message to the ubuntu maintainer via launchpad (clint@ubuntu.com) to catch its attention.

---

### Post by nutznboltz on 2012-02-08
Looking at the list of fixes upgrading mdadm from 3.2.2 to 3.2.3 shows some severe regressions were fixed.

mdadm: re-add fails (regression in mdadm-3.2.2-1ubuntu1)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=651880](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=651880)

mdadm: segmentation fault when converting raid10 to raid0
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645563](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=645563)

mdadm-raid does not assemble mds on multipath devices
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641584](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=641584)

---

### Post by nutznboltz on 2012-02-08
I added the regression-update tag to 
[https://bugs.launchpad.net/bugs/920324](https://bugs.launchpad.net/bugs/920324)

If you think that wasn't the right tag to use please let me know, thanks.

---

### Post by dino99 on 2012-02-08
Have you followed my comments above into post #5 to join the maintener guy ?
Posting your whinings here is useless.

---

### Post by nutznboltz on 2012-02-08
> **dino99 said:**
> Have you followed my comments above into post #5 to join the maintener guy ?
Posting your whinings here is useless.

Paradoxically useless modulo getting advice from you.

I subscribed the maintainer, thanks.

---

### Post by dino99 on 2012-02-08
> **nutznboltz said:**
> Paradoxically useless modulo getting advice from you.

I subscribed the maintainer, thanks.

yes, here its the users place, devs rarely glance on forum

but you got it, "importance" is set on "high" now :)

---

