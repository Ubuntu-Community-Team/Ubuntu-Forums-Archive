---
title: "Trouble with Ubuntu 14.04, LEMP server, Joomla, Ajenti, 502 gateways and 404s"
date: 2015-08-31
forum: Server Platforms
---

### Post by jimmy39 on 2015-08-31
Hey guys,

I have recently fired up a Digital Ocean droplet (Ubuntu 14.04) and have successfully installed a lemp server, Ajenti Control Panel and PhpMyAdmin. The server runs php files and runs wordpress fine (with the correct nginx.conf file).

But when I installed Joomla to the same server I can bring up the /administrator url and it shows the login page, however I get a 502 error when i try to login. The frontend just shows a nginx 404 error.

The Ajenti created .conf file looks like this.

```
#AUTOMATICALLY GENERATED - DO NO EDIT!



server {
    listen 80;


    server_name [www.mysite.co.nz]("http://www.mysite.co.nz") mysite.co.nz;

    access_log /var/log/nginx/joomlaproject.access.log;
    error_log /var/log/nginx/joomlaproject.error.log;

    root /srv/mysite.co.nz;
    index index.php index.html index.htm;

location / {
              try_files   $uri $uri/ /index.php?q=$request_uri;
        }



    location ~ [^/]\.php(/|$) {
        try_files $uri =404;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;

        fastcgi_index index.php;
        include fcgi.conf;
        fastcgi_pass unix:/var/run/ajenti-v-php-fcgi-joomlaproject-php-fcgi-0.sock;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;

    }


```


The error log shows [B]
```
2015/08/31 16:10:18 [error] 6380#0: *9 upstream sent invalid status "0 Cannot open file for writing log" while reading response header from upstream, client: 203.97.202.195, server: [www.mysite.co.nz]("http://www.mysite.co.nz"), request: "POST /administrator/index.php HTTP/1.1", upstream: "fastcgi://unix:/var/run/ajenti-v-php-fcgi-joomlaproject-php-fcgi-0.sock:", host: "www.mysite.co.nz", referrer: "http://www.mysite.co.nz/administrator/"

2015/08/31 16:10:23 [error] 6380#0: *9 directory index of "/srv/mysite.co.nz/" is forbidden, client: 203.97.202.195, server: [www.mysite.co.nz]("http://www.mysite.co.nz"), request: "GET / HTTP/1.1", host: "www.mysite.co.nz"

2015/08/31 17:06:52 [error] 6641#0: *3 directory index of "/srv/mysite.co.nz/" is forbidden, client: 85.246.2.67, server: [www.mysite.co.nz]("http://www.mysite.co.nz"), request: "GET / HTTP/1.1", host: "mysite.co.nz", referrer: "http://buttons-for-website.com"

2015/08/31 18:38:26 [error] 6641#0: *47 directory index of "/srv/mysite.co.nz/" is forbidden, client: 66.249.65.23, server: [www.mysite.co.nz]("http://www.mysite.co.nz"), request: "GET / HTTP/1.1", host: "mysite.co.nz"
```

All files in the /srv/mysite.co.nz have the permissions of www-data and www-data. Just to be clear, Wordpress works fine on this server and I can view phpinfo.php from /srv/mysite.co.nz.

Cheers
Hope someone can help!

---

### Post by QIII on 2015-08-31
Please use standard fonts and colors.

Enclose code in code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by SeijiSensei on 2015-09-01
> ```
2015/08/31 17:06:52 [error] 6641#0: *3 directory index of "/srv/mysite.co.nz/" is forbidden, client: 85.246.2.67, server: www.mysite.co.nz, request: "GET / HTTP/1.1", host: "mysite.co.nz", referrer: "http://buttons-for-website.com"
```

I don't use nginx, but I bet your configuration does not allow "indexes" by default.  In apache you would use this
```

<Directory "/path/to/the/webroot">
     Options +Indexes [...]
     [...]
</Directory>

```
This is a security precaution imposed by the server software above and beyond the directory permissions at the filesystem level.  There's probably an equivalent in nginx to the "Indexes" option in apache.

---

