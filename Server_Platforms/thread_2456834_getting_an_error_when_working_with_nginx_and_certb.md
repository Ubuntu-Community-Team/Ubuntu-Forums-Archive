---
title: "getting an error when working with nginx and certbot"
date: 2021-01-20
forum: Server Platforms
---

### Post by espressobeanmachine on 2021-01-20
I want to get a Let's Encrypt SSL certificate but I am getting an error in my syntax.

**OS:** Ubuntu 20.04
**Webserver:** NGiNX 1.18

web configuration:


```
server {
    listen                  443;# ssl http2;
    listen                  [::]:443;# ssl http2;
    server_name             nextcloud.domain.com;
    root                    /var/www/nextcloud.domain.com;


    # SSL
    #;#ssl_certificate         /etc/letsencrypt/live/nextcloud.domain.com/fullchain.pem;
    #;#ssl_certificate_key     /etc/letsencrypt/live/nextcloud.domain.com/privkey.pem;
    #;#ssl_trusted_certificate /etc/letsencrypt/live/nextcloud.domain.com/chain.pem;


    # security
    include                 nginxconfig.io/security.conf;


    # logging
    access_log              /var/log/nginx/nextcloud.domain.com.access.log;
    error_log               /var/log/nginx/nextcloud.domain.com.error.log warn;


    # index.php fallback
    location ~ ^/api/ {
        try_files $uri $uri/ /index.php?$query_string;
    }


    # reverse proxy
    location / {
        proxy_pass http://192.168.7.204;
        include    nginxconfig.io/proxy.conf;
    }


}


# HTTP redirect
server {
    listen      80;
    listen      [::]:80;
    server_name nextcloud.domain.com;
    include     nginxconfig.io/letsencrypt.conf;


    location / {
        return 301 https://nextcloud.domain.com$request_uri;
    }
}
```

I ran the command to comment out the SSL directives:

```
sed -i -r 's/(listen .*443)/\1;#/g; s/(ssl_(certificate|certificate_key|trusted_certificate) )/#;#\1/g' /etc/nginx/conf.d/nextcloud.domain.com.conf

```
but running ***nginx -t*** i get the following error:

```
root@nginx:/etc/nginx/conf.d# nginx -t
nginx: [emerg] no "ssl_certificate" is defined for the "listen ... ssl" directive in /etc/nginx/conf.d/nextcloud.domain.com.conf:1
nginx: configuration file /etc/nginx/nginx.conf test failed
```

What am I doing wrong?

---

### Post by CharlesA on 2021-01-20
Why are you commenting out the SSL blocks? Just testing?

I don't think the listen blocks like comments, so remove the ssl reference and see if the config passes or not.

---

### Post by espressobeanmachine on 2021-01-20
> **CharlesA said:**
> Why are you commenting out the SSL blocks? Just testing?

I don't think the listen blocks like comments, so remove the ssl reference and see if the config passes or not.
I am commenting it out because it will look for an SSL cert that does not exist.

---

### Post by CharlesA on 2021-01-20
Have you been able to get certbot working? If so, where is it placing the certificates?

---

### Post by espressobeanmachine on 2021-01-20
> **CharlesA said:**
> Have you been able to get certbot working? If so, where is it placing the certificates?
I cannot get it to work if NGiNX is throwing errors and not working. I need to resolve this issue with NGiNX and then be able to run certbot.

---

### Post by LHammonds on 2021-01-20
You are trying to make it run on port 443 without SSL?

Why not configure it on port 80 without SSL to get it running so you can run certbot which "should" add the 443 port and links to the certs?  I am assuming here since I do not use NGINX.

I would also remove the in-line comments you have on the listen lines and have them as separate comment-only lines.  I did a quick search and have yet to find any working examples with in-line comments on the listen line.

You also need to make sure your firewall (both software and hardware firewalls) allow port 80 and 443 to pass thru.

LHammonds

---

### Post by CharlesA on 2021-01-20
> **espressobeanmachine said:**
> I cannot get it to work if NGiNX is throwing errors and not working. I need to resolve this issue with NGiNX and then be able to run certbot.

Try this nginx config so you can get certbot to issue you a certificate:

```

# Listen on HTTP
server {
        listen 80;
        server_name example.com;
        charset utf-8; # Character Set set to utf-8
        access_log /var/log/nginx/example.com_access.log; # Access Log
        error_log /var/log/nginx/example.com_error.log warn; # Error Log
        root /var/www/html/example.com; # Web Root Directory
        index index.html; # Look for index.html

        location / {
                try_files $uri $uri/ /index.html =404;
                limit_except GET HEAD POST { deny all; }
        }

}

```

---

### Post by espressobeanmachine on 2021-01-20
> **CharlesA said:**
> Try this nginx config so you can get certbot to issue you a certificate:

```

# Listen on HTTP
server {
        listen 80;
        server_name example.com;
        charset utf-8; # Character Set set to utf-8
        access_log /var/log/nginx/example.com_access.log; # Access Log
        error_log /var/log/nginx/example.com_error.log warn; # Error Log
        root /var/www/html/example.com; # Web Root Directory
        index index.html; # Look for index.html

        location / {
                try_files $uri $uri/ /index.html =404;
                limit_except GET HEAD POST { deny all; }
        }

}

```

got it. seems weird that nginxconfig.io advised otherwise, i will open a ticket them. thanks.

---

