---
title: "Openqrm fails to initalize database"
date: 2010-07-03
forum: Virtualisation
---

### Post by Smithjoe1 on 2010-07-03
Hey everyone,

I've been stuck on this problem for days trying to figure it out. I've followed the OpenQRM install guide to the letter on a freshly formatted server using ubuntu Lucid Lynx 10.04, everything manages to make and install, I had to upgrade a few of the make dependancies as mysql-client is now 5.1 and busybox's download is a .tar.bz2 and the config was trying to download a .tar.gz file.

So I run through the inital config to the point where it asks to configure my database and I get the following errors in /var/log/messages
Jul  3 16:15:33 SJhost nagios3: SERVICE ALERT: localhost;Disk Space;CRITICAL;HARD;4;DISK CRITICAL - /home/smithjoe1/.gvfs is not accessible: Permission denied
Jul  3 16:15:33 SJhost nagios3: SERVICE NOTIFICATION: root;localhost;Disk Space;CRITICAL;notify-service-by-email;DISK CRITICAL - /home/smithjoe1/.gvfs is not accessible: Permission denied

I've added -A -i '.gvfs' to each of the 4 file lines in /etc/nagios-plugins/config/disk.cfg to try and ignore this. Now all I'm getting is

Jul  3 16:34:21 SJhost logger: openQRM engine: Running as root cmd : /usr/share/openqrm/bin/openqrm init_config
Jul  3 16:34:21 SJhost openQRM init-config[8455]: init_config already running. Skipping re-init

Has anyone been able to get this working on 10.04?

---

### Post by erk on 2010-08-06
Have you tried following the ubuntu howto on the OpenQRM site?

[http://www.openqrm-enterprise.com/fileadmin/DATA/Whitepapers/Setup_your_own_openQRM_Cloud_on_Ubuntu_Lucid_Lynx.10052010.pdf](http://www.openqrm-enterprise.com/fileadmin/DATA/Whitepapers/Setup_your_own_openQRM_Cloud_on_Ubuntu_Lucid_Lynx.10052010.pdf)

---

