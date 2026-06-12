---
title: "Apache Upgrading"
date: 2010-11-14
forum: Server Platforms
---

### Post by adamrobertson on 2010-11-14
Hi,
My Server is 8.04 (hardy) and Apache is 2.2.8
 
I have been receiving emails from Apache each time a new stable release is available, most of which say you should install them due to security issues.
 
The current stable release of apache being offered is 2.2.17
 
 
Q1) Do you recommend I upgrade from Apache 2.2.8 to 2.2.17?
 
Q2) Does this come automatically with my regular updates via Update Manager once the Ubuntu community thinks its stable enough (it appears that it doesnt)?
 
Q3) What is the best way to install the update?
 
Q4) Any concerns about installing it into a live enviroment? I dont have a development platform to try it in first.
 
Thanks for your help.
Adam

---

### Post by James78 on 2010-11-14
1. Always a good idea, but remember that your release is still supported for security updates as it's not at end of life. I still suggest upgrading to the latest release.
2. Yes and no. Usually there will only be security updates. If you want to upgrade Apache, you need to upgrade to the latest LTS or latest release. Latest LTS has 2.2.14 and latest release should have 2.2.16.
3. Upgrade to 10.04 LTS or 10.10.
4. You should be perfectly fine. The install will mess a little with your configuration files, but it'll let you know when you update, and you'll be able to view what changes are being made, then you can mend the files yourself. I recommend always going with the latest configuration files, just because it's a good idea.

---

### Post by xAnarChisTx on 2010-11-15
> **adamrobertson said:**
> Hi,
My Server is 8.04 (hardy) and Apache is 2.2.8
 
I have been receiving emails from Apache each time a new stable release is available, most of which say you should install them due to security issues.
 
The current stable release of apache being offered is 2.2.17
 
 
Q1) Do you recommend I upgrade from Apache 2.2.8 to 2.2.17?
 
Q2) Does this come automatically with my regular updates via Update Manager once the Ubuntu community thinks its stable enough (it appears that it doesnt)?
 
Q3) What is the best way to install the update?
 
Q4) Any concerns about installing it into a live enviroment? I dont have a development platform to try it in first.
 
Thanks for your help.
Adam

This is exactly what I am looking to do as well, but I was wondering how to go about obtaining the Apache upgrade.  I did try apt-get upgrade, but it stated that I already have the most up-to-date version.  Is there a deb package that I need to add to pull down the latest version, or how would one go about upgrading?

---

### Post by James78 on 2010-11-15
If you really must, you can go download the latest versions of Apache from packages.ubuntu.org (currently only at 2.2.16 however), however, as I noted before, as long as your release is not at end of life, security updates should still be released, and although you may have an older version of Apache, it should be safe security wise. I still recommend just upgrading the OS to the latest release however, because then you can just upgrade the packages for everything on the system, more features!

---

