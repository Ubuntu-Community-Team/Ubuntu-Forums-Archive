---
title: "Apache sites as different users"
date: 2013-02-27
forum: Security
---

### Post by superspinner on 2013-02-27
We have a LAMP setup serving multiple CMS that are used by different end-users.  Recently a plug-in for a joomla site wasn't being properly patched by one of those end-users and that site was hacked.  Currently all of the sites run as the same ubuntu user in apache and we would like to run each site as a different ubuntu user to eliminate the security issues if one of the sites is hacked. Can anyone offer directions for how to do this or point me to some documentation? Thanks.

---

### Post by hydn79 on 2013-02-27
The easiest why would be to run PHP with fastcgi. Your problem is most likely not Apache itself but vulnerable PHP scripts.

Sounds like you are still running PHP under mod_php.

cPanel for example you could do this in a few clicks and each website/cPanel user & their user-traffic would access PHP as different user accounts thus restricting security issues to only that user. But cPanel isn't Ubuntu compatible. [http://cpanel.net/cpanel-whm/system-requirements/](http://cpanel.net/cpanel-whm/system-requirements/)

So you would have to do this manually. Its not hard but you just have to know how or find someone to do it.

---

### Post by unspawn on 2013-02-27
[http://httpd.apache.org/docs/current/programs/suexec.html](http://httpd.apache.org/docs/current/programs/suexec.html)
[http://docs.joomla.org/How_do_phpSuExec_file_permissions_work%3F](http://docs.joomla.org/How_do_phpSuExec_file_permissions_work%3F)

*cPanel is "just" a web-based management panel and most that provide, deploy or run it shouldn't be running it in the first place IMNSHO.

---

### Post by superspinner on 2013-02-28
Thank you both!  I setup cpanel today and it seems there is a way we can use it that will also help with some of our other annoyances.  Thank you again!!!

---

