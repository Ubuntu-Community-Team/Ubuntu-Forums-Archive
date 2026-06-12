---
title: "Can't install phpBMS from php script"
date: 2008-07-14
forum: Server Platforms
---

### Post by xeo_pt on 2008-07-14
I'm trying to install phpbms in one of my servers.
everything is installed (apache2, php and mysql)
the setup instructions say to run a script ../install/install.php
I point the browser (FF) to the location and FF ask me if I want to save the file, 
where the server should run the file and install the applications.

I check all the conf files a give permition to run the scrip.

Thanks in advance for your help.

---

### Post by windependence on 2008-07-14
In your browser's address bar you type:

[http://yourserverIP/phpbms_directory/install/install.php](http://yourserverIP/phpbms_directory/install/install.php)

And that should start the install in your browser. Your path may be a bit different depending on your root directory and how you have it set up.

-Tim

---

### Post by xeo_pt on 2008-07-14
Hi Tim, thanks for your replay.

> **windependence said:**
> In your browser's address bar you type:

[http://yourserverIP/phpbms_directory/install/install.php](http://yourserverIP/phpbms_directory/install/install.php)

And that should start the install in your browser. Your path may be a bit different depending on your root directory and how you have it set up.

-Tim


I type:
```
http://192.168.0.101/phpbms/install/install.php 
```

but the server downloads the file.
The httpd.conf files in the server is empty!
Cloud this be the problem?

---

### Post by mrmonday on 2008-07-14
If firefox offers to download the file for you then you haven't configured apache properly. It seems apache is not runing the file through php first. Are you using mod_php or mod_fcgi?

---

### Post by windependence on 2008-07-14
Can you post your apache configuration file here?

-Tim

---

### Post by xeo_pt on 2008-07-14
The apache.conf as an attachment.

I think the problem is with apache configuration.

How can I check if mod_php or/and mod_fcgi are enable ?

Thank you.


[ATTACH]77708[/ATTACH]

---

### Post by windependence on 2008-07-14
Can you post the contents of 

/etc/apache2/mods-enabled/*.load

and 

/etc/apache2/mods-enabled/*.conf

-Tim

---

### Post by xeo_pt on 2008-07-14
heare it goes.[ATTACH]77712[/ATTACH]

> **windependence said:**
> Can you post the contents of 

/etc/apache2/mods-enabled/*.load

and 

/etc/apache2/mods-enabled/*.conf

-Tim

---

### Post by windependence on 2008-07-15
Does this file exist on your machine?

/usr/lib/apache2/modules/libphp5.so

-Tim

---

### Post by xeo_pt on 2008-07-15
> **windependence said:**
> Does this file exist on your machine?

/usr/lib/apache2/modules/libphp5.so

-Tim
Yes it as.

---

### Post by windependence on 2008-07-15
Hate to make you do this but can I look at your 

/etc/apache2/sites-enabled/

and

/etc/apache2/conf.d/

and

/etc/apache2/httpd.conf

Also what is the content of your 

php5.conf

and

php5.load

I also noticed you are missing your servername directive.

Thanks,

-Tim

---

### Post by hyper_ch on 2008-07-15
try
```

sudo a2enmod php5 && sudo /etc/init.d/apache2 restart

```

---

### Post by xeo_pt on 2008-07-15
> **windependence said:**
> Hate to make you do this but can I look at your 

/etc/apache2/sites-enabled/

and

/etc/apache2/conf.d/

and

/etc/apache2/httpd.conf

Also what is the content of your 

php5.conf

and

php5.load

I also noticed you are missing your servername directive.

Thanks,

-Tim
my http.conf is empty

```
zorze@dx7:/etc/apache2/mods-available$ cat php5.load 
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

```
zorze@dx7:/etc/apache2/mods-available$ cat php5.conf 
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

```
zorze@dx7:/etc/apache2/sites-enabled$ ls
000-default
```

```
zorze@dx7:/etc/apache2/conf.d$ ls
charset
```

Hope it helps.

Thank you.

---

### Post by windependence on 2008-07-15
> **hyper_ch said:**
> try
```

sudo a2enmod php5 && sudo /etc/init.d/apache2 restart

```


I figured he did that already but thanks for reminding me.
:)

-Tim

---

### Post by windependence on 2008-07-15
> **xeo_pt said:**
> my http.conf is empty

```
zorze@dx7:/etc/apache2/mods-available$ cat php5.load 
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

```
zorze@dx7:/etc/apache2/mods-available$ cat php5.conf 
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

```
zorze@dx7:/etc/apache2/sites-enabled$ ls
000-default
```

```
zorze@dx7:/etc/apache2/conf.d$ ls
charset
```

Hope it helps.

Thank you.

Everything looks good, did you try the load command hyper_ch suggested?

-Tim

---

### Post by xeo_pt on 2008-07-15
> Everything looks good, did you try the load command hyper_ch suggested?

I can't my system doesn't know what is a2enmod

---

### Post by windependence on 2008-07-15
What is the error you get when you try to run the command? You are using sudo, correct?

-Tim

---

### Post by xeo_pt on 2008-07-15
That's it :guitar::guitar:
When I said that my system didn't know the problem was because I as typing in my desktop.

I execute the command and now it works.

thanks a lot people for your help, you are :KS:KS:KS:KS:KS

---

