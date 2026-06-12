---
title: "Ubuntu 14.04 apache 2.4 custom directory 403 forbidden"
date: 2014-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by AndyLaci on 2014-04-23
Hello, I recently moved to 14.04 from 12.04. On the old version I had few sites in /etc/apache2/sites-available folder. Now I moved to new ubuntu and apache writes the 403 error with the same config. Please help, here is the info about my problem.

---- old virtual host file:

<VirtualHost *:80>
	ServerAdmin webmaster@localhost


	DocumentRoot /home/andy/Developer/workspace/php/mysite/public
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
</VirtualHost>

---- my new file with this I am trying now:

<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    DocumentRoot /home/andy/Developer/workspace/php/mysite/public


    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined


    <Directory "/home/andy/Developer/workspace/php/mysite/public">
        Require all granted
        Options Indexes FollowSymLinks MultiViews
    </Directory>


</VirtualHost>

I have the site enabled in sites-enabled, my home folder ownership is set to user:user . Dont know what might be possibly wrong, I also set index.php in public folder to 777 for 100 percent insurance. Is there some restriction, that virtual host can't point to outside /var/www folder? Trying to cope with this for 4 hours and I am desperate, please help

---

### Post by AndyLaci on 2014-04-23
Solved, it was permissions problem. But how can I edit my site data and be able to read them with www-data user. Now it works only when ownership of files is set to www-data:some-group. In that group now are 2 users, www-data and me andy. However I cant edit the files, just www-data. Is there some "secure" and usable solution for this?

---

### Post by AndyLaci on 2014-04-24
So the final conclusion, don't know if its right, but switching ownership for my folder in home directory to user > andy and group > www-data solved the problem, hope this post will help someone, because such a stupid little thing took me a lot of wasted time.

---

