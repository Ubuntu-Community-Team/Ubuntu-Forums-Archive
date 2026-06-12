---
title: "Sarg getword error"
date: 2009-11-05
forum: Server Platforms
---

### Post by ldavisson on 2009-11-05
I have rebuilt the access file. I think it might be that we have some long FQDN but in the log they are all ip addresses. I am using the dansguardian log right now 

sudo sarg
SARG: getword loop detected.
SARG: searching for 'x20'
SARG: Maybe you have a broken record or garbarge in your access.log file.

Here are few of the lines from the Access file.
1257270662.816    168 192.168.1.225 TCP_MISS/301 141 GET [http://yahoo.com](http://yahoo.com) - DEFAULT_PARENT/127.0.0.1 -

Please let me know if you need any conf files.

---

### Post by ldavisson on 2009-11-05
I read a post to that they were able to get SARG x20 error if they ran it through Webmin.
So I installed Webmin and got it working and here is the error through Webmin.
Does anyone have SARG Running with Dansguardian log working?

SARG: getword loop detected.
SARG: searching for 'x5d'
SARG: Maybe you have a broken record or garbage in your access.log file.

---

