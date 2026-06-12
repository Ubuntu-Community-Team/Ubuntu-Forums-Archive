---
title: "Nginx certbot ssl issue"
date: 2018-05-18
forum: Server Platforms
---

### Post by joe297 on 2018-05-18
Good evening,

I have just spun up a new Ubuntu 16.04 VM with wordpress installed on it.

I was trying to add an ssl cert to my newly created site. I was following the guide provided by by VPS provider here. [https://www.vultr.com/docs/install-lets-encrypt-ssl-on-one-click-wordpress-app](https://www.vultr.com/docs/install-lets-encrypt-ssl-on-one-click-wordpress-app)

I followed the instructions to the letter. However at this stage:

```
certbot --nginx --redirect
```

I get the following error halfway through the configuration.

```
Deploying Certificate to VirtualHost /etc/nginx/conf.d/wordpress_https.conf
nginx: [error] invalid PID number "" in "/var/run/nginx.pid"
```

I figured I stopped the nginx service at the start so surely it wouldn't be running? 

I then ran the following and could see there was multiple processes running for it?

```
netstat -tulpn |grep 80


nginx     1244  1228  0 20:05 ?        00:00:00 php-fpm: pool www
nginx     1245  1228  0 20:05 ?        00:00:01 php-fpm: pool www
root      2151     1  0 20:06 ?        00:00:00 nginx: master process nginx -c /etc/nginx/nginx.conf
nginx     2787  2151  0 20:13 ?        00:00:00 nginx: worker process
nginx     2993  1228  0 20:22 ?        00:00:00 php-fpm: pool www
root      3198  2940  0 20:38 pts/0    00:00:00 grep --color=auto nginx

```

I figured I'd kill the process using the below and try again.

```
kill -9 2151
kill -9 2787
```

I get the exact same. I've checked and my website is not using a ssl cert at the moment. I'm very new to Linux so hopefully I have posted enough information for someone to be able to advise me on what I am doing wrong or where I can look for further information. Some log files maybe or something that might prove helpful.

Kind regards, Joe.

---

### Post by TheFu on 2018-05-18
Sorry, can't help with cert deployment for php webapps, but you shouldn't kill nginx with a -9 signal unless the 3 other methods to stop it cleanly fail ...which I've never seen.

To start and stop well-known services on 16.04, you should be using **systemctl**   or if you can't remember that, "service", but service is deprecated.

I use *Let's Encrypt* service, but with Apache, not nginx. Last time I looked, the nginx facilities weren't automated, but it has been months, so perhaps they are now?  For the first year, the apache cert stuff worked well, then it broke.  I've had to switch to manually installing the certs since last Sept. It is a pain, but about the same as we did in the old days, just every 3 months instead of every 1, 3, 5 yrs like we had to with paid certs.

---

### Post by darkod on 2018-05-19
Did you try simply adding the cert path in the website .conf file? I guess that certbot command should do it but sometimes too much automatization actually hurts. Adding a cert path in a website .conf file is rather simple.

Try that, restart nginx and see if it worked.

---

### Post by joe297 on 2018-05-22
in my wordpress.https.conf file it has the below where xx.com is my domain name

```

server {
    listen 443 ssl deafult_server;
    server_name xx xx.com;
    ssl_certificate /etc/letsencrypt/live/xx.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/xx.com/privkey.pem;
```

I'm totally lost :(

---

### Post by TheFu on 2018-05-22
The way that Let's Encrypt works is non-trivial.  certbot is a CLI tool that interfaces with the Let's Encrypt server, modifies your website so the certbot can respond to the LE server requests, proving that you are indeed in control of the domain for which you are requesting a cert.  Once that is proven, it exchanges some data that is needed to make a non-trivial cert, then signs it with the LE CA, transfers the public and private certs back to you.  Then the certbot should place them into the correct location and modify the web config file for the specific domain, and bring  the web server back up to answer normal web traffic.   That's the general idea for certbot. Don't take it as 100% accurate.

 Clear as mud?

Because it is non-trivial to do this in an automatic way, things often fail.  Some failures that I've seen were DNS issues, not having port 80/tcp open, things like that.  The lets encrypt errors aren't really all that useful IME.  With the error you have, I'd just guess that the cert stuff all got through fine, just modifying and restarting the webserver (nginx) failed.  Also, I thought that apache was assumed and that nginx needed an extra option, but maybe they have the automation figure out which web server is being used at this point?  IDK.

---

