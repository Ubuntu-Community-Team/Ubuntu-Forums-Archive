---
title: "NGINX setup &quot;fastcgi_pass&quot; directive is duplicate"
date: 2012-06-30
forum: Server Platforms
---

### Post by retrodans on 2012-06-30
I am trying to get an NGINX setup working on Ubuntu Server within virtualhost to get a bit of learning going on, but have come across an initial stumbling block.

I have the various packages installed and ready, but notice that when I restart/start NGINX I get the error message returned:
```
$ sudo /etc/init.d/nginx restart
Restarting nginx: nginx: [emerg] "fastcgi_pass" directive is duplicate in /etc/nginx/sites-enabled/default:69
nginx: configuration file /etc/nginx/nginx.conf test failed

```

Does anyone have an idea what the duplicate directive error is?  I looked in my nginx.conf file, and the term cgi is not there at all, so wonder what could be causing this.

Thanks for any pointers,
Dan

---

### Post by retrodans on 2012-06-30
Eventually found the solution.  I was calling that function twice as incommented both lines when enabling php5-fpm.  So just went in and commented out the php5-cgi line.

---

