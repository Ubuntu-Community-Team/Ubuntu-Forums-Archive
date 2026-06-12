---
title: "configuring apache 2.4 on 14.04"
date: 2015-03-06
forum: Server Platforms
---

### Post by Drone4four on 2015-03-06
I came up with a two questions as I was configuring my apache web server.

**#1 **Here are the contents of /etc/apache2/apache2.conf as per the linode docs for setting up LAMP:

```
KeepAlive On

...

<IfModule mpm_prefork_module>
StartServers 2
MinSpareServers 6
MaxSpareServers 12
MaxClients 30
MaxRequestsPerChild 3000
</IfModule>

```
See here: [https://www.linode.com/docs/websites/lamp/lamp-server-on-ubuntu-14-04](https://www.linode.com/docs/websites/lamp/lamp-server-on-ubuntu-14-04)
They say that those settings are best for the 1GB ram server.  My droplet is 512MB. Would different settings be suited for less ram as in my case?  I know that I am using documentation for linode even though I am running a digitalocean droplet, but I find that this linode guide is better than the guides on digital ocean for setting of apache 2.4 on 14.04.

**#2. **My homepage is a 403 and not the default apache index.html .  I think it has to do with a line in my /etc/apache2/sites-available/angeles4four.info.conf.  Here are the contents of this file in full:

```
 <VirtualHost *:80> 

	ServerAdmin webmaster@angeles4four.info
	ServerName  www.angeles4four.info
	ServerAlias angeles4four.info
	DocumentRoot /var/www/html/angeles4four.info/public_html/
	ErrorLog /var/www/html/angeles4four.info/logs/error.log 
	CustomLog /var/www/html/angeles4four.info/access.log combined

	<Directory /path/to/public/website/>
		        Require all granted
	</Directory>

</VirtualHost>
```

What does the author of the guide mean with respect to &#8220;<Directory /path/to/public/website/>&#8221;?  I tried /var/www/html/angeles4four.info/public_html/ but that doesn't get rid of the 403.    I think this is the source of my problem but I can't figure out what it should be.  The guide isn't clear.

It's worth noting that when I input ```
$ a2ensite angeles4four.info.conf
``` it gives me: ```
Site angeles4four.info already enabled
```
I tried reloading the apache web server and the default index.html still doesn't show.  It gives me a 403.  See? [http://www.angeles4four.info/](http://www.angeles4four.info/)

I checked to make sure the default apache index.html file is present in /var/www/html (I even copied it into one directory below  /var/www/html/angeles4four.info) and set the permissions for both of those indexes to 0777 with chmod.  No dice.  What else could I try?

---

### Post by Lars Noodén on 2015-03-06
The [Directory](http://httpd.apache.org/docs/2.4/mod/core.html#directory) directive has to point to an existing directory, one where you have your HTML documents.  

```

	<Directory  /var/www/html/angeles4four.info/public_html/>
		        Require all granted
	</Directory>

```

Then you might want the access logs in the same directory as the error logs:

```

	CustomLog /var/www/html/angeles4four.info/**logs**/access.log combined

```

Lastly, the 777 permissions have to be undone.  Files should be 644 or 664 and directories 755 or 775.

---

### Post by Drone4four on 2015-03-06
> **Lars Noodén said:**
> The [Directory](http://httpd.apache.org/docs/2.4/mod/core.html#directory) directive has to point to an existing directory, one where you have your HTML documents.  

```
	<Directory  /var/www/html/angeles4four.info/public_html/>
		        Require all granted
	</Directory>
``` 

As I said, I tried that.  Is there something else that I'm doing wrong?

> Then you might want the access logs in the same directory as the error logs: ```
CustomLog /var/www/html/angeles4four.info/**logs**/access.log combined
``` 
I overlooked that.  Thanks for pointing it out.  

> Lastly, the 777 permissions have to be undone.  Files should be 644 or 664 and directories 755 or 775.
Thanks for pointing this out too. I changed the permissions back from 0777 to 0644.

Now [http://www.angeles4four.info](http://www.angeles4four.info) is no longer a 403, its an empty index page.  So I'm getting somewhere. But [http://www.angeles4four.info/index.html](http://www.angeles4four.info/index.html) is a 404.  After making the changes that I did, I'm wondering why my webserver still doesn't show the default apache index page.  Any ideas?

---

### Post by Lars Noodén on 2015-03-06
You might get some more information by monitoring the error logs

```

tail -f /var/www/html/angeles4four.info/logs/error.log 

```

but more likely you need to allow access to the main directory, for a public site.   403 is forbidden and 404 is not found.  

```

<Directory  /var/www/html/angeles4four.info/public_html/>
  Order allow,deny
  Allow from all
</Directory>

```

Then the file index.html has to exist in /var/www/html/angeles4four.info/public_html/ and have permissions 644 or 664.

---

### Post by Drone4four on 2015-03-06
Thank-you **Nooden** for the help.  

The ```
/var/www/html/angeles4four.info/logs/error.log
``` is empty.

I configured /etc/apache2/sites-available/angeles4four.info.conf to include 
```
Order allow,deny
  Allow from all
```
This configuration file now looks like this in full:
```

<VirtualHost *:80>

        ServerAdmin webmaster@angeles4four.info
        ServerName  www.angeles4four.info
        ServerAlias angeles4four.info
        DocumentRoot /var/www/html/angeles4four.info/public_html/
        ErrorLog /var/www/html/angeles4four.info/logs/error.log
        CustomLog /var/www/html/angeles4four.info/logs/access.log combined

     <Directory /var/www/html/angeles4four.info/public_html/>
        Order allow,deny
        Allow from all
     </Directory>

</VirtualHost>

```
I inputted ```
$ a2ensite angeles4four.info.conf
```, reloaded apache and the default index still doesn't show.  What say you?

Thanks Nooden for taking the time to help me out and thank you for your patience with me taking humble baby steps into the world of LAMP system administration.

---

### Post by Drone4four on 2015-03-06
Solution found. I had a default index.html placed in /var/www/html  .  I had another one in /var/www/html/angeles4four.info/ . I just placed another copy this time in /var/www/html/angeles4four.info/public_html/ and it worked.  Problem solved.  I thought I tried this already, but apparently not.

---

