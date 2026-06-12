---
title: "LSI MegaRAID 84016E software"
date: 2008-12-16
forum: Server Platforms
---

### Post by hewittm on 2008-12-16
Hi.  I'm an experienced Debian sysadmin who is setting up a Ubuntu 8.04 amd64 server.  It includes storage mounted via an [LSI MegaRAID SAS 84016E adapter](http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/megaraid_sas_84016e/index.html).  I was trying to set up the LSI MegaRAID Storage Manager software and having no end of problems.

The software is only in RPM format.  I followed a similar [thread](http://ubuntuforums.org/showthread.php?p=6331876) from the forums, but that only got me so far.

After converting that via alien, I had to resolve some minor issues (install to /etc/rc.d/rc?.d/, /etc/init.d/ script asking for sh but needing bash, etc.) but still have major ones.

The LSI jre doesn't appear to work (may be due to 32/64-bit issues), and using the sun-java6-jre allows the vivaldiframework daemon to run (with a fault on 32-bit library libjsig.so).  However, the mrmonitor daemon starts but quickly fails.  I can launch the management UI tool, but it can't connect to the monitor.

I've extracted the MegaCli64 tool so I can support the card, although awkwardly.  I've sent a support request to LSI, but I was wondering if anyone had gotten farther or had another option.  (More details on request.)

---

### Post by jamesstansell on 2008-12-16
Sorry, can't say much.  There is a 32-bit jre package available in the 64-bit repositories, which may possibly be of interest to you.

You may find a little more help in the 64-bit forum.

---

