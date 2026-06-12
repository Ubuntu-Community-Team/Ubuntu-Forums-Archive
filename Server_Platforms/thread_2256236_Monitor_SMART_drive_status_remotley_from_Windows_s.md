---
title: "Monitor SMART drive status remotley from Windows system?"
date: 2014-12-10
forum: Server Platforms
---

### Post by ADz83 on 2014-12-10
Hi,

Can anybody recommend a program (for Windows) that can monitor multiple remote Ubuntu 10.04 servers drive smart status?

Thanks.

---

### Post by tgalati4 on 2014-12-11
You could set up Nagios and Cacti and monitor the servers from a browser page in Windows.  If you just want SMART status, you could write a script to email when SMART changes.  You can set up an email notifier in Windows.

> tgalati4@Mint14-Extensa ~ $ sudo smartctl -H /dev/sda
smartctl 5.43 2012-06-30 r3573 [x86_64-linux-3.5.0-51-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)

Using hardware RAID utilities:

[http://serverfault.com/questions/589070/how-to-monitor-the-hard-disk-status-behind-dell-perc-h710-raid-controller-with-c](http://serverfault.com/questions/589070/how-to-monitor-the-hard-disk-status-behind-dell-perc-h710-raid-controller-with-c)

---

### Post by nerdtron on 2014-12-11
I remember some server (manufacturers like supermicro) let's you install a utility in Linux that will give you access to the system storage utility. You can view hard drive and raid status from any web browser.
 But only RPMs are available not ubuntu.

One possible solution is to create a script on the Ubuntu server to check for the drive status and then send email to you.

---

### Post by MAFoElffen on 2014-12-11
Wouldn't another option be to install the "Subsystem for UNIX-based Applications" to the MS Server so they can interact with each other a little more seamlessly(?)

---

