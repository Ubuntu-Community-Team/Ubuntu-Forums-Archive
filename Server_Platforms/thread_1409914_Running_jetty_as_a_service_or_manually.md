---
title: "Running jetty as a service or manually"
date: 2010-02-18
forum: Server Platforms
---

### Post by gacilu on 2010-02-18
Hello guys,

I have a very strange issue. I have a web application that runs fine. 

Whenever I run jetty manually the application runs ok. This is what I do:

sudo java -jar start.jar

The application is located within the webapps directory correctly and the required jar files are within /usr/share/jetty/lib.

But when I run jetty as a service:

sudo service jetty start

The server starts, but the application does not respond. There is no error in the output. This is very strange, isn't it?

Thanks in advance for your ideas,

GA

---

### Post by eirirlar on 2011-02-23
Maybe you're missing some env vars? I modified my jetty script by prepending this:

JAVA_HOME=/home/dev/jdk6
PATH=${JAVA_HOME}/bin:${PATH}
JETTY_HOME=/home/prod/jetty
JETTY_USER=prod

Regards

---

