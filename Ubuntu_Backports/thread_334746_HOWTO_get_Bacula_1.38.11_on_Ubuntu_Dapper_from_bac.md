---
title: "HOWTO get Bacula 1.38.11 on Ubuntu Dapper from backports"
date: 2007-01-09
forum: Ubuntu Backports
---

### Post by mforbes on 2007-01-09
I'm currently running Ubuntu 6.06 Dapper and have installed bacula 1.36.3. I would like to upgrade the version of bacula to 1.38.11 but can't seem to get it to work. I have found this version for dapper from [http://www.backports.org](http://www.backports.org) and would like to use apt-get to upgrade my version.

I have added the following line to my sources.list file:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

After adding this line to my sources.list file, I ran apt-get update, then I ran apt-get upgrade but bacula was not in the listed output.

I then tried 
apt-get -t dapper-backports install bacula

and received the following message:
bacula is already the newest version.

How do I get apt-get to use the backport version 1.38.11???

thanks,

Mike

---

### Post by mlind on 2007-02-05
Hi mike,

[http://www.backports.org](http://www.backports.org) contains packages for Debian distributions. Although Ubuntu is a Debian derivative, Debian binary packages are usually not (binary-)compatible with Ubuntu distributions. You can rebuild the bacula source package from backports.org or grab bacula package from Feisty source repository and rebuild that one. You either need to rebuild bacula manually or use third-party provided package if you want newer version for Dapper.

There is no newer 'official' update or backported bacula package for Dapper as you can see from [bacula package list]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=sourcenames&version=all&exact=1&keywords=bacula")

Here's a link for bacula 1.38.11-7ubuntu6 which I built from Feisty source packge. It's untested, but installs fine and probably works okay. There's no source modifications.
[http://www.freefilehoster.com/uploads/1170717667bacula-1.38.11-7ubuntu6_dapper.tar.gz](http://www.freefilehoster.com/uploads/1170717667bacula-1.38.11-7ubuntu6_dapper.tar.gz)

---

