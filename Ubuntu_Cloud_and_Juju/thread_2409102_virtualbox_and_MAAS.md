---
title: "virtualbox and MAAS"
date: 2018-12-27
forum: Ubuntu Cloud and Juju
---

### Post by khbkhb on 2018-12-27
[https://blog.ubuntu.com/2015/01/15/virtualbox-extensions-for-maas](https://blog.ubuntu.com/2015/01/15/virtualbox-extensions-for-maas)  is a nice writeup, but a little dated (Ivan, the author, mentions he'd planned on some script improvements ... but that was some years back....) On the specific issue of getting commissioning to work, MAAS (understandably) wants to know the powertype ... the blog posting suggests . "The small fragment of code used by the template is listed here and it is part of the file /etc/maas/templates/power/ether_wake.template:" unfortunately in MAAS 2.4.2 doesn't have /etc/maas/templates...                          ls /etc/maas                          drivers.yaml  preseeds  rackd.conf  regiond.confI *assume* that the reference to "${home_dir}/VBox_extensions/power_on i" means that I should create a VBox_extensions subdirectory ... as there isn't one yet (if so, seems like the "template" above needs to invoke it ... so it needs to be coordindated ;>).I'm sure folks (especially Canonical folks ;>) have used VirtualBox with MAAS so I'd think there's well known solutions ... so pointers to FM or other documents much appreciated.Host: Mac OS X 10.14.2VirtualBox: 6.0.0MAAS: 2.4.2 Ubuntu 18.04.1 LTS

---

