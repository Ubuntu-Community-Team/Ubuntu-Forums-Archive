---
title: "nginx+Magento"
date: 2015-04-09
forum: Server Platforms
---

### Post by dirkman on 2015-04-09
So i search the whole inet for a solution tried it on my owen but i coundn´t do it .

**Now to my problem:**

I set up nginx and mysql php5-fmp on ubuntu ,created a database and copied the Magento files in my www folder .
Than i tried to start it with localhost/magento but i belive it creates a loop , it goes to localhost/magento/index.php/install and after that i get a 404 error back.
I had the same problem on windows with apache but the reason was only the chrome browser and i disabled browser.fix in firefox this inst it.
It musst have something to do with the nginx.conf or the server default maybe the php.ini too.

Can anybody help me please?

---

### Post by midhun_kv on 2015-04-21
Check your www/magento/app/etc/local.xml file. The file may be missing or do not have sufficient permissions.

---

