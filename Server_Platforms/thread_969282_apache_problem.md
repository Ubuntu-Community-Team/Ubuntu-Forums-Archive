---
title: "apache problem"
date: 2008-11-03
forum: Server Platforms
---

### Post by cajee on 2008-11-03
I hope this is the right place for this topic if not let my know so that this post can be placed somewhere more appropriate.
First the configuration on my server is
Ubuntu 6.3
PHP    5.2.3
MySQL  ?
Moodle 1.8.5
Joomla 1.5.8

This server has been working flawlessly since April of this year as a public web site. Last week my network had an address change. I changed the servers NIC to reflect the new address and since then the web site has not been accessible, even if I change the NIC to the old address. 
The Apache error log has this error
[error] [client 127.0.0.1] file does not exist/htdocs
this error will be generated for each time an attempt is made to access the site. 
Any way that is what I know about this problem, any help is greatly appreciated.

Kevin Gober

---

### Post by puppywhacker on 2008-11-03
I googled a bit on your error message. Google said you are missing a DocumentRoot statement in your apache conf, so apache takes the default /htdocs which doesn't exist on your system. 

For me the default DocumentRoot is set in the file /etc/apache2/sites-enabled/000-default

```
DocumentRoot /var/www/
```

[http://www.webmasterworld.com/apache/3361414.htm](http://www.webmasterworld.com/apache/3361414.htm)

[http://ubuntuforums.org/showthread.php?t=668979](http://ubuntuforums.org/showthread.php?t=668979)


P.S. a good process restart is always healthy :)
/etc/init.d/apache2 restart

---

### Post by cajee on 2008-11-03
Thanks for the post PW. I have been working on this most of the day and have finally had some progress that makes me think this is winnable. 
My default web directory was //var/www
I created a //htdocs directory and copied all web content into the htdocs folder. The result is that now I can access the contents of my htdocs directory using [http://127.0.0.1](http://127.0.0.1). This is a small but very stress reducing development.
I think that the problem must be one of configuration in either my apache2.conf or in my sites-available/sites-enabled file.
What is most confusing is why changing the IP address of my NIC would alter the way Apache reads its config files. I will look into the Documentroot Directive tommorow
Thanks again.
kevin

---

### Post by evrol on 2009-05-12
I am very new to ubuntu. and moodle but I am learning after I install apache server with desktop I install all the applications needed for moodle (apache, Mysql, PHP) then I install moodle but when I try to access the moodle from*** [http://localhost/moodle/admin.php](http://localhost/moodle/admin.php)*** this what I get _**The requested URL /moodle/admin.php was not found on this server **_can someone help me please ?

---

### Post by evaristegalois on 2010-05-21
Make sure you follow

[http://docs.moodle.org/en/Step-by-step_Install_Guide_for_Ubuntu](http://docs.moodle.org/en/Step-by-step_Install_Guide_for_Ubuntu)

I just did and didn't have a problem accessing moodle locally.

---

