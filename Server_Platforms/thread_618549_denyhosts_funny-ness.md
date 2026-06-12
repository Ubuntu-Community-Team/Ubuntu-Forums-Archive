---
title: "denyhosts funny-ness"
date: 2007-11-20
forum: Server Platforms
---

### Post by maerlma on 2007-11-20
I have installed denyhosts on my server and it has worked very well for the last two weeks or so. However, I did notice a funny thing. For some reason, it added 127.0.0.1 to hosts.deny . I looked through /var/log/* and didn't find anything, except that I had tried to send mail to an Exchange server on my network that failed over and over before postfix gave up. Would that have caused the issue? Also, before this happened I changed denyhosts.conf to block access to all services for offending hosts. Any ideas on what might have caused this and should I be worried?

#############################################
#
# BLOCK_SERVICE: the service name that should be blocked in HOSTS_DENY
#
# man 5 hosts_access for details
#
# eg.   sshd: 127.0.0.1  # will block sshd logins from 127.0.0.1
#
# To block all services for the offending host:
BLOCK_SERVICE = ALL
# To block only sshd:
#BLOCK_SERVICE  = sshd
# To only record the offending host and nothing else (if using
# an auxilary file to list the hosts).  Refer to:
# [http://denyhosts.sourceforge.net/faq.html#aux](http://denyhosts.sourceforge.net/faq.html#aux)
#BLOCK_SERVICE =
#
#############################################

---

