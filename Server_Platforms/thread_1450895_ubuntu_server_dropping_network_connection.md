---
title: "ubuntu server dropping network connection"
date: 2010-04-09
forum: Server Platforms
---

### Post by stdcinout on 2010-04-09
hi guys for some reason my ubuntu server always drop network connection 

i have bind , samba, cups ,webmin and ssh server installed.  

static ip 

no firewall configured.. 

this is mainly for intranet print server. 

the bind thing, and samba may not be properly configured as i am still learning how to configure them 

what bothers me is the network connection drops all the time I am configuring the printers or on the webmin 

apparently it is not the network issue as other machine are working fine 

google get me to 

tail /var/log/daemon.log
tail /var/log/kern.log
tail  /var/log/messages
tail /var/log/syslog

i saw those log.. some  error message dont give me any clue.. 


any suggestion what i should do? thanks

---

### Post by Iowan on 2010-04-09
I don't suppose it's running headless? 
There are a couple of other threads about problems with headless machines. [Here]("http://ubuntuforums.org/showthread.php?p=9094422#post9094422") is one - mentions acpi=off as possible solution.

---

### Post by olograph on 2012-10-18
I'll try it here and get back to you people

---

