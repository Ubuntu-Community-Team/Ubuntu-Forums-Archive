---
title: "apache2 tomcat6 portforwarding"
date: 2010-09-02
forum: Server Platforms
---

### Post by Thyagaraj on 2010-09-02
I have apache2 and tomcat6 installed on ubuntu 9.10. By default tomcat6 port no is 8080. I want to run tomcat on port 80 but both apache & tomcat should work. For tomcat virtual hosting it should navigate to tomcat webapps and for apache it should direct to var/www.

Plz any one give me step by step guide to achive this
Thank you!

---

### Post by Thyagaraj on 2010-09-05
I have tomcat6 running on the port 80 and for this I following the link [http://rcpeters.blogspot.com/2009/05/installing-apache2-and-tomcat6-on.html](http://rcpeters.blogspot.com/2009/05/installing-apache2-and-tomcat6-on.html) 
I checked its working creating a jsp file under /var/lib/tomcat6/ROOT/.
But the files(index.html ...) under /var/www are not working, its only redirecting to tomcat.
If I comment the following in the file '/etc/apache2/sites-enabled/000-default' then only apache2 is working but not tomcat on port 80
<IfModule mod_jk.c>
          JkMount / worker1
          JkMount /* worker1

Is there any way so that I can run both apache2(/var/www) and tomcat6 on the port 80?.

---

### Post by houndi on 2010-09-05
Intresting. can see forward

---

### Post by Thyagaraj on 2010-09-05
Please any one help me... to keep up some hope on me at the office. Any tips, tricks, tweaks...
Thank you!

---

### Post by _sluimers_ on 2010-09-05
It's possible. In fact, I have a similar problem at the moment as my previous server burned down and now I have to rebuild it, but I basically got it without really knowing what I was doing.
Right now I have tomcat AND apache working, however nothing is getting deployed.

What I remember is that I did it without any mod_jk stuff as that was outdated or something.
[EDIT]Okay, found it[/EDIT]

I did step 2 and 7 at [http://rcpeters.blogspot.com/2009/05/installing-apache2-and-tomcat6-on.html](http://rcpeters.blogspot.com/2009/05/installing-apache2-and-tomcat6-on.html)

I also made a file called ajp.load at /etc/apache2/mods-enabled:

```

LoadModule proxy_module /usr/lib/apache2/modules/mod_proxy.so
LoadModule proxy_balancer_module /usr/lib/apache2/modules/mod_proxy_balancer.so
LoadModule proxy_http_module /usr/lib/apache2/modules/mod_proxy_http.so
LoadModule proxy_ajp_module  /usr/lib/apache2/modules/mod_proxy_ajp.so

```

Then I added this on 000-default:

```

....
        <Proxy *>
		AddDefaultCharset Off
		Order Deny,Allow
		Allow from all
	</Proxy>

        RewriteEngine On
        RewriteCond %{REQUEST_URI} /.*\.(jsp|do)
        RewriteRule ^/(.*) ajp://localhost:8009/$1 [P]
        RewriteCond %{REQUEST_URI} /css/.*
        RewriteRule ^/(.*) ajp://localhost:8009/$1 [P]
        RewriteCond %{REQUEST_URI} /img/.*
        RewriteRule ^/(.*) ajp://localhost:8009/$1 [P]
        RewriteCond %{REQUEST_URI} /j_security_check
        RewriteRule ^/(.*) ajp://localhost:8009/$1 [P]

</VirtualHost>

```

I dunno why I made my css and img folder work on tomcat, but anyway, this shows how I made tomcat work only on certain areas with mainly apache running the rest.

---

### Post by kulshoks2121 on 2010-09-05
this one is working but its a bit old [http://ubuntuforums.org/showthread.php?t=971517]("http://ubuntuforums.org/showthread.php?t=971517") might as well try my tutorial :tongue:

---

### Post by LightningCrash on 2010-09-05
> **Thyagaraj said:**
> I have tomcat6 running on the port 80 and for this I following the link [http://rcpeters.blogspot.com/2009/05/installing-apache2-and-tomcat6-on.html](http://rcpeters.blogspot.com/2009/05/installing-apache2-and-tomcat6-on.html) 
I checked its working creating a jsp file under /var/lib/tomcat6/ROOT/.
But the files(index.html ...) under /var/www are not working, its only redirecting to tomcat.
If I comment the following in the file '/etc/apache2/sites-enabled/000-default' then only apache2 is working but not tomcat on port 80
<IfModule mod_jk.c>
          JkMount / worker1
          JkMount /* worker1

Is there any way so that I can run both apache2(/var/www) and tomcat6 on the port 80?.

Don't redirect / and /*, that will redirect everything!

Try

JkMount /appname worker1
JkMount /appname* worker1

---

### Post by Thyagaraj on 2010-09-07
By Lightingcrash tips and kulshoks tutorial I could able to do this. Thanks a lot!
I have both apache2 and tomcat running on port 80. And the guy last posted in the kulshocks tutorial ignited me.

Here is my /etc/apache2/sites-enabled/000-default configuration

```


<IfModule mod_jk.c>
  JkMount / tomcat6
  JkMount /* tomcat6
  JkUnMount /*.html tomcat6
</IfModule>

                  (or)

<IfModule mod_jk.c>
 JkMount /app tomcat6
 JkMount /*.jsp tomcat6
 JkMount /*.ajp tomcat6
</IfModule>



```




I need your help again in using this tomcat6. Previously I used tomcat5.5 and as far as I know there is only one webapps(I installed under /usr/share/tomcat). But in tomcat6 we have multiple webapps directory and I fell in confusion where to deploy my .war file?.

I need help on how to use tomcat6-admin- "manager webapps" and "host-manager webapps" on the browser.

Thank you all again!

---

