---
title: "Multiple websites at one domain, one of them “This site can’t be reached”"
date: 2020-04-02
forum: Server Platforms
---

### Post by veromi on 2020-04-02
[COLOR=#444444][FONT=&amp][B]Ubuntu Server 18.04 LTS (HVM)
[/B][/FONT][/COLOR][COLOR=#242729][FONT=Arial]Created a server with 3 websites on it. Two websites work fine and one with numbers in the name like 1800flowers.com writes "The connection has timed out"[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I did all the same for all 3 [/FONT][/COLOR]
[HTML]mkdir -p /var/www/test.com/public_html
chown -R $USER:$USER /var/www/test.com/public_html
chmod -R 755 /var/www
nano /var/www/test.com/public_html/index.html
[/HTML]
[COLOR=#242729][FONT=Arial]
created index.html[/FONT][/COLOR]
[HTML]cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/test.com.conf
nano /etc/apache2/sites-available/test.com.conf
[/HTML][COLOR=#242729][FONT=Arial]then I put this info in the .conf file[/FONT][/COLOR]
[HTML]<VirtualHost *:80>
    ServerAdmin admin@test.com
    ServerName test.com
    ServerAlias www.test.com
    DocumentRoot /var/www/test.com/public_html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
[/HTML]
[COLOR=#242729][FONT=Arial]
then[/FONT][/COLOR]
[HTML]a2ensite test.com.conf
service apache2 restart
[/HTML][COLOR=#242729][FONT=Arial]then I have[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]"The connection has timed out"[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Same error if I trying to connect via IP address[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Does it matter if domain has numbers in the name?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I also tried to recreate a new .conf file - didn't help [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Please help to solve the problem.[/FONT][/COLOR]

---

### Post by veromi on 2020-04-03
[COLOR=#141414][FONT=&quot]I figured out myself. I had to add http and https ports to AWS security group[/FONT][/COLOR]

---

