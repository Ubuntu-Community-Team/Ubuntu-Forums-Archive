---
title: "cgi script wants to download, not execute"
date: 2008-01-07
forum: Server Platforms
---

### Post by detachment2702 on 2008-01-07
i recently installed ubuntu server (which has been GREAT by the way) but I ran into a little problem today. I wanted to install a cgi file (which I had never done before) so I downloaded it, moved it to /usr/lib/cgi-bin, chmoded it to 775 and made sure it belonged to www-data. However if I try to access the script at [http://localhost/cgi-bin/script.cgi](http://localhost/cgi-bin/script.cgi) I am prompted to download the script and it does not execute. What could be the problem?

---

### Post by metoor30 on 2008-01-07
Look in /etc/apache2/mods-enabled and make sure there is a cgi.load symlink to /etc/apache2/mods-available/cgi.load.

This usually happens when the proper apache modules are not loaded.

---

