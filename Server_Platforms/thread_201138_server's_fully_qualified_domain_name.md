---
title: "server's fully qualified domain name"
date: 2006-06-21
forum: Server Platforms
---

### Post by Simian on 2006-06-21
When I try to restart apache I get this message:

```
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
```

What does it mean and what should I do about it?

Thanks.

---

### Post by rbalfour on 2006-06-21
Just add or change the ServerName option in your apache config file. On my Debian/Apache2 system the file I had to modify is /etc/apache2/apache2.conf. I added this line:

    ServerName thugone

and then restarted Apache, which started without the error.

If that doesn’t work, make sure that whatever you defined as the ServerName is specified in your /etc/hosts file:

    127.0.0.1 thugone localhost

---

### Post by Simian on 2006-06-21
Thanks, that helped :)

---

### Post by ben22 on 2008-03-05
Hello,

I had the same problem about the qualified domain name.

Adding ServerName "localhost" to the apache2.conf and restarting apache2 made the problem vanish.

However, I still cannot open localhost to get the message "It works".

I edited the /sites-available/default file and changed the directory - NO SUCCESS:

```

[DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
**	<Directory /var/www/apache2-default>**
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>
```

Removing the # did not help by the way.


Here also the data from the /etc/hosts:

127.0.0.1	localhost
127.0.1.1	ben-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Bottomline: opening [http://localhost](http://localhost) does not show any page.

HELP VERY MUCH APPRECIATED!!


ben

---

### Post by Yarbo on 2008-04-16
Ben, it appears, from looking at your hosts file, that your computers domain name is "ben-desktop" and not localhost.
 
So in your apache2.conf file, change the ServerName line to 
 
ServerName ben-desktop
 
Then you should be able to point your browser to [http://ben-desktop/](http://ben-desktop/) to get the "it works" message.

You might want to restart apache with
 
sudo /etc/init.d/apache2 restart
 
Cheers!

---

