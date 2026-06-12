---
title: "which soft to use to precompile php scripts ?"
date: 2009-03-13
forum: Server Platforms
---

### Post by fabianus on 2009-03-13
Hello all !

I would like to precompile a php website in order to make it faster. 

I would appreciate a lot if you could give me some hints on how to get this done!

Regards, 
Fabianus

PS Carful, I'm a greenhorn on ubuntu/linux ...

---

### Post by hyper_ch on 2009-03-13
zend

---

### Post by fabianus on 2009-03-13
Hi hyper_ch,

thanks for the brief, but very helpful hint. 

Could you be so kind and give me some additional suggestion? I am looking for some good explenation on how to install zend community server on ubuntu 8.10. There are some posts out there, but none seemd relyable to me as e beginner. I do not need pages and pages of instruction, just be sure that the instructions I get are right. If you could give me some advice ...

Thanks in advance, 
Fabianus

---

### Post by hyper_ch on 2009-03-13
no clue, never done it.

---

### Post by fabianus on 2009-03-13
man, you did 11138 postes, you are supposed to know !

:-) :-)

no serious, thanks for your help. 

See you, 
Fabian

---

### Post by cariboo on 2009-03-14
[This]("http://www.yinfor.com/blog/archives/2007/04/install_zend_optimizer_328_on.html") is for an older version, but there shouldn't be any differences, except for maybe a new version of Zend.

Jim

---

### Post by fabianus on 2009-03-14
Hi Jim, 

thanks for the link. I followed these instructions : 

[http://www.pyrosoft.co.uk/blog/2008/09/02/installing-zend-framework-on-ubuntu-hardy/](http://www.pyrosoft.co.uk/blog/2008/09/02/installing-zend-framework-on-ubuntu-hardy/)

telling me to simply do 
sudo apt-get install zend-framework

but now, I do not know how to precompile the php website. I suppose that it is not done automatically ... 

If you have any idea, would be very helpfull !

Regards, 
Fabainus

---

### Post by fabianus on 2009-03-14
Here I am again. 

In fact, after some reading I think that what I need is FastCGI. Do you agree ?
Is there any simple tutorial on how to install and enable fastcgi with php5 on apache2 ? (ubuntu 8.10 defautl installation). 


Thanks a lot for any help !

Regards, 
Fabianus

---

### Post by fabianus on 2009-03-14
Hello all !

So here is what I did : 

I installed fastcgi module on apache with this : 

sudo apt-get install libapache2-mod-fastcgi 

now I want to activat it and I wrote this in my apache config file : 

```
<VirtualHost *:80>
	ServerAdmin webmaster@fabianus.com
	ServerName fabianus.com
        ServerAlias store.fabianus.com
	DocumentRoot /home/fabianus/store/www/
	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/

	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/fabianus/store/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None

		AddHandler php5-fastcgi .php
		Action php5-fastcgi /cgi-bin/php.cgi


		Order allow,deny
		allow from all
	</Directory>

	
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

	

</VirtualHost>
```

But when I add these : 

		AddHandler php5-fastcgi .php
		Action php5-fastcgi /cgi-bin/php.cgi

and someone access the website, he is proposed to download the index.php file ...

I would appreciate a lot if anybody could give me a hint on this !

Thanks in advance, 
Fabianus

---

### Post by fabianus on 2009-03-14
ok, here is what I did : 

sudo apt-get install libapache2-mod-fcgid libapache2-mod-fastcgi
sudo a2enmod fcgid
sudo a2enmod fastcgi


I configured the  /etc/apache2/mods-enabled/fastcgi.conf
 file like this : 


```
<IfModule mod_fastcgi.c>
  AddHandler fastcgi-script .fcgi
  #FastCgiWrapper /usr/lib/apache2/suexec
  FastCgiIpcDir /var/lib/apache2/fastcgi

   FastCgiConfig -singleThreshold 1 -killInterval 300 -autoUpdate -idle-timeout 240 -pass-header HTTP_AUTHORIZATION

    # Define that every file named .php[345]? will be handled through the PHP FastCGI subsystem
    AddType application/x-httpd-fastphp .php .php3 .php4 .php5


</IfModule>
```


and now I do not have the previous problem anymore. 
BUT, is the fastcgi working ? Don't know and would love to be sure about. Do you guys know any solution on how to test this?

I did a phpinfo() file and it says that the fastcgi module is enabled, but I do not know if a perticular website really uses it. Thanks a lot for any feedback !

Regards, 
Fabianus

---

