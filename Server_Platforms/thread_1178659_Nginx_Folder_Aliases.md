---
title: "Nginx Folder Aliases"
date: 2009-06-04
forum: Server Platforms
---

### Post by sr243 on 2009-06-04
I'm trying to get phpmyadmin to work with nginx. I want it to show up such that when I access mydomain.com/pma/ it would go to the phpmyadmin page.

Here's my server configuuration:

server {
	listen          80 default;
	access_log      /var/log/nginx/access.log;

	location / {
		autoindex on;		
		index index.html index.htm index.php;
		root  /var/www;
	}

	location /pma {
		root /usr/share/phpmyadmin;
		index index.php;
	}

	# Pass the PHP scripts to FastCGI server

	location ~ ^/pma.+\.php$ {
		root /usr/share/phpmyadmin;
		include /etc/nginx/fastcgi_params;
		fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;	
	}

	location ~ \.php$ {
		root /var/www;
		include /etc/nginx/fastcgi_params;
		fastcgi_param  SCRIPT_FILENAME $document_root$fastcgi_script_name;
	}
}

However, when I try it, it just gives a 404 when I access mydomain.com/pma/

What am I doing wrong? Thanks.

---

### Post by geoff2 on 2009-06-07
> **sr243 said:**
> I'm trying to get phpmyadmin to work with nginx. I want it to show up such that when I access mydomain.com/pma/ it would go to the phpmyadmin page.

Here's my server configuuration:

server {
	listen          80 default;
	access_log      /var/log/nginx/access.log;

	location / {
		autoindex on;		
		index index.html index.htm index.php;
		root  /var/www;
	}

	location /pma {
		root /usr/share/phpmyadmin;
		index index.php;
	}

	# Pass the PHP scripts to FastCGI server

	location ~ ^/pma.+\.php$ {
		root /usr/share/phpmyadmin;
		include /etc/nginx/fastcgi_params;
		fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;	
	}

	location ~ \.php$ {
		root /var/www;
		include /etc/nginx/fastcgi_params;
		fastcgi_param  SCRIPT_FILENAME $document_root$fastcgi_script_name;
	}
}

However, when I try it, it just gives a 404 when I access mydomain.com/pma/

What am I doing wrong? Thanks.
Hey, I had the same problem. It seems that when using the 'location' directive, nginx appends the path given in the URI to the end of the root directory listed within the directory. So, in the above, when you visit [http://example.com/pma/](http://example.com/pma/), nginx is trying to pull the file from /usr/share/phpmyadmin/pma/, which doesn't exist.

I'm sure there are ways around it, but my solution was just to recognize what nginx was doing and adapt. So, here's my relevant location code:

```
location ^~ /phpmyadmin {
   root /usr/share;
   include fastcgi_params;
   ...
}
```

Thus, when I hit [http://server.com/phpmyadmin/](http://server.com/phpmyadmin/), nginx retrieves the file from /usr/share/phpmyadmin/, and all is well.

 - geoff

---

