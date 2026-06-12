---
title: "apache mod_rewrite &quot;null&quot; string"
date: 2011-03-07
forum: Server Platforms
---

### Post by maghajan on 2011-03-07
Hi, can anyone tell me what is going on with my mod_rewrite? Below is some output from the rewrite log file I have created. Why is that "/null" being added toward the end of my rewrites?? Any help is appreciated!!!



127.0.0.1 - - [07/Mar/2011:14:31:18 --0600] [localhost/sid#7fbc21aec840][rid#7fbc21dd88c8/initial] (3) [perdir /var/www/LabOrders/] add path info postfix: /var/www/LabOrders/NewLabOrder -> /var/www/LabOrders/NewLabOrder/null

127.0.0.1 - - [07/Mar/2011:14:31:18 --0600] [localhost/sid#7fbc21aec840][rid#7fbc21dd88c8/initial] (3) [perdir /var/www/LabOrders/] strip per-dir prefix: /var/www/LabOrders/NewLabOrder/null -> NewLabOrder/null

127.0.0.1 - - [07/Mar/2011:14:31:18 --0600] [localhost/sid#7fbc21aec840][rid#7fbc21dd88c8/initial] (3) [perdir /var/www/LabOrders/] applying pattern '^NewLabOrder/$' to uri 'NewLabOrder/null'

127.0.0.1 - - [07/Mar/2011:14:31:18 --0600] [localhost/sid#7fbc21aec840][rid#7fbc21dd88c8/initial] (3) [perdir /var/www/LabOrders/] add path info postfix: /var/www/LabOrders/NewLabOrder -> /var/www/LabOrders/NewLabOrder/null

127.0.0.1 - - [07/Mar/2011:14:31:18 --0600] [localhost/sid#7fbc21aec840][rid#7fbc21dd88c8/initial] (3) [perdir /var/www/LabOrders/] strip per-dir prefix: /var/www/LabOrders/NewLabOrder/null -> NewLabOrder/null

127.0.0.1 - - [07/Mar/2011:14:31:18 --0600] [localhost/sid#7fbc21aec840][rid#7fbc21dd88c8/initial] (3) [perdir /var/www/LabOrders/] applying pattern '^NewLabOrder$' to uri 'NewLabOrder/null'

---

