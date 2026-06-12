---
title: "Web server infected?"
date: 2014-01-16
forum: Security
---

### Post by minerbog on 2014-01-16
I have recently progressed onto a vps for my website. Going through the logs just now I have found the following..
```

208.115.113.87 - - [16/Jan/2014:12:29:40 +0000] "GET /blog HTTP/1.1" 200 14305 "-" "Mozilla/5.0 (compatible; Ezooms/1.0; help@moz.com)"
58.213.141.194 - - [16/Jan/2014:12:45:57 +0000] "GET /vtigercrm/graph.php?current_language=../../../../../../../..//etc/elastix.conf%00&module=Accounts&action HTTP/1.1" 404 38 "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; de; rv:1.9) Gecko/2008052906 Firefox/3.0"
221.14.169.156 - - [16/Jan/2014:12:46:00 +0000] "GET http://wujieliulan.com/mnews.htm HTTP/1.1" 200 38 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1)"
65.55.213.242 - - [16/Jan/2014:12:51:07 +0000] "GET /robots.txt HTTP/1.1" 200 56 "-" "msnbot/2.0b (+http://search.msn.com/msnbot.htm)"
65.55.213.242 - - [16/Jan/2014:12:51:07 +0000] "GET /sitemap.xml.gz HTTP/1.1" 200 38 "-" "msnbot/2.0b (+http://search.msn.com/msnbot.htm)"

```
Now line 2, I know is a common exploit that is tried but people trying to break servers, but it returned a 404 status code so not really bothered about that. Its the line below. A GET request to some random looking website that I have no idea about yet it gets a 200 OK Status response! Has my server been compromised?? Why would it return a 200 if there's no such web site?

I'm running Nginx 1.4.4 by the way.

Regards

Gavin.

---

### Post by Dave_L on 2014-01-16
The web site in the third line exists. I can access it from firefox.

---

### Post by CharlesA on 2014-01-16
It looks like someone trying to do php injection to acceess /etc/elastix.conf. If you have php secured, you should be fine.

Read this:
[https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/](https://nealpoole.com/blog/2011/04/setting-up-php-fastcgi-and-nginx-dont-trust-the-tutorials-check-your-configuration/)

---

### Post by minerbog on 2014-01-17
Thanks CharlesA, PHP is very restriced by the ini file and up to date so it should be fine.

My concern is the line below that. To me someone has hit my server with a GET request for wujieliulan.com/mnews.htm (which does not exsist on my server) and has got a 200 status code back saying its was OK. That REALLY concerns me!!

Regards

Gav.

---

### Post by CharlesA on 2014-01-17
Could you have Nginx set up as a proxy?

[http://serverfault.com/questions/216096/access-logs-show-someone-geting-a-random-ip-why-does-this-return-200](http://serverfault.com/questions/216096/access-logs-show-someone-geting-a-random-ip-why-does-this-return-200)

---

### Post by SeijiSensei on 2014-01-17
My guess is that person received the default index page.  The returned object is just 38 bytes long.  That's longer than the default "It Works!" page (177 bytes), but perhaps you have a different item as /var/www/index.html or index.php.

I see these attempts to proxy connections from time to time.  I wondered about the 200 status code as well until I realized they were getting the default index page in reply.

---

### Post by CharlesA on 2014-01-17
> **SeijiSensei said:**
> 
I see these attempts to proxy connections from time to time.  I wondered about the 200 status code as well until I realized they were getting the default index page in reply.

I sometimes see connections to my web server from random sites that try to use it as a proxy but those return a 400, not 200.

I tried testing this yesterday by doing a manual GET request after connecting to port 80, but that didn't work very well on my main web server. I wonder if that is because I am running Varnish in front of Nginx on my main server.

---

