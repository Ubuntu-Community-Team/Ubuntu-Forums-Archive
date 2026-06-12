---
title: "Apache removed from cloud instance won't reinstall"
date: 2011-02-24
forum: Ubuntu Cloud and Juju
---

### Post by Japhering on 2011-02-24
I had a lamp install on an Amazon AWS instance running the 10.10 cloud image.   One of my colleagues in trying to install subversion and trac .. decided that it would be faster to clean up apache by uninstalling and reinstallling. 

The only problem is that the reinstall fails... the binaries all install, but /etc/apache2 ends up with only directories and no files..  

Anyone have any ideas on what might be happening and how to fix it ?

Thanks.

---

### Post by kim0 on 2011-02-25
Hi,
Get a list of apache packages installed
dpkg -l | grep apache

then perform
apt-get purge apache2 apache2-mpm-worker ... <all pkgs here>

this will completely remove all apache2 packages, then try reinstalling them fresh

---

