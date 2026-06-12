---
title: "How to config VirtualHost in Ubuntu Hoary"
date: 2005-05-03
forum: Server Platforms
---

### Post by freeflying on 2005-05-03
I have config the [color=#3366FF]**"/etc/apache2/site-default/default"**[/color]  as follow:
```
  <VirtualHost drupal.3322.org>
      ServerName drupal.3322.org/var/log/apache2
      ServerAdmin rne@sina.com
      ScriptAlias /cgi/ /home/cgi-bin/drupal/
      DocumentRoot /home/www/drupal/
      <Directory /home/www/drupal>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
      </Directory>
      ErrorLog /var/log/apache2/drupal.3322.org-error_log
      CustomLog /var/log/apache2/drupal.3322.org-access_log common
  </VirtualHost>
```

But it still can not work correct .

---

### Post by jdonnell on 2005-05-03
Explain what you mean by 'not working'. 

I'm no apache expert but your config looks wrong to me.
```

      ServerName drupal.3322.org/var/log/apache2
      #this should be the domain name. Why do you have /var/log/apache2 ???

```

---

### Post by freeflying on 2005-05-04
Now I have correct the "[color=#3366FF]ServerName drupal.3322.org/var/log/apache2[/color]" ,but the virtualhost does not work . All request to drupal.3322.org will be redirect to the default document directory.

---

### Post by deuce868 on 2005-05-04
I think his point is why in the world do you have /var/log/apache2 as part of the site name?

Second, did you add an entry in your /etc/hosts for this site name as well?

---

### Post by alastair on 2005-05-04
The Apache site has good docs on all of this. There is little Ubuntu specific :

[http://httpd.apache.org/docs-2.0/](http://httpd.apache.org/docs-2.0/)

---

### Post by crmanski on 2005-05-04
[QUOTE=freeflying]Now I have correct the "[color=#3366FF]ServerName drupal.3322.org/var/log/apache2[/color]" ,but the virtualhost does not work . All request to drupal.3322.org will be redirect to the default document directory.[/QUOTE]
 This is what I do...
<VirtualHost *>
DocumentRoot /your/path/here
ServerName domain.com
ServerAlias [www.domain.com](www.domain.com) domain.com
</VirtualHost>

---

