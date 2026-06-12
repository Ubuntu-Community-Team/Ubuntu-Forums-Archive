---
title: "Syslog entry unremovable after apache2 upgrade"
date: 2013-08-15
forum: Server Platforms
---

### Post by Seb_Boffen on 2013-08-15
Syslog entry un removable after apache2 upgrade

After the upgrade of apache from 2.4.2 to 2.4.6 I end up with a syslog entry witch I'm unable to remove called: File /etc/apache2/${APACHE_LOG_DIR}/error.log
I manually added the entry in the past but I'm unable to find where syslog gets the entry from as it’s not the one defined in the vhost files nor in the /etc/syslog.conf file.
Could anyone help although it’s not a big issue I'd like to keep the overview of my log files clean, I'm using webmin to browse through the syslog files. 
Or maybe knows of an program to delete entries not able to edit with rsyslog in webmin.

Simular files I have witch behave the same but have an purpose:

Output from dmesg
File /var/webmin/miniserv.error

I don't like to edit them but I'll give you an example of what I mean.

---

