---
title: "Apache2 Virtual Hosting - HELP!"
date: 2012-05-09
forum: Server Platforms
---

### Post by DannyBlackfire on 2012-05-09
I am trying to set up virtual hosts on Ubuntu Natty with apache2 server and I am having a devil of a time getting it to work.

I have scoured the internet for a working solution to this problem and everything I try fails.

Does anyone know the correct procedure for setting up multiple websites in Natty with apache2?

HELP!

---

### Post by SeijiSensei on 2012-05-09
Use the file /etc/apache2/sites-available/default as a template and define additional sites with unique ServerName and DocumentRoot directives. You may want to create unique log files for each site as well. (You can delete the stanza with "Alias /doc/" and the "<Directory /usr/share/doc>" directives, and the equivalent entries for "ScriptAlias /cgi-bin/" if you don't use the cgi-bin interface to run executables.)  

Store each site in a separate file.  Then run "sudo a2ensite filename" to enable each site.  (All that does is create a symbolic link in /etc/apache2/sites-enabled/ that points to the corresponding file in /sites-available/.)  Restart Apache with "sudo service apache2 restart".

Client machines need to be able to reach each virtual host using a URL that contains the entry in the ServerName field of the corresponding <VirtualHost> definition.  That requires having proper DNS resolution configured or using the clients' "[hosts]("http://en.wikipedia.org/wiki/Hosts_%28file%29")" files to map from server names to IP addresses.

---

### Post by CharlesA on 2012-05-10
Thanks for clearing up the right way to create virtual hosts, Seiji.

---

