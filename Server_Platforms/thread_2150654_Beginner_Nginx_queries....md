---
title: "Beginner Nginx queries..."
date: 2013-06-01
forum: Server Platforms
---

### Post by Ravenshade on 2013-06-01
I'm in the midst of trying (failing) to set up a server. I'm using nginx on ubuntu...12.04 (I think, don't quote me, I just downloaded and installed *cough* on a virtual machine). 

Anyway...

[http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/3/](http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/3/)

I got this far and hit a brick wall. 

```
location / {
    try_files $uri $uri/ =404;
```

Doesn't actually appear to do anything and I'm not sure why. I changed the server name to check that is what I was actually accessing and it seems to work well *cough*, but this line doesn't seem to matter if I have index.html or not it simply refers back to itself. According to the tutorial it should display a built in 404 error. 

Question: Where'd I screw up?

---

### Post by CharlesA on 2013-06-01
What does the full server block look like?

---

### Post by sandyd on 2013-06-01
> **Ravenshade said:**
> I'm in the midst of trying (failing) to set up a server. I'm using nginx on ubuntu...12.04 (I think, don't quote me, I just downloaded and installed *cough* on a virtual machine). 

Anyway...

[http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/3/](http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/3/)

I got this far and hit a brick wall. 

```
location / {
    try_files $uri $uri/ =404;
```

Doesn't actually appear to do anything and I'm not sure why. I changed the server name to check that is what I was actually accessing and it seems to work well *cough*, but this line doesn't seem to matter if I have index.html or not it simply refers back to itself. According to the tutorial it should display a built in 404 error. 

Question: Where'd I screw up?

It should display a error only if there is no file named $uri or $uri/

If you access a non-existent file or directory, then the 404 page will show.

For example, with the configuration below:
```

        location / {
                # First attempt to serve request as file, then
                # as directory, then fall back to index.html
                try_files $uri $uri/ =404;
                # Uncomment to enable naxsi on this location
                # include /etc/nginx/naxsi.rules
        }
        location /normalbehaviour {
                # First attempt to serve request as file, then
                # as directory, then fall back to index.html
                try_files $uri $uri/ /index.html;
                # Uncomment to enable naxsi on this location
                # include /etc/nginx/naxsi.rules
        }

```
Accessing [http://199.15.251.155/](http://199.15.251.155/) will give an index page, because index.html is set as an index and there is a file there called index.html
Accessing [http://199.15.251.155/12345](http://199.15.251.155/12345) will give a 404 page because no file/folder exists
Accessing [http://199.15.251.155/normalbehaviour/randomstuff](http://199.15.251.155/normalbehaviour/randomstuff) will give an index page, because index.html is set as an index and the site redirects back to the root url.

---

### Post by Ravenshade on 2013-06-01
Gonna have to type all of this out... 

```
server {
    listen 80 default_server;
    listen [::]:80 default_server ipv6only=on;

    root /usr/share/nginx/html;
    index index.html index.htm index.php;

    server_name hades;

    location / {
        try_files $uri $uri/ /index.html =404; #Doesn't matter whether I have /index.html or =404 or both or none. 
    }
}
```

The rest of it is all commented out by default. 


I've typed

hades/index.html = produces the default nginx page. 

hades/stupidity.me = produces the default nginx page. (there's no such file). 

Remove /index.html replace with =404; 

hades/stupidity.me = still produces the default nginx page.

---

### Post by CharlesA on 2013-06-01
That is what my site does, but the server block is way more complicated.

```

server {
        listen 80;
        server_name charlesa.net;
        root /webroot/charlesa.net;
        gzip_types application/x-javascript text/css;
        access_log /var/log/nginx/charlesa.net_access.log;
        index index.html index.htm index.php;

        location ~* \.(?:ico|css|js|gif|jpe?g|png)$ {
                expires 30d;
                add_header Pragma public;
                add_header Cache-Control "public";
        }

        location ~ \.php$ {
                fastcgi_split_path_info ^(.+\.php)(/.+)$;
                # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
                # With php5-fpm:
                fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_index index.php;
                include fastcgi_params;
        }
}

```

EDIT: I just noticed I am missing the try statement, but I will have to see what it looks like on the server itself.

---

### Post by Ravenshade on 2013-06-01
S'alright, I'm not entirely sure why mine is not doing as it is supposed to do. I *think* I've followed all the instructions to the letter, I've double checked where I thought I might have slipped up. Though it's not clear which file I should have opened I tested that by changing the server_name variable. 

The only difference from mine and the tutorial is that nginx has inserted a few other things (like listen[::]:80 and I've only included index.php (which apparently doesn't effect the try statement).

---

### Post by Ravenshade on 2013-06-01
My mistake...server_name apparently does nothing. 

Okay...so in site-enabled /etc/nginx/site-enabled/www does nothing apparently. Anyone know a good way to test it. Server_name isn't as reliable as I thought and try_files isn't working at all.

---

### Post by CharlesA on 2013-06-01
What do you have as server_name?

Works fine for me, but you would need to access the server via that server name - charlesa.net, in my case, not the name of the machine.

---

### Post by Ravenshade on 2013-06-01
I'm assuming I set the server name in server block right? 

In which case, I've tried hades, which works, I've changed the name to luna...which doesn't work ._.; 

ifconfig doesn't 'appear' to have a hostname anywhere...and I know I called it hades somewhere.... (by the way, this is only intended to be localhosted at the moment 192.168.1.83 is the local ip address).

basically, if I type "Hades" into the address bar of my host machine, it heads off to the server (as expected). 

If I change server_name to 'Luna' then type luna into the address bar of the host machine... it googles luna instead! *shakes fist*. So doesn't work with any other setting and the try statement doesn't work either. >.>

okay, found hostname (shoots self). Reset server_name to hades...but apparently makes no difference.

---

### Post by Ravenshade on 2013-06-01
O_o... okay...something works now. (not sure wtf I did though). 

Though I had a reaction from /etc/init.d/nginx reload that I hadn't had before. Eg, it actually came up with something before moving on. Which probably means, unless you're 'root' you're not allowed to change things which means I screwed up -_-; (too used to doing things user side not admin side that I now feel uncomfortable staying in root XD) 

I'll mark thread as solved. 

Solution: You need to be root it seems.

---

### Post by CharlesA on 2013-06-01
You can set the server name to whatever as it is what nginx is looking for for that connection. If the hostname:

```
hostname
```

Shows hades, leave it as hades and restart nginx:

```
sudo service nginx restart
```

---

