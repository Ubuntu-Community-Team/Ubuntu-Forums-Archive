---
title: "wordpress won't load"
date: 2010-04-09
forum: Server Platforms
---

### Post by bgrohe on 2010-04-09
I have my own personal web server with xubuntu on it, but after I upgraded to 9.10 my wordpress blog stopped working.:confused: Any Ideas?

---

### Post by cdenley on 2010-04-09
Stopped working how? What error do you get? What URL are you using when attempting to access it?
```

tail /var/log/apache2/error.log
cat /etc/apache2/conf.d/* /etc/apache2/sites-enabled/*

```

---

### Post by ICEB3AR on 2010-04-09
Okay too late, look at cdenley's post.

---

### Post by bgrohe on 2010-04-09
What I mean is that I get I can't connect to server for that one page. I can access all the other pages and when I try to access the page directly. I get the text of the page but without the theme or write placement.

---

### Post by bgrohe on 2010-04-10
I ran those commands in the terminal and they apparently don't exist. Which is partly my fault because I didn't mention that I am using xampp.

---

### Post by cdenley on 2010-04-10
> **bgrohe said:**
> I ran those commands in the terminal and they apparently don't exist. Which is partly my fault because I didn't mention that I am using xampp.

I'm not familiar with how xampp is setup. If you switch to ubuntu software, then I might be more help. Post the URL and/or the html contents of the page which isn't displayed properly.

---

### Post by bgrohe on 2010-04-10
the url is 
grohehosting.homelinux.net/techpod

I keep on getting the server cannot be found? Anyway I hope this helps

---

### Post by cdenley on 2010-04-10
> **bgrohe said:**
> the url is 
grohehosting.homelinux.net/techpod

I keep on getting the server cannot be found? Anyway I hope this helps

That is the URL for your redirection service. The URL for your server is supposed to be, I'm guessing, [http://grohehosting.homeftp.net:8000/techpod](http://grohehosting.homeftp.net:8000/techpod). However, at the IP that domain resolves to, 68.112.240.182, there is no server available. Verify that is the correct IP. Run this on the server:
```

wget -q -O - http://whatismyip.org/ && echo

```

Then verify your web server is listening for connections
```

sudo netstat -tlnp

```

---

### Post by bgrohe on 2010-04-10
Sorry my webserver is on Wifi. And it disconnected. And I did think of that but the rest of the webserver is working. That is why I am confused.

---

### Post by cdenley on 2010-04-10
> **bgrohe said:**
> Sorry my webserver is on Wifi. And it disconnected. And I did think of that but the rest of the webserver is working. That is why I am confused.
I see that URL gives yet another redirection to [http://www.grohehosting.homeftp.net:8000/techpod/](http://www.grohehosting.homeftp.net:8000/techpod/).
```

cdenley@cdenley:~$ echo -e "GET /techpod/ HTTP/1.0\nHost: grohehosting.homeftp.net\n"|nc -w 5 68.112.240.182 8000
HTTP/1.0 301 Moved Permanently
Date: Sat, 10 Apr 2010 21:09:35 GMT
Server: Apache/2.2.11 (Unix) DAV/2 mod_ssl/2.2.11 OpenSSL/0.9.8i PHP/5.2.8 mod_apreq2-20051231/2.6.0 mod_perl/2.0.4 Perl/v5.10.0
X-Powered-By: PHP/5.2.8
X-Pingback: http://www.grohehosting.homeftp.net:8000/techpod/xmlrpc.php
**Location: http://www.grohehosting.homeftp.net:8000/techpod/**
Content-Length: 0
Connection: close
Content-Type: text/html; charset=UTF-8

```

However, there is no DNS record for that domain, which is why you fail to connect to your non-existent server. Either configure the www sub-domain, or stop redirecting to it. I'm guessing that **www.**grohehosting.homeftp.net is configured in wordpress somewhere.

---

### Post by bgrohe on 2010-04-10
Wow, I never noticed that, do you know where that would be configured in wordpress?

---

### Post by cdenley on 2010-04-10
> **bgrohe said:**
> Wow, I never noticed that, do you know where that would be configured in wordpress?

No. I never used it before.

---

