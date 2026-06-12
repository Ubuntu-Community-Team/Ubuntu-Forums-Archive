---
title: "apache2 on LiveCD don't work properly"
date: 2007-11-18
forum: Server Platforms
---

### Post by FAo10rK on 2007-11-18
I customize a liveCD and I want to store a website in the /var/www.
But when I just install apache2, I can't see long pages. I explain :

I test this with Kubuntu, Ubuntu and Xubuntu, and the same things appear.

I boot with the CD, I install apache2 (sudo apt-get install apache2) and I see the apache2-default directory in the page [http://localhost](http://localhost).
And when I go in the directory (with my web-browser) I can the the famous message "It works"; this index.html contains .
```
<html><body><h1>It works!</h1></body></html>
```

When I copy it to /var/www, the same message appear.
But if I edit this page and add some characters like this :
```
<html><body><h1>It works!</h1>
qsdqsdqsd
qsdsqdqsdf
qsdfsqdfqsdf
qsdfqsdfqsdf
qsdfqsdfqsdf
sqdfqsdfqsdf
qsdfqsdfqsdf
qsdfqsdfqsdfqsdf
qsdfqsdfqsdfqsd
qsdfqsdf
qsdfqsdfqsdf
dqfqsdfqsdf
qsdfqsdfqsdf
qsdfqsdfqsdfqsdf
qsdfqsdfqsdfqsdf
qsdfqsdfqsdf
qsdfqsdfqsdf
</body></html>
```

Tha page don't show the good texte and show me :
```
An error occurred while loading http://localhost/:
Connection to host localhost is broken.

```

BUT, if I delete some 10 lines, the same page show :
```

It works!
 qsdqsdqsd qsdsqdqsdf qsdfsqdfqsdf qsdfqsdfqsdf qsdfqsdfqsdf sqdfqsdfqsdf qsdfqsdfqsdf qsdfqsdfqsdfqsdf qsdfqsdfqsdfqsd 

```

How can you explain it ?

This test is just done to show that I can't put a long html page (or a complete web-site in html) in my local /var/www on a liveCD.

Thanks a lot.

Should I modify anothers parameters in apache2 ?
The /etc/hosts contains :
```
127.0.0.1 localhost
127.0.1.1 ubuntu

```

The /etc/apache2/apache2.conf contains :
```

ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile /var/run/apache2.pid
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User www-data
Group www-data

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>

DefaultType text/plain
HostnameLookups Off
ErrorLog /var/log/apache2/error.log
LogLevel warn

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf

LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

ServerTokens Full

ServerSignature On
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/

```

Can you help me, please ?

---

### Post by FAo10rK on 2007-11-20
I can add some details :

When I try to show some pictures in PNG or in GIF, it doesn't work.

For example, if I want to see the pictures present in /var/www/apache2-default, I can't.
Firefox point to [file://localhost/apache2-default/apache_pb22.png](file://localhost/apache2-default/apache_pb22.png)
And in my Firefox window, I just can see this :
"http://localhost/apache2-default/apache_pb22.png"
That's all, any picture.

But, if I try to visit some sites, I can see every PNG or GIF.
It's just in localhost.

Another idea :
I can change the file index.html in index.php with module php5 activated.
And I insert 
```

<?
echo '

**html code**
'
?>

```

And I can see the entire page (like HTML), but any pictures in PNG or GIF in localhost.
If I install this liveCD, the website in html is entirely shown correctly, with PNG and GIF.

Can you help me ? I really need to have a website in my custom liveCD. 

For information, it also happens in a live CD Ubuntu sent by shipit.ubuntu
Someone else has see it : 
[http://ubuntuforums.org/showthread.php?t=245492](http://ubuntuforums.org/showthread.php?t=245492)
[http://ubuntuforums.org/showthread.php?t=555804](http://ubuntuforums.org/showthread.php?t=555804)

Thanks.

---

### Post by FAo10rK on 2007-11-25
The answer of this problem is here :
[https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393](https://bugs.launchpad.net/ubuntu/+source/apache2/+bug/95393)

You just have to add this line in /etc/apache2/apache2.conf :
EnableSendfile Off

And it works !

Thanks a lot, bapoumba !

---

