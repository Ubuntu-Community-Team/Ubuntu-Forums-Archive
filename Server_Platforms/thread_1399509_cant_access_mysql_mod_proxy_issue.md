---
title: "cant access mysql mod_proxy issue"
date: 2010-02-05
forum: Server Platforms
---

### Post by 007casper on 2010-02-05
I set up mod_proxy in order to get rid of :8080 

now I cant access phpmyadmin through the browser. 

what is the quickest way to turn off mod_proxy and access phpmyadmin?  I would like to optimize the tables and back up the sql file.  I just need to turn it on for a bit, and then enable mod_proxy again.

Right now, if I got to localhost/phpmyadmin, it redirects to the main application.

I have used a2enmod, and added
sudo a2enmod proxy
sudo a2enmod proxy_http
sudo a2enmod proxy_ajp

over at /etc/apache2/mods-available, /etc/apache2/sites-enabled then stopped, and started tomcat, apache 

then added these lines at the end of /etc/apache2/sites-enabled/000-default, when I enabled mod_proxy 
```

	ProxyRequests Off
	<Proxy *>
	Order deny,allow
	Allow from all
	</Proxy>

	ProxyPass / ajp://localhost:8009/
	ProxyPassReverse / ajp://localhost:8009/
```

any ideas?

Thank you

---

### Post by 007casper on 2010-02-06
> ProxyPass /mysql !

is that proper?  would it work?  I just dont want to create a chaos over here

---

### Post by 007casper on 2010-02-06
I got it working.  I just temporarily took out the 
> 
	ProxyRequests Off
	<Proxy *>
	Order deny,allow
	Allow from all
	</Proxy>

	ProxyPass / ajp://localhost:8009/
	ProxyPassReverse / ajp://localhost:8009/

and it worked.  However, I still would like to figure out how to bypass certain applications.  Please, let me know.  Thank you.

---

