---
title: "htaccess allowing one ip with authentication?"
date: 2012-08-05
forum: Server Platforms
---

### Post by hesson on 2012-08-05
Hi,

i want to set up .htaccess on my Apache web server such that all users are straight-up denied access except one user which is my IP. Since this IP represents my entire home network, I also want to add authentication in the case the IP is correct to ensure that only I can access that directory and no one else using my home network.

This is how my .htaccess file looks so far:

```

Order deny,allow
Deny from all
AuthType Basic
AuthUserFile /var/www/path_to_forbiden_dir/.htpasswd
AuthName "Protected"
require valid-user
Allow from xxx.xx.xx.xxx

```

where xxx.xx.xx.xxx is my IP

This works in denying IPs outside the local network, however no authentication is shown when I try to access that directory from the IP specified. So, how can I create authentication only for the IP specified?

---

### Post by hesson on 2012-08-05
I resolved the issue after re-reading [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

---

