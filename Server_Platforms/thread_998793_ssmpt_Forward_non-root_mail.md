---
title: "ssmpt: Forward non-root mail?"
date: 2008-12-01
forum: Server Platforms
---

### Post by digamma on 2008-12-01
How can I get ssmtp to forward local non-root mail to a remote server?  

Example:  
$ echo testing | mail -s test localuser 
should forward the mail to remoteuser@remotehost where remoteuser!=localuser.

It works for root by setting root=otheruser@remotehost in ssmtp.conf. I tried some tricks with /etc/mail/aliases but they're not used by ssmpt.

---

### Post by Philio on 2008-12-01
Have you tried using /etc/aliases?

---

