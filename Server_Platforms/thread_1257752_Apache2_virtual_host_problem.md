---
title: "Apache2 virtual host problem"
date: 2009-09-04
forum: Server Platforms
---

### Post by botfish on 2009-09-04
I have a live server running Ubuntu 7.10 and Apache2. The hostname is example.com

```

~$ hostname
example.com

```

I successfully have multiple virtual hosts running. If the host header is not specified in a request a default page will be displayed. eg [http://255.255.255.255/](http://255.255.255.255/) will display the default page.

But I can not get the example.com virtual host running correctly. A request for example.com will incorrectly display the default page.

In the default page <?php echo $_SERVER['SERVER_NAME']; ?> will correctly display either the ip address or example.com

I can get it working if I change "ServerName example.com" to "ServerName test.example.com", and setup the appropriate DNS CNAME record for test.example.com pointing to example.com

```

:/etc/apache2/sites-available$ cat ./example.com
<VirtualHost *>
	ServerAdmin webmaster@example.com
	ServerName example.com

	DocumentRoot /var/www/example.com/htdocs

	CustomLog /var/log/apache2/vhosts/example.com.access.log combined

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>

	<Directory /var/www/example.com/htdocs>
		Options FollowSymLinks
		DirectoryIndex index.php index.html
		AllowOverride None
		Order Allow,Deny
		Allow from all
	</Directory>
</VirtualHost>

```

---

### Post by botfish on 2009-09-23
To archive this I think I need to used a mixture of ip based and name based virtual hosting.

From the apache2 docs:

> If the main_server has no ServerName at this point, then the hostname of the machine that httpd  is running on is used instead.

Does anyone have experience with this?

Regards

---

### Post by openfly on 2009-09-23
Might want to look into mod_rewrite.

---

### Post by Bachstelze on 2009-09-23
If you define hostname as example.com, it means that the machine hostname is "example" and the domain is "com". That is not what you want. You *must* give your machine a hostname in the example.com domain, that's why it works when you change your ServerHost to test.example.com.

Alo, the Apache doc says that the <VirtualHost> block whose ServerName is the same as the one defined on the global config file must go first:

> If you are adding virtual hosts to an existing web server, you must also create a <VirtualHost> block for the existing host. The ServerName and DocumentRoot included in this virtual host should be the same as the global ServerName and DocumentRoot. List this virtual host first in the configuration file so that it will act as the default host.

From [http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html).

---

### Post by botfish on 2009-10-09
Thanks for your reply Bachstelze.

So should my machine name be something.example.com and I should not have a virtual host with the same name?

---

