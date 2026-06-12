---
title: "ModSecurity Install"
date: 2018-08-28
forum: Security
---

### Post by billybobjay on 2018-08-28
I have installed mod security, [https://blog.rapid7.com/2017/04/09/how-to-configure-modsecurity-with-apache-on-ubuntu-linux/](https://blog.rapid7.com/2017/04/09/how-to-configure-modsecurity-with-apache-on-ubuntu-linux/) following those instructions and a few others here and there while attempting to troubleshoot.  I have apache2 on Ubuntu 16.04 and have gone through all the steps in the tutorial & double checked them multiple times for mistakes.
I have even restarted the entire server thinking a service or such was not properly restarted.

What confuses me is when I run-

sudo apachectl -M | grep security
 
I get the following as expected-

security2_module (shared)

However when I run a test -

 curl 'http://192.168.111.2/?q="><script>alert(1)</script>'

I do not get the 403 Forbidden response I should with modsecurity running.  

At this point I am just not sure how to troubleshoot this further and would appreciate any suggestions on how to narrow down the issue.  I can copy and paste any files or such needed to help trouble-shoot this issue.

Thanks,

---

