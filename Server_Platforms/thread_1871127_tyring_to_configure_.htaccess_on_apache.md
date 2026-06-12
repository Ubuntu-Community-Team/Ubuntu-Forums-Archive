---
title: "tyring to configure .htaccess on apache"
date: 2011-10-28
forum: Server Platforms
---

### Post by den372 on 2011-10-28
Hi I have been tring to enable .htaccess on apache 2. I have read the link [https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

and this has been very helpful.  Has anyone been able to do this recently. I have tried to use the above guide line. I do get prompted for a un and password if I access /public_html but the server does nothing afterwards. If i try to access the /var/www html doc the system simply hangs. Any input or suggestions is greatly appreciated.

---

### Post by SeijiSensei on 2011-10-28
.htaccess files are disabled by default in the Ubuntu implementation of Apache.  Look at /etc/apache2/sites-enabled/000-default.  You'll see an "AllowOverride None" directive in the default virtual host configuration.  That disables changes via .htaccess.  See if replacing "None" with "All" in this file and restarting Apache helps.

---

