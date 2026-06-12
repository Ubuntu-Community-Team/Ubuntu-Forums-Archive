---
title: "what is needed for standard webhosting server"
date: 2012-07-13
forum: Server Platforms
---

### Post by P3t3r on 2012-07-13
Hi all,

I'm renting a VPS and running Ubuntu 10.04 LTS on it (planning to move to 12.04 soon). My main goal with it is to host several websites on it, as most webhosts do.

I am however getting lost. For every step I need to do for this (like configuring apache for multiple vhosts, configuring the email sending, ...) I can find some tutorials (often contradicting eachother, but in the end it usually works), but all together it consumes a lot of time and energy, more than I feel it should, given that I'm just trying to set up a standard web hosting machine, as all webhosts have.

What is the best way to turn a vanilla Ubuntu server (10.04LTS or 12.04LTS) into a full-fledged webhosting machine, with all common options and abilities enabled? Is there a full tutorial anywhere? Is there a package or script that takes care of this? Should I install some Plesk-like software on the machine and forget about all the rest? Or should I just forget about Ubuntu server and try some other distro instead, given my goals? Some recommendations would be appreciated.

---

### Post by darkod on 2012-07-13
I am not into web hosting but a default apache2 installation just works.

Now, if you want to add some specific, special options later, that might be more or less complicated, depending what you want.

Otherwise, I remember I recently tried simply installing the apache2 package on basic Ubuntu server (only SSH role installed during the installation), and it worked.

If you are doing a new install with websites in mind, you can select the LAMP or Web Server roles during install.

For more specific questions, I guess there will be someone able to help you here.

---

### Post by d4m1r on 2012-07-13
1) Look at guides that talk about a complete LAMP install (linux apache mysql php).

2) Get a managed host. It is basically a VPS service like you have now, but you ask your host to complete any task (support, install stuff, manage updates, etc) and they do it for you. Obviously this comes at a price but is great if you don't have time to install and manage everything yourself.

---

### Post by sandyd on 2012-07-13
You might just want to use CPanel if you have no experience with setting up a webserver, and don't want to spend time configuring it.

Otherwise, a few things of advice,

[LIST]
[*]Its only me, but I find nginx virtual hosts easier to configure. (see below)
[*]Use IredMail for mail
[/LIST]
When you install nginx, it is already configured with a single virtual host. Since I had extra time, and was bored, I created an entire nginx configuration for you.

1. Reload your VPS. This can be done through solusVM, or whaever control panel our host provides.
2. Install the software.
```

sudo apt-get install nginx php5-fpm php-apc php5-curl php5-gd php5-geoip php5-imagick php5-imap php5-mcrypt php5-mhash php5-mysql php5-sqlite php5-suhosin mysql-server
```3. You will be asked to set a password for mysql during the install. Write it down somewhere.
4. Setup the configuration.
Here is a base configuration - just edit in the places that are marked, and dump it in /etc/nginx/sites-enabled. 
```

server {

    #replace <your_ip_here> with your ip address.
    listen   <your_ip_here>:80; ## listen for ipv4; this line is default and implied
    #listen   [::]:80 default ipv6only=on; ## listen for ipv6

    #location of your files, make sure you run (without quotes) "chmod -R www-data:www-data"   on the location
    root /srv;
    index index.html index.htm;

    # The name of your domain (virtual hosts)
    server_name localhost;

    location / {
        # First attempt to serve request as file, then
        # as directory, then fall back to index.html
        try_files $uri $uri/ /index.html /index.php;
        # Uncomment to enable naxsi on this location
        #include /etc/nginx/naxsi.rules;
                #autoindex on;
    }

    # Only for nginx-naxsi : process denied requests
    #location /RequestDenied {
    #    # For example, return an error code
    #    return 418;
    #}

    #error_page 404 /404.html;

    # redirect server error pages to the static page /50x.html
    #
    #error_page 500 502 503 504 /50x.html;
    #location = /50x.html {
    #    root /usr/share/nginx/www;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ \.php$ {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
    
        # With php5-cgi alone:
    #    fastcgi_pass 127.0.0.1:9000;
        # With php5-fpm:
        fastcgi_pass unix:/var/run/php5-fpm.sock;
        fastcgi_index index.php;
        include fastcgi_params;
    }

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    location ~ /\.ht {
        deny all;
    }
}

```

---

