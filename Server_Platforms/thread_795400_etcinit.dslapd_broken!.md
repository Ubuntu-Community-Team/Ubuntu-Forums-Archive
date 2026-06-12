---
title: "/etc/init.d/slapd broken!?"
date: 2008-05-15
forum: Server Platforms
---

### Post by honeydew on 2008-05-15
I have been running ldap successfully on ubuntu 7.04 for exactly 1 year.. until my ssl certificates expired(forgetful me).  Once I figured out that it was my certificates I went ahead and updated everything..  however /etc/init.d/slapd start/restart/stop no longer works...  I have tryed running update-rc.d remove -f slapd and update-rc.d slapd defaults.  This dosnt seem todo anything.  I can however start the slapd daemon from the command line(and it runs fine)  this is okay, however this is a production machine and is no longer reboot safe with out the proper init.d scripts.  

Update:
I have just been informed that the same issue is occurring on one of our other ldap machines as well.

---

