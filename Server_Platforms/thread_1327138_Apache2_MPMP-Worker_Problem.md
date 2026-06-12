---
title: "Apache2 MPMP-Worker Problem"
date: 2009-11-15
forum: Server Platforms
---

### Post by sangprabv on 2009-11-15
I just installed Apache2 with MPM-Worker and PHP5-CGI. Installation had no problem. Apache's restarted. I add ExecCGI directive to my VirtualHost. Test it with phpinfo and I got PHP runs on CGI mode. I do ps aux and see that apache starts with 5 daemon. I edit apache2.conf and modify <IfModule mpm_worker_module> StartServers 20. Restart Apache but it still show 5. I check mods-available and I see no mpm* files there. Where does the configuration files stored? How to check whether the Apache is already run with mpm_worker not mpm_prefork? Many thanks for any replies.

---

