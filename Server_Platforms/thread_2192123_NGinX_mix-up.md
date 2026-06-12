---
title: "NGinX mix-up"
date: 2013-12-06
forum: Server Platforms
---

### Post by John_Madrid on 2013-12-06
hi All,

Here is what I have:  

A system was currently handed over to me with a huge potential to explore on my own.

We have several active websites in one server (192.168.1.5) which is pointing to another server that manages the http traffic (192.168.1.10)

Per say, websites are as follows:

webone.com listens to port 80
webtwo.com listens to port 80 and proxy is pointed to webone.com:8082
webthree.com listens to port 80 and proxy is pointed to webone.com:8083
webfour.com listens to port 80 and proxy is pointed to webone.com:8084

when i access the webone.com site, it opens the webfour.com page.

I have checked the config files and even recreated a webone.com file from one that works.

Where should i check now, im passed 5 hours trying to look for a reason why it is not working when it was working few days ago without any prior change. well that is since I got in.

Thanks in advanced.

---

### Post by CharlesA on 2013-12-06
How are you doing the redirects?

---

### Post by John_Madrid on 2013-12-09
> **CharlesA said:**
> How are you doing the redirects?

thanks charles, you mean how the commands where written?

---

### Post by CharlesA on 2013-12-09
> **John_Madrid said:**
> thanks charles, you mean how the commands where written?

Sorta. I have a block in my configuration file that is written like this:

```
server {
        listen 127.0.0.1:8080;
        server_name www.charlesa.net;
        return 301 http://charlesa.net$request_uri;
}

```

Don't mind the listening on 127.0.0.1:8080 bit, that's because I'm running Varnish on my web server. :)

---

### Post by sandyd on 2013-12-11
> **John_Madrid said:**
> hi All,

Here is what I have:  

A system was currently handed over to me with a huge potential to explore on my own.

We have several active websites in one server (192.168.1.5) which is pointing to another server that manages the http traffic (192.168.1.10)

Per say, websites are as follows:

webone.com listens to port 80
webtwo.com listens to port 80 and proxy is pointed to webone.com:8082
webthree.com listens to port 80 and proxy is pointed to webone.com:8083
webfour.com listens to port 80 and proxy is pointed to webone.com:8084

when i access the webone.com site, it opens the webfour.com page.

I have checked the config files and even recreated a webone.com file from one that works.

Where should i check now, im passed 5 hours trying to look for a reason why it is not working when it was working few days ago without any prior change. well that is since I got in.

Thanks in advanced.

Can you post the config files in /etc/nginx/sites-enabled/*

Thanks

---

