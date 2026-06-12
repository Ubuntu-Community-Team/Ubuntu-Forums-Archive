---
title: "Apache/Tomcat"
date: 2006-10-26
forum: Server Platforms
---

### Post by subnet_rx on 2006-10-26
I downloaded apache and tomcat5.5 and the libapach2-mod-jk module.  Apache works find when tested, but localhost:8080 comes back with nothing.  I'm assuming I have to start Tomcat manually, but what I don't understand is what the Apache module is for.  Shouldn't it start Tomcat?  If I start Tomcat don't I just get a standalone instance of Tomcat like I would without the module?

---

### Post by wieman01 on 2006-10-26
Tomcat is a Java servlet (JSP) engine/server... I does not run on port 8080 by default as far as I remember (long time ago since I used it). You need to check the configuration files.

Why you need Apache if you need JSP & Java Servlets? Actually you don't. Tomcat can be run as standalone server, however, Apache is faster & still makes sense if the majority of your web-pages is HTML rather than JSP.

---

### Post by subnet_rx on 2006-10-26
yeah, I've worked with Tomcat some on Windows since I'm beginning to learn J2EE.  What I didn't understand is the module or why it's even there.

---

### Post by wieman01 on 2006-10-26
Tomcat takes care of the J2EE bit. Runs your servlets & JSP's (which are essentially servlets as well).

If you are interested... JBoss is an excellent EJB engine. It's open-source, free, fast as lightning, and simply the best engine I know. Just in case you want to embark on "Enterprise Java Beans". Very interesting field.

---

### Post by subnet_rx on 2006-10-26
on Windows, I have tested JBOSS 4.0GA, and I have installed and looked at their portal product.  If I need EJB support, JBoss is definitely my first choice.

---

### Post by jessecollins on 2006-11-05
When I had Tomcat 5.0 running on Ubuntu it was initially setup on port 8180.  [http://localhost:8180]("http://localhost:8180")

But, I just installed Tomcat 5.5, which is again setup on port 8180, and I don't get anything back on port 8180.  Has anyone successfully setup Tomcat 5.5 with Apache2 on Ubuntu?

Thanks. ;)

---

### Post by morganee on 2006-11-17
Regarding Tomcat5.5 and ubuntu 6.10, having startup issues.  Need to dig a little to set JAVA_HOME, CATALINA_BASE and CATALINA_HOME.  Using java 1.4.2, but GNU flavor not Sun's.  Not obvious, but poking around.  Will post again if I get lucky.

Quick acid test with Tomcat is 'netstat -an | grep 8005'.  This detects the server port binding.  8180 should also be there.  

-morganee

---

### Post by adamkane on 2006-11-17
Ubuntu + Tomcat:
[http://doc.gwos.org/index.php/Install_tomcat_5.5](http://doc.gwos.org/index.php/Install_tomcat_5.5)

---

### Post by morganee on 2006-11-17
> **subnet_rx said:**
> yeah, I've worked with Tomcat some on Windows since I'm beginning to learn J2EE.  What I didn't understand is the module or why it's even there.

Apache passes JSP (actually Apache Java Server Protocol -- AJP1.3) requests back to Tomcat for active content.  Although Tomcat can serve HTTP, that is not it's primary purpose.  Apache is much better suited for that, especially if your site is using SSL, authentication, etc.  Read up on mod_jk and mod_jk2 for more on this topic.  

For testing, prototyping, and so on the HTTP service in Tomcat is a great fit.

-HTH

---

### Post by Bagnoli on 2007-11-02
Although new to Linux, I've been doing quite a bit of investigation and have an answer to this problem.

The Apache2 install that I got through apt-get install Apache2 does not have the mod_jk module available as noted earlier in this thread (or another that I was using to try and find my answer) so I decided to address the issue myself.

I downloaded the mod_jk-1.2.25-httpd-2.0.59.so file from [http://tomcat.apache.org/download-connectors.cgi](http://tomcat.apache.org/download-connectors.cgi) and copied that to /usr/lib/apache2/modules/.

I then created a mod_jk.conf and mod_jk.load files in /etc/apache2/mods-available/

mod_jk.conf looked something like this:

<IfModule mod_jk.c>

JkWorkersFile "/etc/apache2/mod_jk/conf/workers.properties"
JkLogFile "/etc/apache2/mod_jk/logs/mod_jk.log"

JkLogLevel info

JkMount /url_path_example worker1
JkMount /url_path_example/* worker1

</IfModule>

and mod_jk.load:

LoadModule jk_module /usr/lib/apache2/modules/mod_jk-1.2.25-httpd-2.0.59.so


Then I can use the a2enmod command to enable it.

---

### Post by gtducati on 2007-11-09
You can install the apache tomcat connector with the following command:

sudo apt-get install libapache2-mod-jk

Always be sure to use :

apt-cache search "search-string"

to find what you're looking for :)  In this case if you type

apt-cache search connector

 the mod-jk package shows up in the query.

---

### Post by dcostelloe on 2007-12-01
This link provides and easy install for Tomcat 6.0 on Ubuntu

:popcorn:

[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/]("http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/")

---

