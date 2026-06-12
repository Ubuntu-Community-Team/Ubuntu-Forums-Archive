---
title: "Using Apache 2.2 Ubuntu -"
date: 2008-09-05
forum: Server Platforms
---

### Post by kmeth187 on 2008-09-05
Hello I have a question about running apache 2.2 on ubuntu. Im new to this so sorry if this seems obvious. I have a two part question. First why is the httpd.conf file empty after installation does the apache2.conf file replace that on ubuntu? If so why is that? I thought httpd.conf was the standard configuration file. Secondly does anyone have a link to an explanation about how to edit .conf files for apache. Something simple for beginners. Thank you.

---

### Post by windependence on 2008-09-05
This is actually just an Apache2 thing. The httpd.conf is still there and works, but it is only there for backward compatibility with Apache 1.3 and back.

As you know, in Apache 1.3, there was one single config file that tended to get, well, rather unweildy. With Apache2, the approach is modular. I have to say it took me a while too since I still run quite a few 1.3 sites, but I have kinda grown to like the new model. I'll dig up some articles for you, there is one good one out there that explains it all and of course, the Apache docs are really good too.

As far as editing files I am assuming you were talking about how to use the new format. If you meant editors, most of us use nano or vi.

-Tim

---

### Post by kmeth187 on 2008-09-05
Thanks for the response. Wow that was alot faster than I thoughts! Actually I dont have much experience with apache 1.3 either. I guess I just need some documentation for the over all basics of how apache 2 works. As far as editing I was talking about what the different statements in the apache2.conf file do and how to alter them.

---

### Post by cdenley on 2008-09-05
> **kmeth187 said:**
> Thanks for the response. Wow that was alot faster than I thoughts! Actually I dont have much experience with apache 1.3 either. I guess I just need some documentation for the over all basics of how apache 2 works. As far as editing I was talking about what the different statements in the apache2.conf file do and how to alter them.
I have used this a lot.
[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

---

### Post by kmeth187 on 2008-09-06
> **cdenley said:**
> I have used this a lot.
[http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/)

I took a look at the site before. It seems alot of the direction given applies to a UNIX system or windows. It seems like ubuntu has little differences so sometimes its not much help. One other question I had that I cant seem to find on the site is: How does apache now were to look for your index.html site when it gets a request and how can you change that?

---

### Post by windependence on 2008-09-06
In your apache2.conf file there will be a DocumentRoot directive. This is the directory that Apache looks in for your web files. If you have several virtual hosts configured, each of them will have a section in /etc/apache2/sites-available for this. You can change it there, but it's recommended to keep it somewher under the default /var/www directory.

For more help with configuring Apache2:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

Hope this helps.

-Tim

---

