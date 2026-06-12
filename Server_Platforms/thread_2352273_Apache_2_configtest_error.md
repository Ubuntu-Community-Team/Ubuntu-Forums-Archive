---
title: "Apache 2 configtest error"
date: 2017-02-11
forum: Server Platforms
---

### Post by Pandee on 2017-02-11
So I am trying to restart apache2 when i get these errors (I wrote down these lines as best as i could)

 
[TABLE="width: 90%, align: center"]
[TR]
[/TR]
[TR]
[TD="class: code"] * Restarting web server apache2                                                                     [fail] 
 * The apache2 configtest failed. 
Output of config test was: 
apache2: Syntax error on line 216 of /etc/apache2/apache2.conf: Syntax  error on line 5 of /etc/apache2/conf-enabled/zz010_psa_httpd.conf:  Syntax error on line 58 of /etc/apache2/plesk.conf.d/server.conf: Could  not open configuration file  /etc/apache2/plesk.conf.d/ip_default/grayles.net.conf: No such file or  directory 
Action 'configtest' failed.[/TD]
[/TR]
[/TABLE]
 
 
line 216 of apache2.conf is : 
 
IncludeOptional conf-enabled/*.conf 
 
line 5 of zz101 is : 
 
Include '/etc/apache2/plesk.conf.d/server.conf' 
 
line 58 server.conf 
 
IncludeOptional "/etc/apache2/plesk.conf.d/ip_default/*.conf"

Google Didn't really help.

Thanks ahead!

---

### Post by SeijiSensei on 2017-02-11
I've never used Plesk, but obviously the file /etc/apache2/plesk.conf.d/ip_default/grayles.net.conf does not exist on your system or is not in that location.

---

### Post by Pandee on 2017-02-11
The strange thing is, that it is there..

---

