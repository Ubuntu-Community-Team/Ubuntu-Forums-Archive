---
title: "Configure mail to work as send only"
date: 2009-11-30
forum: Server Platforms
---

### Post by bobbywayn on 2009-11-30
Total n00b on the linux mail server. I cannot get mail notifications to go when a customer signs up for membership on website. I have tried postfix, sendmail and exim4. I've probably mucked up the configuration totally. I am running ubuntu server 8.04.2 on an HP Netserver LC 2000 r. Apache, MySql and PHP all running fine. I've done LAMP servers, but i must have done something wrong.

I am not adverse to restarting from scratch, so if anybody can tell me how to easily install an MTA that only needs to send mail notifications, it would greatly be appreciated. Send links if need be, but I have followed several and am lost. I am nearing deadline on these sites (one is OsCommerce the other in Joomla).

regards,
Bobby Wayne Truemark

---

### Post by dmizer on 2009-11-30
Are you positive that your internet provider allows smtp port 25 outbound? Most providers block this to prevent spam.

---

