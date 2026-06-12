---
title: "Disabling authenticated packages for unattended-upgrade"
date: 2008-12-20
forum: Security
---

### Post by bubba on 2008-12-20
Hi, I'm using a source which does not support GPG package signing ([http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu)), and was wondering if there was a way to disable this requirement when using the 'unattended-upgrade' script.  I know you can pass --allow-unauthenticated to apt, but unattended-upgrade does not run apt (it appears to make API calls to APT), thus I cannot figure out how to disable this requirement.

I realize that this isn't secure, but if there are updates for these packages, I'd prefer them to be updated rather than get an email saying that the update failed since I'm just going to login and install them anyway.  

Thanks,
Bubba

---

