---
title: "denyhosts keeps blocking my external ip"
date: 2010-10-31
forum: Security
---

### Post by holiday on 2010-10-31
I've been using Deny Hosts for a couple of years now without trouble. My router forwards SSH calls to host tock on my LAN. My router's internet hostname is michigan.  

I keep an svn repository on tock and access it through michigan. In this way I can update my repository when I'm at home or away.

Just today, however, whenever I try any ssh to michigan, I get a closed connection and find michigan in my hosts.deny file. I delete it, make a successful connection, but then on my next attempt - there I am in the hosts.deny file again.

I've worked around it by putting michigan into my hosts.allow file, but I would really like to know what's going on. 

I've configured Hosts Deny to lock out IPs after three failed attempts, but it is locking out michigan after one successful connection.

---

### Post by FuturePilot on 2010-10-31
Perhaps it blocked you at one time for 3 failed logins and you didn't remove the IP properly? Try this and then see if it happens again.
[http://denyhosts.sourceforge.net/faq.html#3_19]("http://denyhosts.sourceforge.net/faq.html#3_19")

WORK_DIR refers to /var/lib/denyhosts

---

### Post by holiday on 2010-10-31
> **FuturePilot said:**
> Perhaps it blocked you at one time for 3 failed logins and you didn't remove the IP properly? Try this and then see if it happens again.
[http://denyhosts.sourceforge.net/faq.html#3_19]("http://denyhosts.sourceforge.net/faq.html#3_19")

WORK_DIR refers to /var/lib/denyhosts

Thank you. And thank you so much for resolving WORK_DIR. 

I do not know how to change the prefix, but I want to mark this solved.

---

### Post by cariboo on 2010-10-31
Go to the to of the page in this thread and click Thread Tools->Mark this thread solved

---

