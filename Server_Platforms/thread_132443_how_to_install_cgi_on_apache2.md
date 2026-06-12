---
title: "how to install cgi on apache2"
date: 2006-02-18
forum: Server Platforms
---

### Post by kasemodz on 2006-02-18
Well I'm trying to install cgi-proxy on apache2.  I installed the cgi in the default folder and I even put a test file which works fine. However, when I try to access the cgi file, there is a blank screen. I'm trying to follow this guide. [http://httpd.apache.org/docs/1.3/howto/cgi.html#dynamiccontentwithcgi]("http://httpd.apache.org/docs/1.3/howto/cgi.html#dynamiccontentwithcgi")
It is a little confusing, i did put this in the apache2 config.
> AddHandler cgi-script cgi pl
I even added > <Directory /usr/lib/cgi-bin>
                Options +ExecCGI
</Directory>
and it still did the same thing. What am I doing wrong. I'm trying to install this. Here is the main page of the software. [http://www.jmarshall.com/tools/cgiproxy/]("http://www.jmarshall.com/tools/cgiproxy/")

---

