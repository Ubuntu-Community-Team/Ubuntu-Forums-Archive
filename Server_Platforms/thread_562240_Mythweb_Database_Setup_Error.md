---
title: "Mythweb Database Setup Error"
date: 2007-09-28
forum: Server Platforms
---

### Post by severedspirit on 2007-09-28
just upgraded to the new SVN release of mythweb, however im having a couple of problems, when viewing the page it says
-------------------
Database Setup Error

The database environment variables are not correctly set in the
included .htaccess file. Please read through the comments included
in the file and set up the db_* environment variables correctly.

Some possible solutions are to make sure that mod_env is enabled
in httpd.conf, as well as having followed the instructions in the
README about the AllowOverride settings.
-------------------

Ive had a look through he .htaccess file and it seems fine, anyone got any idea how to fix it, its probably just some small stupid thing ive forgotten to do, thanks ahead

---

### Post by merlin69 on 2007-09-29
Hava had same error here. The .htaccess link to /etc/mythtv/mythweb-htaccess.conf was broken (links to /etc/mythtv/mythweb-htaccess). Removing .htaccess and linking it to /etc/mythtv/mythweb-htaccess.conf fixed this issue.

---

### Post by severedspirit on 2007-09-29
Yer, just tried that, didnt work :s

However i stopped apache2 and used apache instead and it worked, now just working out what I'm missing

---

### Post by fatbastard spice on 2007-09-30
Check that you haven't got an AllowOverride None option making Apache ignore the mythweb .htaccess file. Any Directory directives for the mythweb folder need AllowOverride All.

---

### Post by severedspirit on 2007-09-30
thanks for your help, found out the problem, I hadn't installed the rewrite function on the apche2 configuration, it all works fine now

---

