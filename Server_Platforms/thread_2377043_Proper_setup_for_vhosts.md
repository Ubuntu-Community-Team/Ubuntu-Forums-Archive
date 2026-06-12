---
title: "Proper setup for vhosts?"
date: 2017-11-08
forum: Server Platforms
---

### Post by Adrian_Padilla on 2017-11-08
i am currently running  ubuntu linux 16.04.2 running lamp

i need to see fi my vhosts are properly set up


<VirtualHost *:80>
	ServerAdmin [email]admin@justbuysomestuff.com[/email]
	ServerName [www.justbuysomestuff.com](www.justbuysomestuff.com)
	ServerAlias justbuysomestuff.com
	DocumentRoot /var/www/html/justbuysomestuff/store	
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

the reason i am here is because i remember i had a older server and it had some options and things like 

options + inclused and some other things in the vhost file 

can anyone help me out i thinki am missing some options + includes entries somewhere it just does not look correct 

and also my htaccess file might not be workign properly

Thank you so much

---

### Post by QIII on 2017-11-08
Moved to Server Platforms for a better fit and given a more descriptive title.

Cheers!

---

### Post by Adrian_Padilla on 2017-11-08
Thank you for your help and support

---

