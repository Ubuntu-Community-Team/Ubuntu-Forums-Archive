---
title: "HTTP Server Opinions"
date: 2006-07-14
forum: Server Platforms
---

### Post by kaptainlange on 2006-07-14
I was looking to setup a lightweight webserver on my desktop computer to do some minor web requests over home network.

Just curious if anyone had any recommendations on a small, fast, lightweight server.

---

### Post by simonn on 2006-07-14
I use [mini_httpd](http://www.acme.com/software/mini_httpd/).

---

### Post by kaptainlange on 2006-07-14
Have any idea how it stacks up against thttpd?

---

### Post by simonn on 2006-07-14
> **kaptainlange said:**
> Have any idea how it stacks up against thttpd?

I have no statisics, but it can handle the handful of request/minute peak that it gets :).

Seriously, I doubt you would notice the difference between the two on a home network.

---

### Post by az on 2006-07-14
> **kaptainlange said:**
> I was looking to setup a lightweight webserver on my desktop computer to do some minor web requests over home network.

Just curious if anyone had any recommendations on a small, fast, lightweight server.

Apache is pretty modular.  It only takes up about 5 megs of disk space, installed.

:~$ sudo apt-get install apache2
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  apache2-common apache2-mpm-worker apache2-utils libapr0 libpcre3 ssl-cert
Suggested packages:
  apache2-doc lynx www-browser
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-worker apache2-utils libapr0 libpcre3
  ssl-cert
0 upgraded, 7 newly installed, 0 to remove and 128 not upgraded.
Need to get 1430kB of archives.
After unpacking, 4764kB of additional disk space will be used.

---

### Post by va3uxb on 2006-07-14
I second the vote for mini_httpd.  I have it running on my Dapper server, and I have it running on an embeded Linux ARM device.  It is small and quite easy to configure and seems pretty capable.  It can handle ssl, cgi, and virtual hosts.  

-Stephanie

---

### Post by mazirian on 2006-07-14
Usually when the words lightweight and http server are used together, the lighttpd server is mentioned.  Try that.

I do prefer apache, although it's probably just momentum at this point.

---

### Post by bbatsell on 2006-07-14
I couldn't live without lighttpd :)

[http://www.lighttpd.net/](http://www.lighttpd.net/)

---

### Post by kaptainlange on 2006-07-14
> 
Apache is pretty modular. It only takes up about 5 megs of disk space, installed.


I've been running apache on my server for a while.  It serves its purpose well, I just want to keep things simple for my desktop.

Lighttpd looks to be my boy though, seems like it has all the features I'm looking for and small enough resource requirements.

Thanks for your input everyone!

---

