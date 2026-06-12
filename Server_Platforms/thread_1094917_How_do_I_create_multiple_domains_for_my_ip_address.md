---
title: "How do I create multiple domains for my ip address?"
date: 2009-03-13
forum: Server Platforms
---

### Post by neilevan814 on 2009-03-13
Hello, I have been trying to get a couple different domain names working on my server using vhost configuration, but my server is only serving up one domain name directory.  Does anyone know if this is possible and how to get it to work?

---

### Post by dgoosens on 2009-03-13
did you also add the domains to your hosts file

---

### Post by BkkBonanza on 2009-03-13
See this thread where I answered yesterday.

[http://ubuntuforums.org/showthread.php?t=1093992](http://ubuntuforums.org/showthread.php?t=1093992)

It definitely works so if you still have trouble then post specifics of your config.

---

### Post by neilevan814 on 2009-03-14
Thanks for your replies.  I will check my /etc/hosts file and I will check the link you posted and report back if there are still issues.

---

### Post by neilevan814 on 2009-03-14
I just checked my dyndns.com host service and they had assigned 2 different ip addresses to my multiple domains.  I changed them to the same one and now my vhost configurations are working.  Thanks again.

---

