---
title: "php is not working ?"
date: 2007-02-18
forum: Server Platforms
---

### Post by Mba7eth on 2007-02-18
Hi all , i'm very new to servers stuff. I have just followed [this guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Apache_HTTP_Server") to install apache, php5. Then i added a test.php page in /var/www. tried [http://localhost/test.php](http://localhost/test.php) (as mention in the tut) it shows the save dialog box asking if i want to save test.php or just show it ? 
So please help!!! how to activated ?

---

### Post by Mba7eth on 2007-02-18
please guys any one help ?

---

### Post by jtc on 2007-02-18
> **Mba7eth said:**
> please guys any one help ?
Patience my friend :-P

Run this command, and see if you get any mention of php5?

```
ls /etc/apache2/mods-enabled/
```

---

### Post by Mba7eth on 2007-02-18
Back from a very long adventure ! :) 
Anyhow  this is the output .. 
```
$ls /etc/apache2/mod-enabled
cgi.load userdir.conf userdir.load
```
no signs for a php I guess ?! so how to activate it ?

---

### Post by jtc on 2007-02-18
```
a2enmod php5
```

---

### Post by Mba7eth on 2007-02-19
okey once i got my box i'll try !
Thanks for your help :)

---

### Post by Mba7eth on 2007-02-19
Hmmmm still the same :( i even restarted the apache2 .... but still the same :( 

when ever i type [http://localhost/testphp.php](http://localhost/testphp.php) the same problem as mention is appearing. 

PS: > $ls /etc/ /etc/apache2/mod-enabled
cgi.load userdir.conf userdir.load php5.load php5.conf 
this is what i remember !!!

---

### Post by Mba7eth on 2007-02-20
i accessed it thru w3m from the terminal and worked and tried it again from firefox and it is working ???? REally weired :-k  ?

---

### Post by kernel scurry on 2007-02-25
I'm having the same problem, apache2 is running ok, but trying to open test.php gives me the save file dialog.

mods-enabled gives me:

cgi.load      php4.conf  php5.conf  rewrite.load  ssl.load     userdir.conf
include.load  php4.load  php5.load  ssl.conf      suexec.load  userdir.load

I tried that w3m trick, however it also wants me to save the file. I'm new to this, and not sure what it can be. I just want to be able to test on my desktop. I'm using 6.10 desktop, not server.

Thanks for any help.

---

### Post by jtc on 2007-02-25
You'r trying to load both php4 and php5 at the same time. That might confuse Apache.

---

### Post by kernel scurry on 2007-02-25
I disabled it, now i've only gotten;

cgi.load      php5.conf  rewrite.load  ssl.load     userdir.conf
include.load  php5.load  ssl.conf      suexec.load  userdir.load

Did a force-reload. no change. I've checked the apache conf file and it does have index.php listed there. This is the DirectoryIndex line;

DirectoryIndex index.html index.htm index.shtml index.cgi index.php index.php3 index.pl index.xhtml

I've rebooted, I just dont understand what I missed. I've gone though and looked at several install guides and I just can't figure out what I'm missing. Is there anything in the apache conf file that I should be looking for or should be in there for php to be working?

Ok, I just noticed somthing. In usr/lib/apache2/modules/libphp5.so is not in there, and the php5.load file calls this libphp5.so file... so, I'm thinking that's the problem. However, I'm not sure what I need to do inorder for it to be in there.

Thanks

---

### Post by kernel scurry on 2007-02-25
Got it.

Used this [http://ubuntuforums.org/showthread.php?p=2172553](http://ubuntuforums.org/showthread.php?p=2172553) , after I had already just deleted the apache2 folders...

apt-get remove --purge apache2 apache2-common apache2-mpm-prefork apache2-utils ssl-cert

Then followed the guide to the T. 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Apache_HTTP_Server)

PEBKAC

---

### Post by Liakoni on 2007-02-28
After enabling php5-module and apache2 reload , it's need to empty the cache of the browser !

---

