---
title: "New to ubuntu: tomcat5.5: inserting your servlets?"
date: 2008-10-25
forum: Server Platforms
---

### Post by K.I.N.G.U.B.U.N.T.U on 2008-10-25
Hi everybody,

I am new to ubuntu and tomcat5.5. I have started using it in uni, enjoyed it more than windows so converted.

But here is the problem, in uni, "tomcat start" sets up a tomcat directory for me to put all my servlets in.

When I start tomcat on my laptop,
sudo /etc/init.d/tomcat5.5 start
no directory is made? when I go to [http://localhost:8180/](http://localhost:8180/) I get

HTTP Status 404 - /

type Status report

message /

description The requested resource (/) is not available.
Apache Tomcat/5.5

so I know tomcat is running

I have tried to put files into /usr/share/tomcat5.5/webapps but it I don't have permission? I went to the terminal and created /usr/share/tomcat5.5/webapps/ROOT/WEB-INF/classes. This worked but when trying to put files there, it said 

Code:

root@james-laptop:~# !216
mv /Desktop/Assignment1-17/ChatDb.java /usr/share/tomcat5.5/webapps/ROOT/WEB-INF/classes/
mv: cannot stat `/Desktop/Assignment1-17/ChatDb.java': No such file or directory

I have changed TOMCAT5_SECURITY=no in gedit /etc/init.d/tomcat5.5 as one forum told me to but I still cannot add files?

Am I tring to put them in the wrong directory? Is there some special way of inserting your servlets in tomcat5.5 that I don't know of?

If anyone out there has done this, please help

---

