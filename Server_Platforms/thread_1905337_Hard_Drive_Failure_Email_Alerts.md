---
title: "Hard Drive Failure Email Alerts"
date: 2012-01-06
forum: Server Platforms
---

### Post by umbernaut on 2012-01-06
I was surprised to find google did not easily return an answer on a simple question like: "linux hard drive failure email alerts" or "ubuntu alerts for hard drive failure."

Sure, it gave me stuff for non-RAID setups.  I got info on setting up alerts in webmin, but I need email alerts for drives failing before they totally fail, with a physical RAID controller in the server, etc. (also running LVM if that matters).

I did find this:
[http://www.cyberciti.biz/tips/linux-server-predicting-hardware-failure.html](http://www.cyberciti.biz/tips/linux-server-predicting-hardware-failure.html)

mcelog seems straight-forward and easy.  Also, I've done stuff with SNMP traps before too.

Question: anyone have any other good solutions?  This is a "headless" server, with webmin on it.

I just want to get an email when a drive starts flaking before it totally flakes.

---

### Post by ThePol1 on 2012-01-06
Try the Smartmontools. Here are a few links that helped me out:
[http://techgurulive.com/2009/04/08/how-to-set-up-smart-monitoring-in-ubuntu-smartmontools/](http://techgurulive.com/2009/04/08/how-to-set-up-smart-monitoring-in-ubuntu-smartmontools/)
 
[http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/](http://blog.shadypixel.com/monitoring-hard-drive-health-on-linux-with-smartmontools/)
 
[http://myminutes.wordpress.com/2011/02/13/short-tutorial-smartd-with-mail-notification-to-remote-address/](http://myminutes.wordpress.com/2011/02/13/short-tutorial-smartd-with-mail-notification-to-remote-address/)
 
I installed the following and used my Gmail account to send notification emails:
Smartmontools
bsd-mailx
mailutils
ssmtp

---

