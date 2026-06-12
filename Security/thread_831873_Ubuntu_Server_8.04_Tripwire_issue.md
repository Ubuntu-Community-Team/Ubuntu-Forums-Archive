---
title: "Ubuntu Server 8.04 Tripwire issue"
date: 2008-06-17
forum: Security
---

### Post by gnerdman on 2008-06-17
I just installed Ubuntu 8.04 server, installed Tripwire from the repository, and configured it.  When I run a check and look at the report, the host IP address is incorrect - it shows 213.28.xxx.xxx and my internal network is 192.168.xxx.xxx.  Where does Tripwire get the IP address?  Why would it report an IP that isn't even remotely related to my host?  Thanks in advance.

---

### Post by gaten on 2008-06-19
It's possible that it's grabbing the IP from you actual external IP. Go to [www.whatsmyip.org](www.whatsmyip.org) and see if they match.

If they don't I would look at the config file and see if that IP appears anywhere inside of it.

---

