---
title: "nginx php-fpm document_root problem, php can see outside root"
date: 2013-02-17
forum: Server Platforms
---

### Post by bvidinli on 2013-02-17
I have this config:
Ubuntu, nginx, php-fpm; nginx speaks to php-fpm through tcp.

related config part of nginx:

```

server {
        listen   80;
        server_name  *.sample.net;


        access_log  /var/www/sample/logs/access_log;
        error_log  /var/www/sample/logs/error_log;
        access_log /var/log/apache_common_access_log;

        root   /var/www/sample/httpdocs/somedir;
        index  index.html index.htm index.php;        


# redirect all www to non-www
if ($host ~* ^www\.(.*))
{
    set $host_without_www $1;
    rewrite ^/(.*)$ $scheme://$host_without_www/$1 permanent;
}

       
        location / {
			if (-f $document_root/error_page.html ) {
				error_page 400 401 402 403 404 405 406 407 408 409 410 411 412 413 414 415 416 417 495 496 497 500 501 502 503 504 505 506 507 /error_page.html;
			}
        }

        location ~ \.php$ {
                root   /var/www/sample/httpdocs/somedir;
                access_log /var/log/nginx/debug-fpm.log debug_phpfpm;
                include fastcgi_params;
                try_files $uri =404;

                fastcgi_pass   127.0.0.1:9000;
                fastcgi_index  index.php;
                fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;

        }


        location ~ /\.ht {
                deny  all;
        }
}

```


the problem is this:
I place a php file inside /var/www/sample/httpdocs/somedir, 
Although the config has root (document_root) of /var/www/sample/httpdocs/somedir , the php file is able to read contents from upper dirs, such as /var, or even /

I debug the php-fpm, and checked if it receives document_root variables, by doing:

( [http://forum.nginx.org/read.php?3,3651](http://forum.nginx.org/read.php?3,3651) )

put this in fastcgi_params:
```

fastcgi_param DEBUG "uri=$uri request_uri=$request_uri
request_filename=$request_filename query_string=$query_string is_args=
$is_args document_uri=$document_uri document_root=$document_root args=
$args fastcgi_script_name=$fastcgi_script_name";

```

included this in php:
```
echo $_SERVER["DEBUG"];
```

and I saw the output of test.php, as expected:
uri=/test.php request_uri=/test.php request_filename=/var/www/sample/httpdocs/somedir/test.php query_string= is_args= document_uri=/test.php document_root=/var/www/sample/httpdocs/somedir args= fastcgi_script_name=/test.php


This showed me that nginx sets document_root as expected, and that is recieved by php-fpm. 

**However, that document_root has no effect. This is main problem **

Any advice why is this ?

(I put this in security section, move it to server section if needed, or copy/link to server section. both is related.)

---

### Post by cariboo on 2013-02-17
Moved to the server discussion sub-forum, as you will probably get better help there.

---

### Post by sandyd on 2013-02-18
> **bvidinli said:**
> I have this config:
Ubuntu, nginx, php-fpm; nginx speaks to php-fpm through tcp.

related config part of nginx:

```

server {
        listen   80;
        server_name  *.sample.net;


        access_log  /var/www/sample/logs/access_log;
        error_log  /var/www/sample/logs/error_log;
        access_log /var/log/apache_common_access_log;

        root   /var/www/sample/httpdocs/somedir;
        index  index.html index.htm index.php;        


# redirect all www to non-www
if ($host ~* ^www\.(.*))
{
    set $host_without_www $1;
    rewrite ^/(.*)$ $scheme://$host_without_www/$1 permanent;
}

       
        location / {
			if (-f $document_root/error_page.html ) {
				error_page 400 401 402 403 404 405 406 407 408 409 410 411 412 413 414 415 416 417 495 496 497 500 501 502 503 504 505 506 507 /error_page.html;
			}
        }

        location ~ \.php$ {
                root   /var/www/sample/httpdocs/somedir;
                access_log /var/log/nginx/debug-fpm.log debug_phpfpm;
                include fastcgi_params;
                try_files $uri =404;

                fastcgi_pass   127.0.0.1:9000;
                fastcgi_index  index.php;
                fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;

        }


        location ~ /\.ht {
                deny  all;
        }
}

```


the problem is this:
I place a php file inside /var/www/sample/httpdocs/somedir, 
Although the config has root (document_root) of /var/www/sample/httpdocs/somedir , the php file is able to read contents from upper dirs, such as /var, or even /

I debug the php-fpm, and checked if it receives document_root variables, by doing:

( [http://forum.nginx.org/read.php?3,3651](http://forum.nginx.org/read.php?3,3651) )

put this in fastcgi_params:
```

fastcgi_param DEBUG "uri=$uri request_uri=$request_uri
request_filename=$request_filename query_string=$query_string is_args=
$is_args document_uri=$document_uri document_root=$document_root args=
$args fastcgi_script_name=$fastcgi_script_name";

```

included this in php:
```
echo $_SERVER["DEBUG"];
```

and I saw the output of test.php, as expected:
uri=/test.php request_uri=/test.php request_filename=/var/www/sample/httpdocs/somedir/test.php query_string= is_args= document_uri=/test.php document_root=/var/www/sample/httpdocs/somedir args= fastcgi_script_name=/test.php


This showed me that nginx sets document_root as expected, and that is recieved by php-fpm. 

**However, that document_root has no effect. This is main problem **

Any advice why is this ?

(I put this in security section, move it to server section if needed, or copy/link to server section. both is related.)
If you want that vhost to be confined to the directory root, you probably want to take a look at php5-fpm 's chroot function.

---

### Post by bvidinli on 2013-02-18
I thought that chroot is another level of security. 
This should also work without use of chroot. Isn't it ?

normally, document_root setting in nginx & php-fpm should prevent any file accessing upper folders (even without use of chroot). 

What am I missing ?

---

### Post by sandyd on 2013-02-18
> **bvidinli said:**
> I thought that chroot is another level of security. 
This should also work without use of chroot. Isn't it ?

normally, document_root setting in nginx & php-fpm should prevent any file accessing upper folders (even without use of chroot). 

What am I missing ?

Think of it like this

Depending on what user nginx and php5-fpm runs at (by default, www-data), it can access anything that is
[LIST=1]
[*]Owned by www-data
[*]has the passthrough flag in 'other', along with the read flag
[*]Group owned by www-data (depends on perimissions)
[/LIST]

So if you have a default configuration, /srv is owned by www-data, and all your files were in /srv, and had a directory structure similar to

/srv
----/site1
----/site2

Then _any_ vhost can access _any_ files under /srv, even if they have a docroot set to /srv/site1 or whatever.

It is one of the reasons why people do not like Apache2's Suexec. The files all have to be readable by www-data, so one user can technically access another's files (of course, there are ways to stop this using Litespeed and whatnot)

---

### Post by bvidinli on 2013-02-25
is there a way to stop this in nginx + php-fpm ?

Additionally, php files can even see files outside of /srv ; that is real problem. 
when you put system('ls -l /') in php, it lists all files inside /

---

### Post by bvidinli on 2013-03-05
this post moved to a new thread. 
[http://ubuntuforums.org/showthread.php?t=2122405](http://ubuntuforums.org/showthread.php?t=2122405)

---

### Post by ebuildy on 2013-12-03
You can create different PHP-FPM worker pool for each vhost, and configure the PHP here instead of within Nginx configuration.

---

