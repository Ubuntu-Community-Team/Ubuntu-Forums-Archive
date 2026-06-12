---
title: "In phpmyadmin ($cfg['Servers'][$i]['hide_db']) does not work"
date: 2017-08-15
forum: Server Platforms
---

### Post by degtyarev on 2017-08-15
Hello.
Ubuntu Server 16.04 +all updates (phpmyadmin  4:4.5.4.1-2ubuntu2)
In config.in.php option $cfg['Servers'][$i]['hide_db'] = '(information_schema|phpmyadmin|mysql|performance_schema)'; does not work. 
The listed databases are still displayed in phpmyadmin  (information_schema,phpmyadmin,mysql,performance_schema)
On centos and Windows this setting works.
Any ideas?

---

