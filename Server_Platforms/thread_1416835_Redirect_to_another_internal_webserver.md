---
title: "Redirect to another internal webserver"
date: 2010-02-26
forum: Server Platforms
---

### Post by bolla3 on 2010-02-26
I have two servers on my network One with ubuntu 9.10 server And one with openSUSE 11.2. The ubuntu server is my webserver and runs phpsysinfo and my website. On the openSuse server i have a webbased application and some files that i want people to be able to reach by using mydomain.com wich points to my ubuntu server. Is there any way to do this? I would appreciate it if it was a fairly simple way to do this. 

Sincerely, Bolla3

---

### Post by cdenley on 2010-02-26
Since you said "internal webserver", I'm guessing the user cannot access that server directly, so a redirect wouldn't work since that simply directs the user's browser to browse somewhere else. What you need, if I understand correctly, is for a publicly accessible web server to proxy requests to your "internal webserver".
[http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#examples](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html#examples)
You want the "reverse proxy" configuration. You will need mod_proxy enabled.
```

sudo a2enmod proxy proxy_http
sudo /etc/init.d/apache2 restart

```

---

