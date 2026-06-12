---
title: "Trouble with AWS Ubuntu and PHPMyAdmin, ISPConfig"
date: 2016-06-12
forum: Server Platforms
---

### Post by bevan2 on 2016-06-12
Hello,
I've created a server on AWS: Ubuntu 14.04 LTS
I followed a 'perfect server' tutorial, and installed ISPConfig
Everything was textbook - until I try and access PHPMyAdmin. All I get is a 404: "the requested URL /phpmyadmin was not found on this server"

Can someone point me to the correct forum, or give me the pointers I need to get this going?

T.I.A. !

Bevan

---

### Post by howefield on 2016-06-12
Thread moved to the "*[I]Server Platforms*[/I]" forum.

---

### Post by bevan2 on 2016-06-12
Thankyou!

---

### Post by darkod on 2016-06-12
How are you trying to access it? Is this the main ispconfig server node, or an additional one?

Don't forget that usually the main ispconfig node has url that includes the port number, like [https://yourserverip:8080](https://yourserverip:8080)

In such case, you would access phpmyadmin with [https://yourserverip:8080/phpmyadmin](https://yourserverip:8080/phpmyadmin)

Also make sure your firewall (if any) allows connections to tcp/8080.

---

### Post by bevan2 on 2016-06-12
Thanks. Yes, it is on 8080 but fails. The link alt text says ~/sites/database_phpmyadmin?id=3 and that goes to /phpmyadmin and gives the 404. There's no phpmyadmin.php file in that directory either...

---

### Post by darkod on 2016-06-12
Can you post the tutorial link?

I have installed ispconfig for a friend and if I remember correctly phpmyadmin works well by default and the address is /phpmyadmin. But lets check the tutorial you followed and what it says, they might have done things differently.

---

### Post by bevan2 on 2016-06-12
OK, Will do. Am away from my pc so don't have the link on my phone. Will post it in about 8 hours time

---

### Post by bevan2 on 2016-06-13
[https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p1](https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p1) is the tutorial i followed

---

### Post by darkod on 2016-06-13
That link is broken. Did you copy it good? Or they changed the location of the page (I doubt that)...

---

### Post by Habitual on 2016-06-13
I'm surprised you get a 404 since port 8080 isn't open by default on an EC Security Group. </hint>
Also, some advice about following a "hardening a server" tutorial. AWS Instances are pretty damn hardened (from the edge anyway) when you deploy them.
You do have to be careful about what you open in the Security Group.

Pre-AWS, I'd followed some hardening tutorials, but they all seem to center on CentOS and that gawd awful cPanel.

---

### Post by bevan2 on 2016-06-13
OK, so I opened 8080 in AWS beforehand but I still can't get phpmyadmin

---

### Post by bevan2 on 2016-06-14
[https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3](https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3)
try this link

---

### Post by Habitual on 2016-06-14
OK. Port 8080 is open to you, and you get a 404 on Ubuntu 14.0.4 in an Amazon AWS instance.
Check 
```
tail -f /var/log/apache2/error.log
``` from the web server while connecting from your desktop and keep an eye on this log
for entries from your IP.

Control+c terminates the tail process.

Alternatively, you could on the AWS host.
```
sudo dpkg-reconfigure phpmyadmin
```
Installing via ```
sudo apt-get install phpmyadmin
``` should have had 
the same net-result.

---

### Post by bevan2 on 2016-06-14
OK, so I followed the reconfiguire bit, see below

OK, so I followed the reconfiguire bit, and got this: 
```
ubuntu@server1:~$ sudo su
root@server1:/home/ubuntu# dpkg-reconfigure phpmyadmin
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
apache2_invoke: Enable configuration phpmyadmin
Action 'configtest' failed.
The Apache error log may have more information.
apache2_reload: Your configuration is broken. Not reloading Apache 2
 * Reloading web server apache2                                                  * 
 * The apache2 configtest failed. Not doing anything.
Output of config test was:
apache2: Syntax error on line 223 of /etc/apache2/apache2.conf: Could  not open configuration file /usr/share/phpmyadmin/apache.conf: No such  file or directory
Action 'configtest' failed.
The Apache error log may have more information.
invoke-rc.d: initscript apache2, action "reload" failed.
root@server1:/home/ubuntu# 
```

Furthermore, when I look in /usr/share/phpmyadmin I get the below: no apache.conf file.
```
root@server1:/usr/share/phpmyadmin# ls
browse_foreigners.php  index.php              server_export.php            tbl_move_copy.php
changelog.php          js                     server_import.php            tbl_operations.php
chk_rel.php            libraries              server_plugins.php           tbl_printview.php
config.sample.inc.php  license.php            server_privileges.php        tbl_relation.php
db_create.php          locale                 server_replication.php       tbl_replace.php
db_datadict.php        navigation.php         server_sql.php               tbl_row_action.php
db_events.php          phpinfo.php            server_status_advisor.php    tbl_select.php
db_export.php          phpmyadmin.css.php     server_status_monitor.php    tbl_sql.php
db_import.php          pmd_display_field.php  server_status.php            tbl_structure.php
db_operations.php      pmd_general.php        server_status_queries.php    tbl_tracking.php
db_printview.php       pmd_pdf.php            server_status_variables.php  tbl_triggers.php
db_qbe.php             pmd_relation_new.php   server_variables.php         tbl_zoom_select.php
db_routines.php        pmd_relation_upd.php   setup                        themes
db_search.php          pmd_save_pos.php       show_config_errors.php       themes.php
db_sql.php             prefs_forms.php        sql.php                      transformation_overview.php
db_structure.php       prefs_manage.php       tbl_addfield.php             transformation_wrapper.php
db_tracking.php        print.css              tbl_change.php               url.php
db_triggers.php        querywindow.php        tbl_chart.php                user_password.php
export.php             schema_edit.php        tbl_create.php               version_check.php
favicon.ico            schema_export.php      tbl_export.php               view_create.php
file_echo.php          server_binlog.php      tbl_get_field.php            view_operations.php
gis_data_editor.php    server_collations.php  tbl_gis_visualization.php    webapp.php
import.php             server_databases.php   tbl_import.php
import_status.php      server_engines.php     tbl_indexes.php

```

---

### Post by Habitual on 2016-06-15
Don't know, off hand.
Not sure this forum is the way to go to "fix the issues", or just easier
to purge and re-install from repo, manually.

---

### Post by Habitual on 2016-06-15
Bookmark this [https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-14-04)
I wouldn't use [https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p6](https://www.howtoforge.com/perfect-server-ubuntu-14.04-apache2-php-mysql-pureftpd-bind-dovecot-ispconfig-3-p6)
to install phpmyadmin.

---

### Post by bevan2 on 2016-06-16
I've fixed it: I removed the line that was added to apace2.conf that  looked for the file apache.conf in /usr/share/phpmyadmin/, and now it  works ok

---

