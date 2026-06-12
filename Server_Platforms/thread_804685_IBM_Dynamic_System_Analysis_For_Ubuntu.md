---
title: "IBM Dynamic System Analysis For Ubuntu"
date: 2008-05-23
forum: Server Platforms
---

### Post by andgrim on 2008-05-23
I was wondering if any has had success install IBM's Dynamic System Analysis (collects and analyzes system information) on Ubuntu Server by converting the rpm to a deb package? Currently the only listed supported OS on IBM's site is SUSE and RHEL.

[http://www-03.ibm.com/systems/management/dsa.html](http://www-03.ibm.com/systems/management/dsa.html)

Thanks For your Help,
Andrew

---

### Post by pdwerryhouse on 2008-05-23
I was using this package (on SuSE) just yesterday. It's been pretty badly packaged; essentially, all they did was take a tarball, shove it into an rpm and then add some postinstall scripts that untarred it. I don't quite know why they even bothered.

I suspect alien might not know what do with such a package, so probably the best way for you to use it on ubuntu is to manually extract the RPM's contents and then untar the tarball somewhere.

Eg:

rpm2cpio < ibm_utl_dsa_210i_sles9_x86-64.rpm | cpio -id
cd usr/local/dsalin
tar xzf dsa-sles.tgz
cd dse-sles
./collectall

The RPM postinstall scripts put it in /opt/IBM/DSA; that's probably the best place to untar it to.

Cheers,

Paul

---

