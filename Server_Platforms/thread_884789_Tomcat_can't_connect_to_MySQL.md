---
title: "Tomcat can't connect to MySQL"
date: 2008-08-09
forum: Server Platforms
---

### Post by ggggqqqqihc on 2008-08-09
Mine is Ubuntu 8.10, Tomcat5.5 and MySQL5.0. I found if I start tomcat with /etc/init.d/tomcat5.5 start, it cannot connect to MySQL database and throws an exception "Communications link failure". But if I use /usr/share/tomcat5.5/bin/startup.sh, tomcat works well. I want to make init.d/tomcat5.5 support MySQL but I don't know how to do. Can anyone give me a hand? Thanks.

---

### Post by cariboo on 2008-08-09
To do any thing with mysql and a web server you're going to have to install php. Check out this link:

[http://wiki.apache.org/tomcat/UsingPhp](http://wiki.apache.org/tomcat/UsingPhp)

Jim

---

### Post by tinny on 2008-08-09
> **cariboo907 said:**
> To do any thing with mysql and a web server you're going to have to install php. Check out this link:

[http://wiki.apache.org/tomcat/UsingPhp](http://wiki.apache.org/tomcat/UsingPhp)

Jim

Tomcat is a [servlet container]("http://en.wikipedia.org/wiki/Apache_Tomcat").

What are you trying to do? Are you trying to run a Java web application? If you are trying to run PHP or static web pages you are better off with [Apache HTTP server]("http://en.wikipedia.org/wiki/Apache_HTTP_Server").

You can run standard type web pages in Tomcat but it is not considered to be the right way if doing things.

---

### Post by azhar_mz on 2008-08-09
my name is azhar i am new to ubuntu but i really like's it. the problem with my office pc is i cannot do mp2 from datastream. how ? is it possible. system mysql 6 and mp2 work orders... pls help  :)

---

