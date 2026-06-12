---
title: "Security concern about nginx and php5-fpm setup"
date: 2013-10-20
forum: Security
---

### Post by syahzul on 2013-10-20
Hi all,

I want to ask about my server setup using nginx and php5-fpm. I try to mimic suPHP feature using php5-fpm and nginx. Below are my setup:

nginx virtualhost:
```

...

        location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                fastcgi_pass 127.0.0.1:9010;
                fastcgi_index index.php;
                include fastcgi_params;
        }
...

``` 
*note that i'm using port 9010 for this vhost.*

php-fpm pool:
```

[mysampleuser]


user = mysampleuser
group = mysampleuser
listen = 127.0.0.1:9010
```
*this will listen to port 9010.*

using this setup, i don't have any problem with files/folders permissions when sending the file through ftp clients.

the question is, is there any security issues using this method? sorry for asking, i'm just a web designer trying to setup my own vps. 

thank you.

---

