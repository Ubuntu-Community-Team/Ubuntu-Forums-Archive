---
title: "Citrix ICA Receiver 12.100 corrupt heads up"
date: 2012-04-29
forum: The Cafe
---

### Post by keithpeter on 2012-04-29
Hello All

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

I use the Citrix ICA Client to access my Windows desktop at College from home on my Linux box.

I went to reinstall the client after a clean install of 12.04 on the big box: got errors about a bad .deb

[http://forums.citrix.com/thread.jspa?threadID=306346&tstart=0](http://forums.citrix.com/thread.jspa?threadID=306346&tstart=0)

Looks like someone at Citrix has made a mistake with the compression of the file in some way, and that has made it impossible to install the i386 version of the receiver on any linux distro. The new version (12.100) was uploaded a few days ago. Of course, Citrix have removed all the earlier versions from their site, but I was able to find a backup of the 12.000 .deb and install that.

Just in case anyone needs to know this as they re-install or upgrade: hang onto that version 12.000 deb!

Mods: this might be better in Installation and Upgrades now I'm thinking about it

---

### Post by cptrohn on 2012-04-29
Thanks for the heads up!

I need to be able to access Citrix from Linux boxes as well.

You wouldn't have a link to the older .deb would you?

---

### Post by keithpeter on 2012-04-29
> **cptrohn said:**
> Thanks for the heads up!

I need to be able to access Citrix from Linux boxes as well.

You wouldn't have a link to the older .deb would you?

64 bit debs are OK apparently. It is i386 debs that have the problem.

Google for the previous deb by file name - icaclient_12.0.0_i386.deb - if you don't have copies of the debs from last time. Google Code is a trusted source. I think Citrix remove older versions of the .debs and .rpms from their own site.

---

