---
title: "glassfish + apache, i got it working, sort of..."
date: 2007-05-15
forum: Server Platforms
---

### Post by huggy77 on 2007-05-15
i  saw some posts with people having problems with this - want to post what i did...  

i can currently serve applets without the 8080 - very happy...  want to start severning Jsp too thru apache and gf... will work on that tomorrow...

1:- make sure you have atleast one web ap deployed... do a search and setup the glassfish hello.war... this is very easy to do....

2: read this: [http://blogs.steeplesoft.com/2007/05/04/virtual-hosting-using-apache-and-glassfish/](http://blogs.steeplesoft.com/2007/05/04/virtual-hosting-using-apache-and-glassfish/)  it will tell you how to set up the glassfish server for virtual hosts...
 
2.a: i did make a small change from the blog... under my apache sites-available directory i made an entry that looks like this
```

<VirtualHost *:80>
    ServerName duke
    ProxyPass / http://duke:8080/
    ProxyPassReverse / http://duke:8080/
</VirtualHost>

```

(duke is the character in the hello world ap)

3: i also installed mod_jk with apt (not sure if i need it - but i installed it)

4: added the following lines to the bottom of my apache2.conf file:
LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so

4: becuase i dont want to mess around with dns i added duke to my /etc/hosts file...
```

10.10.10.61    skunkworks
10.10.10.61    skunkworks.aerialphotosofnj.net
127.0.0.1      localhost
10.10.10.61    duke
127.0.0.1      localhost.localdomain


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```


it works nice now... no more 8080 when viewing the hello.war...

now i have to figure out how to serve my jsp pages thru apache....

good luck

---

### Post by huggy77 on 2007-05-15
it is working but i get this error when restartring apache:

apache2: Could not reliably determine the server's fully qualified domain name, using skunkworks.aerialphotosofnj.net for ServerName
[Tue May 15 17:44:54 2007] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
apache2: Could not reliably determine the server's fully qualified domain name, using skunkworks.aerialphotosofnj.net for ServerName
[Tue May 15 17:45:04 2007] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results

any ideas?

---

### Post by huggy77 on 2007-05-16
has anyone gotten glassfish and appache working nicely together under ubuntu?

---

### Post by huggy77 on 2007-05-16
got it working... here is what i did...

check out: Jean-Francois Arcand's Blog
[http://weblogs.java.net/blog/jfarcand/archive/2006/03/running_glassfi_1.html](http://weblogs.java.net/blog/jfarcand/archive/2006/03/running_glassfi_1.html)

1) install mod_jk 

2) edit your httpd.conf, mine looks like this
```

/data/www/sites/jsptest.loc/htdocs
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so
JkWorkersFile /etc/apache2/worker.properties
# Where to put jk logs
JkLogFile /var/log/apache2/mod_jk.log
# Set the jk log level [debug/error/info]
JkLogLevel debug
# Select the log format
JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
# JkOptions indicate to send SSL KEY SIZE,
JkOptions +ForwardKeySize +ForwardURICompat -ForwardDirectories
# JkRequestLogFormat set the request format
JkRequestLogFormat "%w %V %T"
# Send all jsp requests to GlassFish
JkMount /*.jsp worker1
# Send all glassfish-test requests to GlassFish
JkMount /data/www/sites/jsptest.loc/htdocs/* worker1#

```

**JkMount** will be the folder that will hold your jsp docs...  you will have to set this folder up under apache    as a vitual host.

2) create worker.properties in the /etc/apache2 folder... mine looks like this:
```

# Define 1 real worker using ajp13
worker.list=worker1
# Set properties for worker1 (ajp13)
worker.worker1.type=ajp13
worker.worker1.host=localhost.localdomain
worker.worker1.port=8009
worker.worker1.lbfactor=50
worker.worker1.cachesize=10
worker.worker1.cache_timeout=600
worker.worker1.socket_keepalive=1
worker.worker1.socket_timeout=300

```

3) i then dowloaded the tomcat core file from apaches site, unzipped it and moved tomcat-ajp.jar to glassfish/lib 

4) installed via apt libcommons-logging-java &  libcommons-modeler-java , i then moved commons-logging.jar and commons-modeler.jar to glassfish/lib

5) i could not use mr Arcands last step - i had to use the gui... but it was easy... log into glassfish and click the APPLICATION SERVR link, then click JVM SETTINGS, then JVM OPTIONS... now you can add: -Dcom.sun.enterprise.web.connector.enableJK=8009

and it worked...  took me a while but it works beautifully

---

### Post by epsydom12 on 2007-09-17
can you provide info on how you set up your vhost through apache2?
thanks

---

### Post by huggy77 on 2007-09-17
i will post a step by step how to shortly...  I  am actually in the process of rebuilding the server....

---

### Post by epsydom12 on 2007-09-17
I have been following the same threads as most everyone here when i found this thread.  I have been successful in setting up mod_jk so that I can get to my app without the 8080 :) and am looking into vhosting

I may be confused about something here... :confused:

I have: 
[www.mydomain.com](www.mydomain.com) = / (the index dir of apache2)
[www.mydomain.com/myapp](www.mydomain.com/myapp) = my web application 

can i have: 
[www.mydomain.com](www.mydomain.com) = my web application ?

thanks,

---

### Post by huggy77 on 2007-09-24
IT TOOK A WHILE BUT I GOT A SOLUTION...

i ended up fronting TOMCAT with apache using mod_proxy_ajp...  I could not get glassfish working but i have not really tried it using mod_proxy_ajp....  I was trying mod_jk on glassfish and i was having all sorts of issues...

you can see my set up here:
[http://www.blog.market-si.com/2007/09/23/mod_proxy_ajp_and_tomcat.html](http://www.blog.market-si.com/2007/09/23/mod_proxy_ajp_and_tomcat.html)

i hope this helps...  

This is not a condemnation of glassfish - this is more a problem with me not getting the mod_proxy_ajp concept thru my thick skull...

---

